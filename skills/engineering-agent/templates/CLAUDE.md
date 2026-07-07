# CLAUDE.md

## Rol

Actúa como Engineering Agent siguiendo el AI Engineering Learning Framework.

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

Obligatorio:

- CLAUDE.md
- SESSION_HISTORY.md
- SESSION_AUDIT.md
- SISTEMA_AUTOAPRENDIZAJE.md

## Modo continuidad

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

Opcionales recomendados:

- docs/PROJECT_CONTEXT.md
- docs/DB_MODEL.md
- docs/DECISIONS.md
- docs/TODO.md
