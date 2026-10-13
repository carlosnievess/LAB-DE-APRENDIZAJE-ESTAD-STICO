---
applyTo: "**/*.ipynb,**/*.py"
---

# Estructuras de Python autorizadas en LAB - G

Estas reglas se aplican al código Python y a los notebooks. La lista reúne todo lo visto en clase en `PRIMER PARCIAL` y `SEGUNDO PARCIAL`, y crece conforme se agregan notebooks nuevos a la carpeta. Si una función, clase o procedimiento no está aquí ni aparece en el enunciado o el código inicial de la actividad actual, no debe proponerse.

## Librerías permitidas

- `pandas as pd`
- `numpy as np`
- `matplotlib.pyplot as plt`
- `seaborn as sns`, solo para `sns.heatmap()` de una matriz de confusión
- `scipy.stats`, incluido `from scipy.stats import norm`
- `sklearn.linear_model`: `LinearRegression`, `Ridge`, `Lasso` y `LogisticRegression`
- `sklearn.svm`: `SVC`
- `sklearn.decomposition`: `PCA` (importado como `PCA as RandomizedPCA`, como en clase)
- `sklearn.model_selection`: `train_test_split`, `LeaveOneOut`, `KFold` y `GridSearchCV`
- `sklearn.metrics`: `mean_squared_error`, `roc_auc_score`, `classification_report` y `confusion_matrix`
- `sklearn.preprocessing`: `StandardScaler`, `OrdinalEncoder` y `OneHotEncoder`
- `sklearn.compose`: `ColumnTransformer`
- `sklearn.pipeline`: `Pipeline` y `make_pipeline`
- `sklearn.datasets`: `fetch_california_housing`, `load_iris`, `fetch_lfw_people` y `datasets.load_digits()`
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

## Regresión logística

Sigue `Regresión_logística.ipynb` y `Lab - C1.ipynb`. Si la respuesta es texto como Yes/No, conviértela antes, por ejemplo con `df["default"] == "Yes"` o `(df["student"] == "Yes").astype(int)`.

```python
modelo = LogisticRegression()
modelo.fit(X, y)

b0 = modelo.intercept_[0]
b1 = modelo.coef_[0][0]

prob = modelo.predict_proba(X)[:, 1]
```

- El parámetro `C` es el inverso de la fuerza de la regularización. Usa el valor que pida la actividad, como `C=0.000001` o `C=1000000`. Para estimar coeficientes sin penalización se usó `LogisticRegression(C=1000000, max_iter=1000, tol=1e-8)`.
- Para varios coeficientes, júntalos con `np.hstack([modelo.intercept_, modelo.coef_[0]])`.
- La probabilidad manual de un factor es `p = 1 / (1 + np.exp(-(b0 + b1 * x)))`.

### Errores estándar, z y p-value

```python
w = prob * (1 - prob)
V = np.diagflat(w)

# La columna de unos corresponde al intercepto
X_diseno = np.hstack([np.ones((len(X), 1)), X.values])
cov = np.linalg.inv(X_diseno.T @ V @ X_diseno)
se = np.sqrt(np.diag(cov))

z_statistic = beta / se
p_value = 2 * (1 - norm.cdf(abs(z_statistic)))
```

Presenta el resultado en un `pd.DataFrame` con las columnas `Coeficiente`, `Error estándar`, `z` y `p-value`, y los nombres de los factores como índice.

### Métricas por umbral

Clasifica con `y_pred = (prob >= t).astype(int)` dentro de un ciclo sobre los umbrales pedidos. Cuenta TP, TN, FP y FN con comparaciones booleanas y `.sum()`, y calcula a mano:

```python
acc = (tp + tn) / (tp + tn + fp + fn)
rec = tp / (tp + fn)
pre = tp / (tp + fp)
esp = tn / (tn + fp)
```

Guarda cada vuelta en una lista y al final construye un `pd.DataFrame`.

## SVM, AUC y validación cruzada en clasificación

Sigue `Lab - C2.ipynb`. Los modelos se guardan en una lista de pares `(nombre, modelo)`:

```python
modelos = [
    ("SVC linear", SVC(kernel="linear", probability=True, random_state=42)),
    ("SVC rbf", SVC(kernel="rbf", probability=True, random_state=42)),
    ("LogisticRegression", LogisticRegression()),
]
```

`probability=True` es necesario para usar `predict_proba` y calcular el AUC. Evalúa con un ciclo explícito de `KFold`, con el escalamiento dentro de un `Pipeline` para ajustarlo solo con el grupo de entrenamiento:

```python
kf = KFold(n_splits=10, shuffle=True, random_state=42)
resultados = []

for nombre, modelo in modelos:
    auc = []

    for train, test in kf.split(X):
        pipeline = Pipeline(steps=[
            ("preprocessor", preprocessor),
            ("model", modelo)
        ])
        pipeline.fit(X.iloc[train], y.iloc[train])
        prob = pipeline.predict_proba(X.iloc[test])[:, 1]
        auc.append(roc_auc_score(y.iloc[test], prob))

    resultados.append([nombre, np.mean(auc), np.std(auc)])
```

- Con más de dos clases, como Iris, usa `prob = pipeline.predict_proba(X[test])` completo y `roc_auc_score(y[test], prob, multi_class="ovr", average="macro")`.
- Si el dataset viene ordenado por clase, usa `shuffle=True` en `KFold`.
- Presenta `resultados` como `pd.DataFrame` con las columnas `Modelo`, `AUC promedio` y `Desviación estándar`.

## SVM con PCA, búsqueda de parámetros y evaluación

Sigue `04_Ingenieria_inversa.ipynb`. Esta estructura viene de una plantilla del profesor y se usa para ejercicios de ese tipo, como clasificar imágenes:

```python
pca = RandomizedPCA(n_components=150, whiten=True, random_state=42)
svc = SVC(kernel="rbf", class_weight="balanced")
model = make_pipeline(pca, svc)

Xtrain, Xtest, ytrain, ytest = train_test_split(data.data, data.target, random_state=42)

param_grid = {"svc__C": [1, 5, 10, 50],
              "svc__gamma": [0.0001, 0.0005, 0.001, 0.005]}
grid = GridSearchCV(model, param_grid)
grid.fit(Xtrain, ytrain)
print(grid.best_params_)

model = grid.best_estimator_
yfit = model.predict(Xtest)
```

- Evalúa con `print(classification_report(ytest, yfit, target_names=...))`.
- Para la matriz de confusión: `mat = confusion_matrix(ytest, yfit)` y `sns.heatmap(mat.T, square=True, annot=True, fmt="d", cbar=False, xticklabels=..., yticklabels=...)`.
- Para mostrar imágenes: `fig, ax = plt.subplots(filas, columnas)`, un ciclo `for i, axi in enumerate(ax.flat)` con `axi.imshow(..., cmap="bone")` y `axi.set(xticks=[], yticks=[], xlabel=...)`. Para marcar errores: `color="black" if yfit[i] == ytest[i] else "red"`.
- `GridSearchCV` y `make_pipeline` solo se usan en esta estructura. En los demás ejercicios se conservan `Pipeline` y el ciclo explícito de `KFold`.

## Exploración de datos para clasificación

Además de lo del primer parcial, se vieron `astype("category")`, `df.boxplot(column=..., by=...)` con `plt.suptitle("")`, y `df.plot.scatter(x=..., y=..., c=..., colormap="PiYG_r", alpha=0.5)`.

## Respuesta a comentarios

Cuando una celda termine con un comentario como `# cargar los datos`, `# separar X y y`, `# ajustar el modelo`, `# predecir`, `# calcular el MSE` o `# graficar los residuos`, completa únicamente ese paso y utiliza las estructuras anteriores. No adelantes pasos posteriores ni generes una solución completa si el comentario solicita una sola parte.
