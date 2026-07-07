# SISTEMA_AUTOAPRENDIZAJE

Sistema de dos niveles para aprendizaje operativo efectivo y escalable.

## Arquitectura

- Nivel 1 (este archivo): captura, prioriza y valida aprendizajes dentro del proyecto.
- Nivel 2 (MEJORAS_FRAMEWORK.md): propaga aprendizajes validados al framework base para beneficiar proyectos futuros.

## Protocolo de apertura de sesion

Al iniciar cada sesion, antes de ejecutar cualquier tarea:

1. Leer las entradas anteriores de este archivo.
2. Identificar si el problema o patron actual ya aparecio en sesiones previas.
3. Si coincide en 2 o mas sesiones anteriores: marcarlo como RECURRENTE y darle prioridad maxima automaticamente.

## Priorizacion TOP 3

Calificar cada candidato de 1 a 5:

- IP (impacto en productividad): tiempo o errores que evita.
- FR (frecuencia): veces que aparece en sesiones registradas.
- CR (costo de no resolver): riesgo de retrabajo o bloqueo.
- TR (transferibilidad): utilidad en otras tareas o proyectos.
- EF (esfuerzo de implementacion): 1 facil, 5 dificil (resta).

`PRIORIDAD = (IP x 3) + (FR x 3) + (CR x 2) + (TR x 1) - (EF x 1)`

Reglas de seleccion del TOP 3:

- Ordenar por PRIORIDAD de mayor a menor.
- RECURRENTE siempre tiene prioridad sobre critico puntual.
- Maximo 1 critico puntual no recurrente.
- Empate: gana el de menor EF.

## Formato por entrada

### LEARN_XXX — Titulo

- Fecha:
- Categoria (bloqueo / velocidad / calidad):
- RECURRENTE (si/no + sesiones donde aparecio):
- Problema observado:
- Causa raiz:
- Ajuste aplicado:
- Impacto esperado:
- Criterio de validacion:
- Puntaje PRIORIDAD:
- Estado (en prueba / estable / descartado):
- Propagado a MEJORAS_FRAMEWORK (si/no):

## Regla de propagacion

Cuando un aprendizaje alcanza estado "estable": crear entrada correspondiente en MEJORAS_FRAMEWORK.md indicando el documento del framework a actualizar.

## Regla de poda

Eliminar entradas con estado "descartado" o sin actividad en 10 sesiones.
