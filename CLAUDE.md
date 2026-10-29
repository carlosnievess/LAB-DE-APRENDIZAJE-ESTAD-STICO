# LAB - G: Laboratorio de Aprendizaje Estadístico

Actividades escolares en Jupyter Notebook (Python). Alumno: Carlos Enrique Nieves Ochoa, expediente 758210.
Cada notebook empieza con una tabla de Nombre, Fecha y Expediente: llénala con la fecha del día de entrega.

## Regla principal: solo métodos vistos en clase

Esta regla está por encima de cualquier otra consideración, incluida la de escribir código más corto,
eficiente o elegante.

- Usa únicamente librerías, clases, funciones, métodos, parámetros y procedimientos que aparezcan en
  alguno de estos dos lugares:
  1. Los notebooks ya hechos de esta carpeta (lista en "Notebooks registrados").
  2. El enunciado o el código inicial de la actividad nueva.
- Lo que aparece en un notebook queda permitido para todas las actividades posteriores.
- No uses atajos ni versiones más sofisticadas de lo visto, aunque den el mismo resultado: por ejemplo,
  `cross_val_score` en lugar del ciclo de K-Fold, comprensiones o funciones propias donde en clase se
  escribió el paso a paso.
- Si lo vimos de forma manual y después automatizada, usa la forma más reciente vista, salvo que el
  enunciado pida la manual.
- Si la actividad pide algo que no aparece en ningún notebook ni en el enunciado, no lo resuelvas con una
  técnica nueva: avisa qué falta y pregunta antes de continuar.
- Antes de entregar, revisa cada función y método que usaste y confirma en qué notebook o en qué parte del
  enunciado aparece.

## Lista de lo visto en clase

Lo visto en clase, con sus estructuras y su notebook de referencia, vive en `.github/`. Copilot usa los
mismos archivos para recomendar código en los exámenes a partir de un comentario, así que deben reflejar
siempre todo lo visto en los notebooks:

@.github/copilot-instructions.md
@.github/instructions/python-clase.instructions.md

## Cómo hacer una actividad

1. Revisa si hay cambios en la carpeta (sección siguiente).
2. Lee el enunciado completo del notebook y su código inicial.
3. Revisa el notebook de referencia del tema en `.github/copilot-instructions.md`.
4. Completa las celdas sin agregar análisis que no se pidieron.
5. No ejecutes el notebook: solo agrega o cambia las celdas en el archivo y el alumno lo ejecuta. Ejecútalo
   únicamente si lo pide en ese momento.
6. Al terminar, propone actualizar la sección "Avance".

## Revisar cambios al empezar cada sesión

Al empezar una actividad de esta materia, compara la carpeta con lo registrado aquí:

- Ejecuta `git status` y `git log --oneline <commit de "Última revisión">..HEAD` en la carpeta del proyecto.
- Busca notebooks que no estén en "Notebooks registrados" y notebooks registrados que hayan cambiado.
- Si hay notebooks nuevos o cambiados, lee qué librerías, funciones, métodos y estructuras usan y
  actualiza estos archivos:
  - `.github/instructions/python-clase.instructions.md`: agrega lo nuevo a "Librerías permitidas" y, si es
    un tema nuevo, una sección con su estructura tal como aparece en el notebook.
  - `.github/copilot-instructions.md`: agrega el notebook a "Fuentes de referencia por tema" y quita de
    "Herramientas que todavía no se han visto" lo que ya apareció.
  - Este archivo: "Notebooks registrados", "Avance" y "Última revisión".
- Después dile al alumno, antes de empezar la actividad, qué notebook detectaste y qué quedó permitido.
- Si no hay cambios, no digas nada y sigue con la actividad.

Última revisión: commit `c744a1d` (28 oct 2026).

## Notebooks registrados

PRIMER PARCIAL: `1. Regresión`, `2.Regresiónmúltiple`, `6 problemas de la regresion lineal`,
`A01-REGRESIÓNLINEAL`, `A02 - Escalamiento`, `A03 - Codificacion de variables categoricas`,
`A04 - Análisis de residuos`, `Corrección_examen_1`, `Lab - R1`, `Lab - R2`, `Lab - R3`, `Lab - R4`,
`Lab - R5`, `Pipeline`, `Regresión sin penalización y Ridge`.

SEGUNDO PARCIAL: `04_Ingenieria_inversa`, `Lab - C1`, `Lab - C2`, `Lab - C3`,
`Laboratorio de métodos de búsqueda`, `MLP con hiperparámetros(neuronas)`, `Optimización Bayesiana`,
`Regresión_logística`.

## Avance

| Parcial | Actividad | Estado |
| :- | :- | :- |
| Primero | Lab - R1 a R5, A01 a A04, Pipeline, corrección del examen 1 | Terminados |
| Segundo | Regresión logística (clase) | Terminado |
| Segundo | Lab - C1: regresión logística con Default | Terminado (4 oct 2026) |
| Segundo | 04 Ingeniería inversa: rostros con SVM | Terminado (8 oct 2026) |
| Segundo | Lab - C2: SVM, kernels y AUC | Terminado (11 oct 2026) |
| Segundo | Lab - C3: perceptrón multicapa con Brain Tumor | Terminado (19 oct 2026) |
| Segundo | MLP con hiperparámetros (neuronas) y Optimización Bayesiana (clase) | Terminados |
| Segundo | Laboratorio de métodos de búsqueda: GridSearchCV, RandomizedSearchCV y Optuna con College | Terminado (29 oct 2026) |
