# Instrucciones del repositorio LAB - G

Este repositorio contiene actividades escolares de estadística, regresión y aprendizaje automático realizadas en Jupyter Notebook. El objetivo de Copilot es ayudar a continuar las actividades con el mismo nivel, estructura y herramientas que ya se utilizaron en clase.

## Regla principal

- Completa los comentarios escritos en español con código del mismo estilo que aparece en los notebooks de `PRIMER PARCIAL`.
- Usa únicamente estructuras, librerías, clases, métodos y funciones que estén autorizados en `.github/instructions/python-clase.instructions.md`.
- El enunciado y el código inicial del archivo actual tienen prioridad. Después, utiliza como referencia los notebooks anteriores del tema correspondiente.
- Cuando existan un procedimiento manual y otro automatizado que ya se hayan visto, utiliza la versión automatizada más reciente. Conserva el procedimiento manual cuando la actividad lo pida o cuando todavía no se haya visto una función que lo automatice.
- Si no existe un antecedente de clase para resolver lo solicitado, no inventes una técnica distinta. Explica brevemente que no hay una estructura autorizada y pide que se agregue el nuevo ejemplo de clase.
- No agregues análisis, gráficas, transformaciones, validaciones ni explicaciones que no se hayan solicitado.

## Forma de escribir el código

- Mantén el trabajo a nivel estudiante y divide el proceso en celdas con un propósito claro.
- Usa nombres breves y naturales, como `df`, `X`, `y`, `modelo`, `y_pred`, `residuos`, `mse`, `num` y `cat`.
- Escribe comentarios cortos en español que expliquen lo que se hará, sin describir cada línea de forma innecesaria.
- Conserva los nombres reales de las columnas y adapta los ejemplos al dataset actual. No copies valores, resultados ni nombres de archivos de otro ejercicio.
- Presenta tablas con `display()` o `print()` y gráficas sencillas con Matplotlib, siguiendo la apariencia de los notebooks existentes.
- En las interpretaciones, explica primero el resultado, después lo que significa en el contexto del ejercicio y, cuando corresponda, su limitación. Usa lenguaje claro, natural y concreto.

## Fuentes de referencia por tema

- Regresión lineal simple y solución analítica: `Lab - R1.ipynb` y `A01-REGRESIÓNLINEAL.ipynb`.
- Regresión polinomial: `1. Regresión.ipynb` y `A01-REGRESIÓNLINEAL.ipynb`.
- Regresión múltiple e inferencia: `Lab - R2.ipynb` y `2.Regresiónmúltiple.ipynb`. Si difieren, prefiere la estructura más reciente de `Lab - R2.ipynb`.
- Escalamiento: `A02 - Escalamiento.ipynb`.
- Variables categóricas: `A03 - Codificacion de variables categoricas.ipynb`.
- Residuos y seis problemas de la regresión: `A04 - Análisis de residuos.ipynb` y `6 problemas de la regresion lineal.ipynb`.
- Limpieza y análisis exploratorio: `Lab - R3.ipynb`.
- Separación de datos, Ridge y Lasso: `Lab - R4.ipynb` y `Regresión sin penalización y Ridge.ipynb`.
- Preprocesamiento combinado y Pipeline: `Pipeline.ipynb`.
- LOOCV y K-Fold: `Lab - R5.ipynb`.

## Restricciones importantes

- No uses `PolynomialFeatures`, `cross_val_score`, `GridSearchCV`, `RandomizedSearchCV`, Seaborn, `make_pipeline`, clases personalizadas ni otras herramientas que no aparecen en las referencias autorizadas.
- No uses Statsmodels salvo que la actividad pida inferencia, significancia, intervalos, influencia, leverage, VIF o un resumen estadístico, y exista un ejemplo equivalente en los notebooks.
- No reemplaces los ciclos de validación cruzada vistos en clase por funciones nuevas que oculten el procedimiento.
- No cambies una estructura que ya funciona únicamente para hacerla más avanzada, corta o elegante.
- Antes de terminar una respuesta de chat o una edición, comprueba que cada función propuesta aparezca en la lista autorizada y que la solución responda solamente a lo solicitado.
