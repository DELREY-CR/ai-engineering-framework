# Protocolo de Despliegue a Hosting Compartido (HostGator + SSH)

## Propósito

Procedimiento reutilizable para desplegar proyectos Laravel a un hosting compartido tipo HostGator con acceso SSH. Nace de la experiencia real de desplegar DelRey Travels (ver `docs/HOSTGATOR.md` del proyecto para el caso concreto aplicado). Su objetivo es que cada nuevo proyecto no repita desde cero los mismos errores ya resueltos.

## Cuándo usar

Cualquier proyecto del stack objetivo (Laravel + MySQL + Docker local) que se despliega a un hosting compartido Linux con cPanel.

## Fase 0: Acceso

- Confirmar si hay SSH disponible (cPanel → "Acceso a SSH") o solo FTP/File Manager. El método de despliegue cambia completamente según esto.
- Si hay SSH pero el agente no tiene credenciales: generar un par de llaves SSH temporal (el agente lo genera localmente, nunca pedir al desarrollador que comparta contraseñas por chat), pedir al desarrollador que importe la llave **pública** en cPanel → "Administrar claves SSH" → "Importar clave", y que la **autorice** (importar y autorizar son dos pasos separados; sin el segundo la conexión falla con `Permission denied (publickey)`). Revocar la llave al finalizar el despliegue.
- Si `ssh -i llave usuario@host comando` falla con `Too many authentication failures`, agregar `-o IdentitiesOnly=yes` (evita que el cliente ofrezca otras llaves antes que la indicada).
- **Si no se tiene a mano el host/puerto de conexión** (ni el desarrollador lo recuerda ni queda documentado): pedirle que abra **"Terminal"** en el buscador de cPanel (consola web, no necesita SSH externo) y corra `hostname -f`, `whoami`, `curl -s ifconfig.me`. Da host, usuario e IP suficientes para armar el comando SSH externo sin tener que navegar buscando la sección "SSH Access" del panel.
- **Si el repo del proyecto es público en GitHub** (verificar con `curl -s https://api.github.com/repos/<owner>/<repo> | grep '"private"'`), no guardar host/IP/usuario reales en ningún archivo versionado — dejarlos en un archivo local listado en `.gitignore` (ver patrón en `docs/HOSTGATOR-LOCAL.md` de DelRey Travels). El nombre de host o usuario por sí solo no compromete la cuenta (sigue haciendo falta la llave privada), pero no hay razón para publicarlo.
- Confirmar el entorno real del servidor conectándose y corriendo: `php -v`, `composer --version`, `git --version`, `which node npm`, `which uapi`.
- **Gotcha importante**: herramientas como Composer a veces solo están en el `PATH` de un shell de login completo, no en el shell no interactivo que usa `ssh host "comando"`. Si algo da "command not found" por SSH pero funciona en la Terminal interactiva de cPanel, probar envolviendo el comando en `bash -lc "..."`.

## Fase 1: Estructura del document root

- Consultar la estructura **real** con `uapi DomainInfo domains_data` (muestra el `documentroot` exacto de cada dominio de la cuenta) — no asumir por las carpetas que se ven a simple vista en el home del usuario.
- Dos patrones válidos:
  - **Opción A** (mejor si se puede elegir): el document root apunta directo a `public/`. Típico en dominios addon donde se puede fijar la ruta libremente.
  - **Opción B**: el document root apunta a la raíz del proyecto. Es obligatorio para el dominio *principal* de una cuenta cPanel, que normalmente no se puede mover de `public_html`. Requiere un `.htaccess` en la raíz que reenvíe todo a `public/`.
- **Si se usa Opción B, el `.htaccess` raíz debe bloquear, sin excepción**:
  - todos los dotfiles y dot-directorios (`.git`, `.env`, `.gitignore`, `.npmrc`, etc.) vía una regla tipo `RewriteRule (^|/)\.(?!well-known) - [F,L,NC]`
  - **todas** las carpetas de código fuente que no sean `public/`: `app`, `bootstrap`, `config`, `database`, `resources`, `routes`, `tests`, `vendor`, `storage`, y cualquier carpeta propia del proyecto (`docs`, `data`, `scripts`, etc.)
  - archivos sueltos: `composer.json`, `composer.lock`, `package(-lock).json`, `phpunit.xml`, `vite.config.js`, `artisan`, y cualquier `.md` de documentación interna (`README.md`, `SESSION_HISTORY.md`, etc.)
  - **Verificación obligatoria, no opcional**: probar en vivo con `curl` que `/.git/config`, `/composer.json`, `/docs/algo.md` devuelvan 403/404/406, nunca 200. Ya se encontró en producción real que una lista corta de bloqueo (solo `.env`, `artisan`, `composer.*`) deja el resto del repo completo — incluido `.git/` con todo el historial — descargable públicamente.

## Fase 2: Base de datos

- Crear vía `uapi Mysql create_database name=...`, `uapi Mysql create_user name=... password=...`, `uapi Mysql set_privileges_on_database user=... database=... privileges=ALL` — evita depender de la UI de cPanel y es reproducible.
- Respetar el prefijo `usuariocpanel_` obligatorio en nombre de base de datos y usuario.

## Fase 3: Dependencias

- Correr `composer install --no-dev --optimize-autoloader` **directo en el servidor**, no confiar en que el `composer.lock` generado en local/Docker sea instalable ahí.
  - **Gotcha real**: el entorno de desarrollo local (Docker/Sail) puede correr una versión de PHP más nueva que el hosting real. Si el lockfile fija una dependencia que exige esa versión más nueva, `composer install` falla en el servidor con un error de plataforma incompatible. Solución: ajustar esa dependencia a una versión compatible con el PHP real del hosting y correr `composer update <paquete> --with-all-dependencies` **en el propio servidor** (que tiene el PHP real de producción), y después sincronizar el `composer.json`/`composer.lock` resultante de vuelta al proyecto local.
- Si el servidor no tiene Node/npm (lo normal en shared hosting): compilar los assets localmente (`npm run build`, o dentro del contenedor Docker/Sail si el proyecto lo usa) y subir `public/build/` completo por `scp`. Nunca subir `node_modules/`.
- Verificar que los archivos compilados no queden en 0 bytes antes de darlos por buenos — un build interrumpido puede generar un archivo vacío sin que el comando de build falle visiblemente. Confirmar con `ls -la` el tamaño real, no solo que el comando terminó "bien".

## Fase 4: Variables de entorno

- Nunca reusar el `.env` de desarrollo tal cual en producción. Mantener en el repo un `.env.hosting.example` con los valores correctos para hosting compartido: `APP_ENV=production`, `APP_DEBUG=false`, `SESSION_DRIVER=file`, `CACHE_STORE=file`, `QUEUE_CONNECTION=sync` (si ningún `Mailable`/Job del proyecto implementa `ShouldQueue`, no hace falta worker de colas).
- Generar `APP_KEY` en el propio servidor (`php artisan key:generate --force`), nunca reusar la de local.
- Copiar ahí las credenciales reales de producción (API keys, pasarelas de pago, DB) — nunca inventarlas ni asumirlas.

## Fase 5: Migraciones y datos

- `php artisan migrate --force`, `php artisan storage:link`.
- Si el proyecto carga datos maestros por un comando propio (no por seeder estándar de Laravel), correrlo explícitamente (ej. importadores desde Excel).

## Fase 6: Optimización y scripts reutilizables

Definir en `composer.json` estos 3 scripts (copiar/adaptar entre proyectos):

```json
"preflight:hosting": ["sh ./scripts/hostgator-preflight.sh"],
"optimize:hosting": [
    "@php artisan optimize:clear",
    "@php artisan config:cache",
    "@php artisan route:cache",
    "@php artisan view:cache",
    "@php artisan event:cache"
],
"deploy:hosting": [
    "Composer\\Config::disableProcessTimeout",
    "sh -c 'php artisan down --retry=60 && php artisan migrate --force && php artisan storage:link --force && php artisan optimize:clear && php artisan config:cache && php artisan route:cache && php artisan view:cache && php artisan event:cache; exit_code=$?; php artisan up; exit $exit_code'"
]
```

Y un `scripts/hostgator-preflight.sh` que valide antes de abrir el sitio: existencia de `.env`, `.htaccess` (raíz y `public/`), `public/build/manifest.json`, symlink de `public/storage`, y que las variables críticas del `.env` no estén vacías (incluye las credenciales de cualquier pasarela de pago o servicio externo específico del proyecto).

## Fase 7: Verificación post-deploy (obligatoria)

- `curl` a las páginas clave del sitio confirmando 200 (home, rutas principales, sitemap si existe).
- `curl` a archivos que **nunca** deben responder 200: `.env`, `.git/config`, `composer.json`, cualquier doc interno — deben dar 403/404/406 (ver Fase 1).
- Ante cualquier 500, revisar `storage/logs/laravel.log` en el servidor antes de especular.
- **Gotcha conocido**: vistas Blade que emiten XML/texto con una declaración literal `<?xml version="1.0"...?>` como primera línea rompen con `syntax error, unexpected identifier "version"` en servidores con `short_open_tag` activado en PHP (PHP interpreta el `<?xml` como una etiqueta corta de PHP). Solución: partir la secuencia `<?` por concatenación dentro de un `{!! !!}`: `{!! '<' . '?xml version="1.0" encoding="UTF-8"?' . '>' !!}`.
- **Gotcha de inputs `type="date"` en mobile Safari/WebKit (iOS)**: si un `<input type="date">` lleva un ícono decorativo propio con padding izquierdo (`pl-11` o similar), WebKit puede desbordar el control fuera de su contenedor porque su renderizado nativo no respeta bien el espacio reducido, incluso con `min-w-0` y a ancho completo. La solución confiable no es ajustar paddings sino sacar el ícono decorativo y dejar que el navegador muestre su propio ícono nativo de calendario.

## Mantenimiento: actualizar un archivo puntual sin redeploy completo

Es común que el working tree del servidor tenga cambios locales sin comitear (fixes aplicados directo por SSH que después se sincronizaron al repo local pero nunca se comitearon en el propio servidor — ver gotcha de Fase 3). Un `git pull` completo en ese estado puede fallar o pisar esos cambios. Para traer un solo archivo nuevo o actualizado desde `origin/main` sin tocar el resto del árbol:

```bash
cd ~/public_html   # o el document root real
git fetch origin
git show origin/main:ruta/al/archivo > ruta/al/archivo
```

Útil para restaurar un archivo borrado por error o para subir un archivo de verificación de terceros (ver siguiente sección) sin arriesgar un despliegue completo.

## Verificaciones de terceros (Google Search Console, Bing Webmaster, etc.)

Estas plataformas suelen pedir subir un archivo estático a la raíz pública del sitio para confirmar propiedad del dominio.

- El contenido de estos archivos sigue un patrón fijo y no hace falta descargarlos: para Google, el archivo `google<token>.html` contiene una sola línea: `google-site-verification: google<token>.html`.
- En despliegues Opción B (dominio apuntando a la raíz del repo), el archivo debe quedar en la carpeta real que sirve Laravel (`public/`), igual que `robots.txt` y `favicon.ico` — no en la raíz del repo, salvo que el `.htaccess` esté confirmado para no reescribir archivos que ya existen físicamente ahí.
- Verificar siempre con `curl` que el archivo responde 200 con el contenido esperado antes de confirmar la verificación en la plataforma externa.
- No borrar el archivo después de verificar: varias plataformas re-chequean su existencia periódicamente para mantener la verificación activa.

## Fase 8: Cierre

- Revocar la llave SSH temporal (cPanel → "Administrar claves SSH") una vez confirmado que todo funciona.
- Documentar en `SESSION_HISTORY.md` del proyecto: qué se desplegó, qué bugs se encontraron y corrigieron, y pendientes — sin exponer credenciales reales en el documento.
- Si algo de este protocolo resultó incompleto o distinto en la práctica, actualizar este archivo en la misma sesión (no dejarlo para después).
