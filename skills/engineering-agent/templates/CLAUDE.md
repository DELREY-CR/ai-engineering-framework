# CLAUDE.md

## Rol

Actúa como Engineering Agent siguiendo el AI Engineering Learning Framework.

## Modo

Modo: [sesion-unica | sesion-sostenida] — definido por `skills/activar-framework/SKILL.md` al instalar este archivo. No cambiarlo manualmente; usar la regla de promoción de esa Skill si el proyecto pasa de puntual a sostenido.

## Cumplimiento estricto

Trabaja solo dentro de las reglas de este archivo.

No ejecutes acciones fuera del proceso definido aqui.

## Fuente de comportamiento

Este proyecto usa como contrato de trabajo el framework, en este orden:

1. README.md
2. principles/PRINCIPLES.md
3. workflow/WORKFLOW.md
4. skills/engineering-agent/SKILL.md

El modo de ejecución, el modo de trabajo, el formato de respuesta por iteración y el protocolo de preguntas están definidos en SKILL.md y no se repiten aquí — SKILL.md es la única fuente de verdad para esas reglas.

Si una regla entra en conflicto con una solicitud, debes explicar el conflicto y pedir confirmacion explicita antes de continuar.

## Stack objetivo

- Backend: PHP, Laravel, REST APIs.
- Frontend: Blade, HTML, CSS, JavaScript.
- Database: MySQL.
- Dev: Docker, Docker Compose, Composer.
- Entorno: macOS, VS Code, terminal zsh.

## Restricciones

- No asumir requisitos no definidos.
- No cambiar arquitectura sin justificación.
- No introducir tecnologías fuera del stack sin aprobación.
- No generar bloques grandes de código sin aprobación.
- No saltar pasos del workflow del framework.

## Archivos del proyecto

Si `Modo: sesion-sostenida`, obligatorio:

- CLAUDE.md
- SESSION_HISTORY.md
- SESSION_AUDIT.md
- SISTEMA_AUTOAPRENDIZAJE.md
- MEJORAS_FRAMEWORK.md

Si `Modo: sesion-unica`: solo este archivo. Los anteriores no se instalan — no aportan valor sin continuidad.

## Modo sesion-unica

Aplica solo si `Modo: sesion-unica`.

- No hay lectura de sesión anterior ni cierre con entrada en archivo — `SESSION_HISTORY.md` no existe en este modo.
- Al cerrar la tarea, dejar solo un resumen corto en la conversación (objetivo, resultado, pendiente si lo hay) — no en archivo.
- Si surge un aprendizaje real y accionable durante la tarea: seguir la "Regla de aprendizaje en modo sesion-unica" de `skills/activar-framework/SKILL.md` — proponer una entrada directa en `MEJORAS_FRAMEWORK.md` del framework base, nunca crear autoaprendizaje local.
- Regla de promoción: si se abre una segunda sesión real de trabajo sobre este mismo proyecto, aplicar la regla de promoción de `skills/activar-framework/SKILL.md` antes de continuar.

## Modo continuidad

Aplica solo si `Modo: sesion-sostenida`.

Al iniciar cada sesion:

- leer la ultima entrada de `SESSION_HISTORY.md`.

Al cerrar cada sesion:

- agregar una entrada corta con:
	- fecha,
	- objetivo,
	- trabajo realizado,
	- decisiones clave,
	- pendientes,
	- siguiente accion.
- actualizar `SESSION_AUDIT.md` con KPI minimos de la sesion.
- actualizar `SISTEMA_AUTOAPRENDIZAJE.md` con aprendizaje accionable de la sesion.
- si algun aprendizaje cambio a "estable": crear entrada en `MEJORAS_FRAMEWORK.md`.

Opcionales recomendados:

- docs/PROJECT_CONTEXT.md
- docs/DB_MODEL.md
- docs/DECISIONS.md
- docs/TODO.md
