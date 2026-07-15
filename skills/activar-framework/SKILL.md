# Activar Framework

## Propósito

Esta Skill determina el modo de trabajo de un proyecto nuevo bajo el AI Engineering Learning Framework — `sesion-unica` (tarea puntual, sin continuidad) o `sesion-sostenida` (proyecto que se retoma sesión tras sesión) — e instala el set de archivos correcto en el root del proyecto.

No define principios ni workflow propios. Es solo el punto de entrada que decide qué instalar y deja el modo registrado en `CLAUDE.md`. El comportamiento operativo del día a día sigue siendo el de `skills/engineering-agent/SKILL.md`.

## Cuándo usar esta Skill

- Al empezar a trabajar en un proyecto que todavía no tiene `CLAUDE.md` de este framework instalado.
- Cuando el desarrollador pide explícitamente "activar el framework" para un proyecto.
- No usar en un proyecto que ya tiene `CLAUDE.md` con el campo `Modo` definido — en ese caso, leer el modo existente y continuar directo con `skills/engineering-agent/SKILL.md`, sin volver a preguntar.

## Paso 1 — Verificar si ya está activado

Buscar `CLAUDE.md` en el root del proyecto y el campo `Modo:` dentro de él.

- Si existe: informar el modo actual encontrado y detener esta Skill.
- Si no existe: continuar al Paso 2.

## Paso 2 — Determinar el modo (única pregunta bloqueante)

Preguntar directo:

> ¿Esta va a ser una intervención puntual, sin continuidad hacia adelante, o vas a seguir trabajando este proyecto en próximas sesiones?

No inferir la respuesta del tamaño o tipo de tarea — una tarea que suena pequeña puede ser el inicio de un proyecto sostenido, y viceversa. Es una decisión del desarrollador, no una deducción del agente.

## Paso 3 — Instalar el set de archivos según el modo

### Modo `sesion-unica`

Copiar solo `skills/engineering-agent/templates/CLAUDE.md` al root del proyecto como `CLAUDE.md`, dejando:

- `Modo: sesion-unica` en la sección `## Modo`.
- La sección "Modo sesion-unica" activa (la sección "Modo continuidad" queda documentada pero marcada como no aplicable a este proyecto).

No copiar `SESSION_HISTORY.md`, `SESSION_AUDIT.md`, `SISTEMA_AUTOAPRENDIZAJE.md` ni `MEJORAS_FRAMEWORK.md` — sin continuidad no aportan valor, son fricción pura.

### Modo `sesion-sostenida`

Copiar el set completo, tal como documenta `README.md` en "Uso real en proyectos":

- `skills/engineering-agent/templates/CLAUDE.md` (copiar como `CLAUDE.md` al root del proyecto, dejar `Modo: sesion-sostenida`) — nunca copiar un `CLAUDE.md` de `project-templates/`, esos son ejemplos ya instanciados de un proyecto real, no plantillas en blanco.
- `SESSION_HISTORY.md`
- `SESSION_AUDIT.md`
- `SISTEMA_AUTOAPRENDIZAJE.md`
- `MEJORAS_FRAMEWORK.md`

## Regla de promoción (`sesion-unica` → `sesion-sostenida`)

Si se abre una segunda sesión real de trabajo sobre el mismo proyecto mientras sigue en modo `sesion-unica`:

1. Informar que el proyecto dejó de ser puntual.
2. Proponer el cambio a `sesion-sostenida` antes de continuar con la tarea.
3. Si el desarrollador confirma: instalar los archivos faltantes del Paso 3 (modo sostenido) sin perder lo ya trabajado, y actualizar el campo `Modo` en `CLAUDE.md`.
4. Si el desarrollador prefiere seguir puntual: continuar sin instalar nada y repetir esta misma pregunta si vuelve a pasar.

## Regla de aprendizaje en modo `sesion-unica`

En modo `sesion-unica` no existe `SISTEMA_AUTOAPRENDIZAJE.md` local — no hay sesiones futuras de este proyecto que puedan validar un aprendizaje por recurrencia dentro de él.

Si durante la tarea surge un aprendizaje real y accionable (no una observación rutinaria):

1. No crear ningún archivo de autoaprendizaje en el proyecto.
2. Proponer directamente una entrada en el `MEJORAS_FRAMEWORK.md` del framework base (Nivel 2), marcada `Origen: tarea puntual`.
3. Estado inicial siempre `en observacion (no recurrente)`, nunca `estable` ni `pendiente` directo — una sola ocurrencia aislada no se autovalida. Pasa a `pendiente` solo si el mismo patrón vuelve a aparecer en otra tarea puntual o proyecto distinto (ver `MEJORAS_FRAMEWORK.md`, sección "Regla de activación — origen tarea puntual").

## Fuente de conocimiento

El conocimiento operativo reside en `principles/PRINCIPLES.md` y `workflow/WORKFLOW.md`. Esta Skill no lo duplica — solo decide qué instalar.
