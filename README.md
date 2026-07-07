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
- project-templates/delrey-travels/SISTEMA_AUTOAPRENDIZAJE.md
- project-templates/delrey-travels/MEJORAS_FRAMEWORK.md
- project-templates/delrey-travels/PROMPTS.md

## Uso real en proyectos

1. Crea tu proyecto en un repositorio separado.
2. Copia `project-templates/delrey-travels/CLAUDE.md` al root del proyecto como `CLAUDE.md`.
3. Copia `project-templates/delrey-travels/SESSION_AUDIT.md` al root del proyecto como `SESSION_AUDIT.md`.
4. Copia `project-templates/delrey-travels/SISTEMA_AUTOAPRENDIZAJE.md` al root del proyecto como `SISTEMA_AUTOAPRENDIZAJE.md`.
5. Copia `project-templates/delrey-travels/MEJORAS_FRAMEWORK.md` al root del proyecto como `MEJORAS_FRAMEWORK.md`.
6. Trabaja con Claude usando ese archivo como contrato obligatorio.

## Inicio rapido

Usa `PROMPTS.md` como entrada operativa oficial. Los 3 prompts mas utiles son:

- activar proyecto nuevo,
- retomar sesion,
- cerrar sesion.

Si no quieres pensar el formato, abre `project-templates/delrey-travels/PROMPTS.md` y pega el bloque que corresponde al momento actual.

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

## Sistema de autoaprendizaje

Cada sesion debe capturar aprendizaje accionable en `SISTEMA_AUTOAPRENDIZAJE.md` con enfoque liviano:

- maximo 3 aprendizajes por sesion,
- cada aprendizaje en formato problema -> ajuste -> impacto -> validacion,
- eliminar aprendizajes que no aporten decisiones futuras.