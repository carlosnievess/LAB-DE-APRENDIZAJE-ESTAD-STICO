---
applyTo: "**/*.ipynb,**/*.py"
---

# Estructuras de Python autorizadas en LAB - G

Estas reglas se aplican al código Python y a los notebooks. La lista es cerrada. Si una función, clase o procedimiento no está aquí ni aparece en el código inicial de la actividad actual, no debe proponerse.

## Librerías permitidas

- `pandas as pd`
- `numpy as np`
- `matplotlib.pyplot as plt`
- `scipy.stats`
- `sklearn.linear_model`: `LinearRegression`, `Ridge` y `Lasso`
- `sklearn.model_selection`: `train_test_split`, `LeaveOneOut` y `KFold`
- `sklearn.metrics`: `mean_squared_error`
- `sklearn.preprocessing`: `StandardScaler`, `OrdinalEncoder` y `OneHotEncoder`
- `sklearn.compose`: `ColumnTransformer`
- `sklearn.pipeline`: `Pipeline`
- `sklearn.datasets`: `fetch_california_housing`
- `statsmodels.api as sm` únicamente en los casos permitidos por las instrucciones generales
- `variance_inflation_factor` únicamente para VIF

## Pandas y revisión del dataset

Se pueden usar `pd.read_csv()`, `pd.read_excel()`, `head()`, `tail()`, `shape`, `columns`, `dtypes`, `info()`, `describe()`, `isna().sum()`, `duplicated().sum()`, `drop_duplicates()`, `dropna()`, `drop()`, `value_counts()`, `quantile()`, `median()`, `std()`, `map()`, `astype()`, limpieza de texto con `.str`, `pd.DataFrame()` y `pd.concat()`.

Para separar variables, conserva la estructura vista en clase:

```python
X = df.drop(columns=["variable_respuesta"])
y = df["variable_respuesta"]
```

Cuando se use una sola variable explicativa en Scikit-learn, conserva dos dimensiones:

```python
X = df[["factor"]]
y = df["respuesta"]
```

## Regresión lineal

Para el modelo automatizado utiliza esta secuencia:

```python
modelo = LinearRegression()
modelo.fit(X, y)
y_pred = modelo.predict(X)
modelo.score(X, y)
```

Se permiten `intercept_` y `coef_`. Si la actividad pide la solución analítica, calcula `b0` y `b1` con promedios, sumas y diferencias como se hizo en `Lab - R1.ipynb`.

Para regresión polinomial, crea las potencias manualmente con `reshape()` y `np.hstack()`. No uses `PolynomialFeatures`.

## Regresión múltiple e inferencia

Para un ajuste ordinario se prefiere `LinearRegression`. Se permite `sm.add_constant()`, `sm.OLS()`, `fit()` y `summary()` cuando el enunciado solicite coeficientes, errores estándar, estadísticos t, p-values, intervalos o diagnóstico estadístico.

Si la actividad pide el procedimiento manual, se permiten residuos, RSS, RSE, errores estándar, estadísticos t y p-values mediante operaciones de NumPy y `scipy.stats`, siguiendo `Lab - R2.ipynb`.

## Escalamiento y variables categóricas

Se permite calcular Min-Max y estandarización manualmente. Cuando no se pida el procedimiento manual, utiliza `StandardScaler()` con `fit_transform()` o dentro de un `ColumnTransformer`.

Para variables ordinales se permite `map()` u `OrdinalEncoder()`. Para variables no ordinales se permite codificación manual con `np.where()` o `OneHotEncoder()`.

## Separación, penalización y evaluación

Para dividir datos utiliza `train_test_split()` solamente con los valores de `test_size` y `random_state` indicados en la actividad.

Para penalización utiliza:

```python
ridge = Ridge(alpha=valor)
lasso = Lasso(alpha=valor)
```

Después aplica `fit()`, `predict()`, `score()`, `intercept_` y `coef_` como en `Lab - R4.ipynb`. No estandarices ni cambies la partición si el ejercicio no lo solicita.

Para MSE utiliza `mean_squared_error(y_real, y_pred)`. Distingue claramente entre promedio del MSE y desviación estándar de los MSE.

## Validación cruzada

Implementa LOOCV con `LeaveOneOut()` y K-Fold con `KFold()` mediante ciclos explícitos. En cada vuelta, separa con `.iloc`, ajusta el modelo, predice y guarda el MSE. Al final calcula `np.mean()` y `np.std()`.

No uses `cross_val_score` ni funciones que sustituyan el ciclo visto en `Lab - R5.ipynb`.

## ColumnTransformer y Pipeline

Conserva esta organización cuando existan variables numéricas, categóricas y booleanas:

```python
preprocessor = ColumnTransformer(
    transformers=[
        ("num", StandardScaler(), numerical_cols),
        ("cat", OneHotEncoder(), categorical_cols),
        ("bool", "passthrough", boolean_cols)
    ],
    remainder="drop"
)

modelo = LinearRegression()

pipeline = Pipeline(
    steps=[
        ("preprocessor", preprocessor),
        ("model", modelo)
    ]
)

pipeline.fit(X, y)
y_pred = pipeline.predict(X)
```

No transformes `X` por fuera antes de entregarlo al `pipeline`, puesto que el preprocesamiento ya se realiza dentro.

## Residuos y gráficas

Calcula los residuos con:

```python
residuos = y - y_pred
```

En los diagnósticos utiliza la variable indicada por los apuntes de clase. Generalmente se grafica contra `y_pred`; en el problema de correlación se conserva `y` observada, y en puntos palanca el eje horizontal corresponde a `h` y el vertical a los residuos.

Usa Matplotlib con instrucciones sencillas como `plt.figure()`, `plt.scatter()`, `plt.plot()`, `plt.axhline()`, `plt.xlabel()`, `plt.ylabel()`, `plt.title()`, `plt.legend()`, `plt.grid()` y `plt.show()`.

## Respuesta a comentarios

Cuando una celda termine con un comentario como `# cargar los datos`, `# separar X y y`, `# ajustar el modelo`, `# predecir`, `# calcular el MSE` o `# graficar los residuos`, completa únicamente ese paso y utiliza las estructuras anteriores. No adelantes pasos posteriores ni generes una solución completa si el comentario solicita una sola parte.
