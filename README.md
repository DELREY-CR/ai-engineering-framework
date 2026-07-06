# AI Engineering Learning Framework

Version minima y operativa para trabajar con Claude de forma simple.

## Objetivo

### Descripcion breve

Crear un sistema de trabajo profesional para desarrollar software con IA, manteniendo orden tecnico y aprendizaje continuo del desarrollador.

### Resultado practico esperado

- trabajo por iteraciones con contexto claro,
- decisiones tecnicas explicadas antes de implementar,
- buenas practicas de arquitectura y validacion,
- aprendizaje activo mientras se construye el proyecto.

## Archivos que se usan

- principles/PRINCIPLES.md
- workflow/WORKFLOW.md
- skills/engineering-agent/SKILL.md
- skills/engineering-agent/templates/CLAUDE.md
- project-templates/delrey-travels/CLAUDE.md
- project-templates/delrey-travels/SESSION_AUDIT.md

## Uso real en proyectos

1. Crea tu proyecto en un repositorio separado.
2. Copia `project-templates/delrey-travels/CLAUDE.md` al root del proyecto como `CLAUDE.md`.
3. Copia `project-templates/delrey-travels/SESSION_AUDIT.md` al root del proyecto como `SESSION_AUDIT.md`.
4. Trabaja con Claude usando ese archivo como contrato obligatorio.

## Regla principal

El framework se mantiene simple: solo conserva lo que se usa en ejecucion diaria.

## Politica de cambio de stack

El framework es agnostico de tecnologia y puede adaptarse a otro stack sin cambiar su metodologia.

Cuando se cambie de stack, actualizar en la misma iteracion:

- contexto operativo y herramientas,
- reglas de validacion tecnica,
- comandos de build/test/deploy,
- plantillas de proyecto aplicables.

Ningun cambio de stack se considera cerrado sin evidencia minima de que el flujo base sigue funcionando en el nuevo stack.