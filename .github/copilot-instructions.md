# Instrucciones del repositorio LAB - G

Este repositorio contiene actividades escolares de estadística, regresión, clasificación y aprendizaje automático realizadas en Jupyter Notebook. El objetivo es ayudar a continuar las actividades y los exámenes con el mismo nivel, estructura y herramientas que ya se utilizaron en clase.

## Regla principal

- Usa únicamente estructuras, librerías, clases, métodos, parámetros y funciones que aparezcan en `.github/instructions/python-clase.instructions.md`, que reúne todo lo visto en los notebooks de `PRIMER PARCIAL` y `SEGUNDO PARCIAL`, o que aparezcan en el enunciado o en el código inicial del archivo actual.
- No propongas atajos ni versiones más sofisticadas de lo visto aunque den el mismo resultado: sin funciones que oculten un ciclo visto en clase, sin librerías nuevas, sin clases ni funciones propias donde en clase se escribió el paso a paso.
- El enunciado y el código inicial del archivo actual tienen prioridad. Después, utiliza como referencia los notebooks anteriores del tema correspondiente.
- Cuando existan un procedimiento manual y otro automatizado que ya se hayan visto, utiliza la versión automatizada más reciente. Conserva el procedimiento manual cuando la actividad lo pida o cuando todavía no se haya visto una función que lo automatice.
- Si no existe un antecedente de clase para resolver lo solicitado, no inventes una técnica distinta. Explica brevemente que no hay una estructura vista en clase.
- No agregues análisis, gráficas, transformaciones, validaciones ni explicaciones que no se hayan solicitado.

## Completar a partir de un comentario

Este es el uso principal durante los exámenes. Cuando una celda tenga un comentario que describe un paso, como `# cargar los datos`, `# ajustar la regresión logística`, `# calcular el AUC con K-Fold` o `# matriz de confusión`:

- Completa únicamente ese paso, con la estructura del notebook de referencia del tema.
- Adapta nombres de variables y columnas al dataset actual, sin copiar valores ni resultados de otro ejercicio.
- No adelantes pasos posteriores ni generes la solución completa si el comentario pide una sola parte.

## Forma de escribir el código

- Mantén el trabajo a nivel estudiante y divide el proceso en celdas con un propósito claro.
- Usa nombres breves y naturales, como `df`, `X`, `y`, `modelo`, `y_pred`, `prob`, `residuos`, `mse`, `auc`, `num` y `cat`.
- Escribe comentarios cortos en español que expliquen lo que se hará, sin describir cada línea de forma innecesaria.
- Conserva los nombres reales de las columnas y adapta los ejemplos al dataset actual. No copies valores, resultados ni nombres de archivos de otro ejercicio.
- Presenta tablas con `display()`, `print()` o un `pd.DataFrame` al final de la celda, y gráficas sencillas con Matplotlib, siguiendo la apariencia de los notebooks existentes.
- En las interpretaciones, explica primero el resultado, después lo que significa en el contexto del ejercicio y, cuando corresponda, su limitación. Usa lenguaje claro, natural y concreto.

## Fuentes de referencia por tema

### Primer parcial: regresión

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

### Segundo parcial: clasificación

- Regresión logística, parámetro `C`, probabilidades y métricas por umbral: `Regresión_logística.ipynb`.
- Regresión logística simple y múltiple, errores estándar, estadístico z y p-value: `Lab - C1.ipynb`.
- SVM con kernels, AUC y K-Fold con `Pipeline`: `Lab - C2.ipynb`.
- SVM con PCA, búsqueda de parámetros, reporte de clasificación y matriz de confusión: `04_Ingenieria_inversa.ipynb`.
- Perceptrón multicapa (`MLPClassifier`) con train-test 70/30, métricas y comparación de hiperparámetros: `Lab - C3.ipynb`.
- Búsqueda de neuronas con `GridSearchCV`, `make_pipeline` y AUC de test: `MLP con hiperparámetros(neuronas).ipynb`.
- Comparación de `GridSearchCV`, `RandomizedSearchCV` y Optuna con K-Fold de 10: `Laboratorio de métodos de búsqueda.ipynb`.
- Optimización bayesiana con `GaussianProcessRegressor` y selección del siguiente punto: `Optimización Bayesiana.ipynb`.

## Herramientas que todavía no se han visto

No uses `PolynomialFeatures`, `cross_val_score`, `cross_validate`, clases personalizadas ni otras herramientas que no aparezcan en la lista autorizada. Esta lista cambia conforme se ven temas nuevos en clase: lo que aparezca en un notebook nuevo de la carpeta pasa a estar autorizado.

- No uses Statsmodels salvo que la actividad pida inferencia, significancia, intervalos, influencia, leverage, VIF o un resumen estadístico de una regresión lineal, y exista un ejemplo equivalente en los notebooks.
- No reemplaces los ciclos de validación cruzada vistos en clase por funciones que oculten el procedimiento.
- No cambies una estructura que ya funciona únicamente para hacerla más avanzada, corta o elegante.
- Antes de terminar una respuesta de chat o una edición, comprueba que cada función propuesta aparezca en la lista autorizada y que la solución responda solamente a lo solicitado.
