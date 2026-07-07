# PROMPTS — AI Engineering Learning Framework

Prompts listos para copiar y pegar segun el momento de trabajo.
Reemplaza los valores entre [ ] con el contexto real antes de enviar.

---

## 1. Activacion inicial — proyecto nuevo

```
Actua como Engineering Agent siguiendo el AI Engineering Learning Framework.

Lee en este orden:
1. CLAUDE.md
2. SESSION_HISTORY.md
3. SESSION_AUDIT.md
4. SISTEMA_AUTOAPRENDIZAJE.md
5. MEJORAS_FRAMEWORK.md

Confirma que tienes todos los archivos disponibles.
El objetivo del proyecto es: [descripcion breve del proyecto].
Stack: PHP, Laravel, MySQL, Docker, Blade, Tailwind, Vite.
Entorno: macOS, VS Code, terminal zsh.

Una vez confirmado el contexto, dime que necesitas de mi para arrancar.
```

---

## 2. Retomar sesion

```
Retoma el proyecto. Lee la ultima entrada de SESSION_HISTORY.md
y revisa SISTEMA_AUTOAPRENDIZAJE.md.

Respondeme:
1. ¿Que estaba pendiente al cierre de la sesion anterior?
2. ¿Cual es la siguiente accion concreta segun el estado actual?
3. ¿Hay algun aprendizaje RECURRENTE hoy que deba tener presente?

No implementes nada todavia. Solo dame el estado y esperamos confirmar.
```

---

## 3. Nueva tarea de desarrollo

```
Tarea nueva: [descripcion exacta de lo que quiero construir o modificar].

Antes de implementar:
- confirma que entiendes el objetivo,
- identifica el impacto en el sistema existente,
- propone un enfoque con justificacion breve,
- espera mi aprobacion antes de escribir codigo.

Una accion por iteracion. Explicacion orientada al aprendizaje.
```

---

## 4. Debugging o fix

```
Tengo un problema: [descripcion del error o comportamiento inesperado].

Contexto:
- archivo o componente afectado: [nombre]
- lo que deberia pasar: [comportamiento esperado]
- lo que esta pasando: [comportamiento actual]
- lo que ya probe: [si aplica]

Analiza la causa raiz antes de proponer solucion.
Una hipotesis por vez. No cambies mas de lo necesario para resolver.
```

---

## 5. Revision de arquitectura o decision tecnica

```
Necesito tomar una decision tecnica: [descripcion del problema o eleccion].

Opciones que estoy considerando: [si ya tienes alguna].

Quiero que:
1. Evalues las opciones con pros y contras reales para mi contexto.
2. Recomiendes una con justificacion concreta.
3. Esperes mi decision antes de implementar.

No implementes todavia. Solo analisis y recomendacion.
```

---

## 6. Cierre de sesion

```
Cerramos la sesion de hoy.

Genera:
1. Entrada para SESSION_HISTORY.md con: fecha, objetivo, trabajo realizado,
   decisiones clave, pendientes y siguiente accion.
2. KPI para SESSION_AUDIT.md.
3. TOP 3 para SISTEMA_AUTOAPRENDIZAJE.md usando la formula de prioridad.
   Indica si algun aprendizaje es RECURRENTE y su puntaje.
4. Si algun aprendizaje llego a estado "estable":
   crea la entrada correspondiente en MEJORAS_FRAMEWORK.md.
```

---

## 7. Revision del framework (cada 5 sesiones)

```
Revision de MEJORAS_FRAMEWORK.md.

Muestra todas las entradas con estado "pendiente".
Para cada una, propone el cambio exacto en el documento del framework
que corresponde segun el mapa de categoria.

No apliques nada todavia. Esperamos mi aprobacion entrada por entrada.
```

---

## 8. Consulta rapida sin contexto completo

```
Consulta puntual, sin necesidad de retomar contexto de sesion:
[pregunta o tarea especifica].

Responde directo. No necesito resumen de sesion al final.
```
