# MEJORAS_FRAMEWORK

Canal de propagacion de aprendizaje: proyecto → framework base.

## Proposito

Registrar aprendizajes validados (estado "estable" en SISTEMA_AUTOAPRENDIZAJE.md)
que deben actualizar las plantillas base del framework para beneficiar proyectos futuros.

## Regla de activacion

Cuando un aprendizaje en SISTEMA_AUTOAPRENDIZAJE.md alcanza estado "estable":
crear una entrada aqui indicando el documento del framework a modificar.

## Regla de activacion — origen tarea puntual

Un proyecto en `Modo: sesion-unica` (ver `skills/activar-framework/SKILL.md`) no tiene `SISTEMA_AUTOAPRENDIZAJE.md` local — no hay sesiones futuras de ese proyecto que validen un aprendizaje por recurrencia dentro de el.

Cuando surge un aprendizaje real y accionable durante una tarea puntual, se crea la entrada directo aqui (salta el Nivel 1), con:

- `Origen del aprendizaje: tarea puntual`.
- Estado inicial siempre `en observacion (no recurrente)` — nunca `estable` ni `pendiente` directo.

Esta entrada pasa a `pendiente` solo cuando el mismo patron vuelve a aparecer en una segunda tarea puntual o proyecto distinto (el "aparece 2+ veces" de siempre, pero contando entre tareas puntuales en vez de entre sesiones de un mismo proyecto). Si nunca reaparece, se poda igual que cualquier entrada sin actividad en 10 sesiones/tareas.

## Ciclo de revision

Revisar este archivo:

- cada 5 sesiones del proyecto, o
- cuando existan 2 o mas entradas con estado "pendiente".

Al revisar: aplicar los cambios en los archivos del framework base y marcar la entrada como "aplicada".

## Mapa categoria → documento objetivo

- bloqueo       → workflow/WORKFLOW.md
- velocidad     → skills/engineering-agent/SKILL.md
- calidad       → project-templates/delrey-travels/CLAUDE.md
- contrato      → project-templates/delrey-travels/CLAUDE.md

## Formato por entrada

### MEJORA_XXX — Titulo

- Fecha:
- Origen (LEARN_XXX, o "tarea puntual" si no paso por Nivel 1):
- Categoria del aprendizaje:
- Documento objetivo en el framework:
- Cambio propuesto (exacto y accionable):
- Justificacion (patron observado):
- Estado (en observacion (no recurrente) / pendiente / aplicada / descartada):
