# github-actions-stockguard

Práctica de GitHub Actions con Python y `pytest` para comprender el funcionamiento de Integración Continua antes de aplicarlo al proyecto final RapidGo.

## Objetivo

El ejercicio permite comprobar cómo GitHub Actions ejecuta validaciones automáticas ante cambios realizados mediante `push`, `pull_request` y ejecución manual con `workflow_dispatch`.

## Validaciones implementadas

El workflow realiza las siguientes verificaciones:

- Configuración del entorno de Python.
- Instalación de dependencias.
- Validación de sintaxis.
- Ejecución automática de pruebas con `pytest`.

## Evidencias realizadas

Durante la práctica se comprobó el ciclo completo de CI:

1. Ejecución correcta del workflow.
2. Falla controlada modificando intencionalmente una prueba.
3. Identificación del error en los logs de GitHub Actions.
4. Corrección de la prueba y nueva ejecución exitosa.
5. Creación de una rama `feature/alerta-sobrestock`.
6. Pull Request con checks automáticos.
7. Merge después de validar el workflow.
8. Ejecución manual mediante `workflow_dispatch`.

## Falla controlada

La prueba de stock crítico se modificó temporalmente para esperar un resultado incorrecto:

```python
assert clasificar_stock(7, 20) == "NORMAL"
```

La función devolvía correctamente `CRITICO`, por lo que `pytest` generó un `AssertionError`. Después se restauró el resultado esperado y el workflow volvió a pasar correctamente.

## Análisis

Las respuestas a las preguntas de análisis de la práctica se encuentran en:

`docs/respuestas_analisis_github_actions.txt`

## Aprendizaje obtenido

La práctica permitió entender que GitHub Actions no reemplaza las pruebas locales, sino que agrega una validación automática en un entorno limpio antes de integrar cambios a la rama principal. Este mismo enfoque se trasladará al proyecto RapidGo para validar reglas de negocio, eventos JSON y configuración del proyecto.
