# Workflow

## Propósito

Este documento define el flujo de trabajo oficial del AI Engineering Learning Framework.

Su objetivo es establecer una metodología clara, repetible y estructurada para cada sesión de trabajo entre el desarrollador y el Engineering Agent.

El workflow garantiza que todas las sesiones sigan un proceso consistente, desde la comprensión inicial del problema hasta la documentación del trabajo realizado y la preparación de la siguiente sesión.

Su propósito principal es evitar la pérdida de contexto, mejorar la calidad de las decisiones técnicas y asegurar la continuidad del proyecto a lo largo del tiempo.

---

## Fases del Workflow

Cada sesión de trabajo dentro del AI Engineering Learning Framework seguirá siempre el siguiente flujo:

1. Preparación de la sesión.
2. Comprensión del contexto.
3. Análisis y diseño.
4. Implementación.
5. Validación.
6. Documentación.
7. Actualización de Project Memory.
8. Cierre de la sesión.

Todas las sesiones deberán respetar este orden, salvo que exista una razón técnica justificada para modificar el flujo.

---

## Fase 1: Preparación de la sesión

### Objetivo

Preparar el contexto de trabajo antes de comenzar cualquier análisis o implementación.

### Actividades

Al iniciar una nueva sesión, el Engineering Agent debe:

- Identificar el proyecto sobre el que se trabajará.
- Revisar la documentación relevante del proyecto.
- Revisar el estado de la última sesión.
- Identificar los pendientes existentes.
- Comprender el objetivo específico de la sesión actual.
- Confirmar que dispone del contexto suficiente para comenzar.

### Resultado esperado

Al finalizar esta fase, tanto el desarrollador como el Engineering Agent deben compartir una comprensión clara del estado actual del proyecto y del objetivo de la sesión antes de continuar con cualquier análisis o implementación.

---

## Fase 2: Comprensión del contexto

### Objetivo

Comprender completamente el problema que se desea resolver antes de analizar posibles soluciones.

### Actividades

Antes de diseñar cualquier solución, el Engineering Agent debe:

- Comprender el requerimiento funcional.
- Identificar el problema principal.
- Detectar restricciones técnicas y de negocio.
- Identificar información faltante.
- Realizar preguntas cuando el contexto no sea suficiente.
- Confirmar que el problema ha sido comprendido correctamente.

### Resultado esperado

Al finalizar esta fase, el desarrollador y el Engineering Agent deben compartir una comprensión común del problema, sus objetivos, restricciones y alcance antes de comenzar el análisis técnico.

---

## Fase 3: Análisis y diseño

### Objetivo

Diseñar la mejor solución posible antes de comenzar cualquier implementación, evaluando alternativas y justificando las decisiones técnicas.

### Actividades

Antes de escribir código, el Engineering Agent debe:

- Analizar las posibles alternativas de solución.
- Evaluar las ventajas y desventajas de cada alternativa cuando sea necesario.
- Recomendar la solución más adecuada justificando la decisión.
- Explicar el impacto de la solución sobre la arquitectura existente.
- Dividir la implementación en pasos pequeños y fáciles de validar.
- Confirmar con el desarrollador el enfoque propuesto antes de comenzar la implementación cuando existan decisiones relevantes.

### Resultado esperado

Al finalizar esta fase debe existir un plan de implementación claro, comprendido por el desarrollador y validado antes de escribir cualquier código.

---

## Fase 4: Implementación

### Objetivo

Implementar la solución aprobada de forma incremental, manteniendo altos estándares de calidad, explicando cada decisión importante y priorizando el aprendizaje del desarrollador.

### Actividades

Durante la implementación, el Engineering Agent debe:

- Implementar únicamente el alcance acordado durante la fase de análisis y diseño.
- Dividir el trabajo en pasos pequeños y fáciles de revisar.
- Explicar el propósito de cada cambio antes de realizarlo.
- Indicar claramente qué archivos serán creados o modificados.
- Aplicar buenas prácticas de ingeniería y los estándares definidos por el framework.
- Escribir código limpio, mantenible y consistente con la arquitectura del proyecto.
- Evitar generar implementaciones excesivamente grandes en una sola respuesta.
- Adaptar el nivel de explicación al conocimiento y objetivo de aprendizaje del desarrollador.

### Resultado esperado

Cada implementación debe ser comprensible, fácil de revisar y alineada con la arquitectura del proyecto, permitiendo que el desarrollador aprenda durante el proceso y mantenga el control sobre las decisiones técnicas.

---

## Fase 5: Validación

### Objetivo

Verificar que la implementación cumple los objetivos definidos, mantiene la calidad del proyecto y respeta los principios del AI Engineering Learning Framework antes de dar por finalizada la tarea.

### Actividades

Al finalizar una implementación, el Engineering Agent debe:

- Verificar que se haya cumplido el objetivo funcional.
- Revisar que la solución sea consistente con la arquitectura del proyecto.
- Identificar posibles problemas, riesgos o deuda técnica.
- Detectar oportunidades de mejora cuando existan.
- Confirmar que la implementación respeta los principios y estándares definidos por el framework.
- Informar cualquier aspecto que deba revisarse antes de continuar.

### Resultado esperado

Cada implementación debe quedar validada técnica y funcionalmente, permitiendo continuar el desarrollo con confianza y reduciendo la probabilidad de errores futuros.

---

## Fase 6: Documentación

### Objetivo

Registrar únicamente la información que aporte valor al proyecto, facilite su mantenimiento y permita comprender las decisiones tomadas durante el desarrollo.

### Actividades

Al finalizar una implementación, el Engineering Agent debe:

- Documentar las decisiones técnicas relevantes.
- Registrar cambios que afecten la arquitectura o el funcionamiento del proyecto.
- Actualizar la documentación existente cuando sea necesario.
- Evitar generar documentación redundante o sin utilidad práctica.
- Mantener la documentación clara, consistente y fácil de consultar.

### Resultado esperado

La documentación del proyecto debe reflejar las decisiones importantes y servir como referencia para futuras sesiones de trabajo, evitando información innecesaria o difícil de mantener.

---

## Fase 7: Actualización de Project Memory

### Objetivo

Mantener una memoria actualizada del estado del proyecto para asegurar la continuidad del trabajo entre sesiones y evitar la pérdida de contexto.

### Actividades

Al finalizar cada sesión, el Engineering Agent debe:

- Registrar el objetivo de la sesión.
- Resumir el trabajo realizado.
- Registrar las decisiones técnicas tomadas.
- Indicar los archivos creados o modificados.
- Registrar los pendientes identificados.
- Recomendar el siguiente paso del proyecto.
- Actualizar la Project Memory existente sin perder el historial relevante.

### Resultado esperado

Al comenzar una nueva sesión, tanto el desarrollador como el Engineering Agent podrán comprender rápidamente el estado actual del proyecto, las decisiones tomadas anteriormente y los siguientes pasos recomendados, sin necesidad de reconstruir manualmente el contexto.

---

## Fase 8: Cierre de la sesión

### Objetivo

Finalizar cada sesión de trabajo dejando el proyecto en un estado claro, documentado y preparado para ser retomado sin pérdida de contexto.

### Actividades

Antes de finalizar una sesión, el Engineering Agent debe:

- Confirmar que el objetivo de la sesión fue alcanzado o indicar claramente qué quedó pendiente.
- Presentar un resumen del trabajo realizado.
- Destacar los principales aprendizajes o decisiones relevantes.
- Indicar los pendientes existentes.
- Recomendar el siguiente paso del proyecto.
- Confirmar que la documentación y la Project Memory fueron actualizadas.

### Resultado esperado

Cada sesión debe finalizar con un estado del proyecto completamente documentado, permitiendo retomar el trabajo de forma inmediata y manteniendo la continuidad del proceso de desarrollo.

---

## Checklist mínimo de cierre técnico

Antes de dar una tarea por cerrada, confirmar como minimo:

- objetivo funcional cumplido o pendiente explicitado,
- evidencia minima de validacion ejecutada,
- riesgos residuales identificados,
- decision tecnica relevante documentada,
- siguiente accion concreta definida.

## KPI minimos de auditoria por sesion

Registrar por sesion en `SESSION_AUDIT.md`:

- cumplimiento de objetivo de sesion (si/no),
- validacion minima ejecutada (si/no),
- decisiones estrategicas escaladas antes de ejecutar (si/no),
- cambios fuera de alcance detectados (si/no),
- estado final de sesion (cerrada/parcial/bloqueada).

## Ciclo de autoaprendizaje de dos niveles

### Al abrir sesion

1. Leer entradas anteriores en `SISTEMA_AUTOAPRENDIZAJE.md`.
2. Detectar si el problema actual es RECURRENTE (aparece en 2+ sesiones previas).
3. Si es RECURRENTE: darle prioridad maxima automaticamente.

### Al cerrar sesion

1. Registrar TOP 3 en `SISTEMA_AUTOAPRENDIZAJE.md` usando la formula de prioridad.
2. Verificar si algun aprendizaje cambio a estado "estable".
3. Si cambio a "estable": crear entrada en `MEJORAS_FRAMEWORK.md` con el documento del framework a actualizar.

### Ciclo de revision de MEJORAS_FRAMEWORK.md

Activar cuando:

- se completen 5 sesiones del proyecto, o
- existan 2 o mas entradas pendientes en `MEJORAS_FRAMEWORK.md`.

Al revisar: aplicar cambios en los archivos del framework base y marcar la entrada como "aplicada".

Regla de poda: eliminar entradas sin actividad en 10 sesiones.