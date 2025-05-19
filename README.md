# Ajuste de hiperparámetros
# Proyecto de Clasificación de Calidad de Vino Tinto

## 1. Introducción

Este proyecto tiene como objetivo desarrollar modelos de clasificación para predecir la calidad de vinos tintos, categorizándolos como "buenos" o "malos" basándose en diversas características fisicoquímicas. Se exploraron y compararon tres enfoques de modelado: un modelo baseline de Regresión Logística con hiperparámetros por defecto, un modelo ajustado mediante búsqueda aleatoria de hiperparámetros y un modelo ajustado utilizando la biblioteca de optimización bayesiana Optuna. La predicción precisa de la calidad del vino puede ofrecer insights valiosos para la industria vinícola.

## 2. Conjunto de Datos

El conjunto de datos utilizado es "winequality-red.csv", que contiene información sobre las características fisicoquímicas de diferentes vinos tintos y una puntuación de calidad entre 3 y 8. Para facilitar la tarea de clasificación, la variable objetivo 'quality' se transformó en una variable binaria 'quality_binaria', donde los vinos con una calidad ≥ 7 se consideran "buenos" (1) y aquellos con calidad < 7 se consideran "malos" (0).

### 2.1. Explicación de las Variables

* **fixed acidity (acidez fija):** Ácidos no volátiles presentes en el vino.
* **volatile acidity (acidez volátil):** Cantidad de ácido acético, que en exceso puede dar un sabor a vinagre.
* **citric acid (ácido cítrico):** Ácido que puede añadir frescura y sabor.
* **residual sugar (azúcar residual):** Azúcar restante después de la fermentación.
* **chlorides (cloruros):** Cantidad de sal en el vino.
* **free sulfur dioxide (dióxido de azufre libre):** Forma activa del SO2 con propiedades antioxidantes y germicidas.
* **total sulfur dioxide (dióxido de azufre total):** Suma del dióxido de azufre libre y combinado.
* **density (densidad):** Densidad del vino, influenciada por el alcohol y el azúcar.
* **pH:** Medida de la acidez o basicidad del vino.
* **sulphates (sulfatos):** Aditivo que actúa como antimicrobiano.
* **alcohol:** Porcentaje de contenido de alcohol del vino.
* **quality (calidad):** Puntuación de calidad sensorial (variable original, 3-8).
* **quality_binaria:** Variable objetivo binaria (0 = Mala, 1 = Buena).

## 3. Metodología

El proyecto siguió los siguientes pasos:

1.  **Importación y Exploración de Datos:** Carga y análisis inicial del dataset.
2.  **Detección y Manejo de Outliers:** Identificación de valores atípicos mediante el método IQR y aplicación de transformación logarítmica para mitigar su impacto.
3.  **Preparación de Datos:** División del dataset en conjuntos de entrenamiento y prueba.
4.  **Reducción de Dimensionalidad (PCA):** Aplicación de PCA para reducir la dimensionalidad a 6 componentes, conservando la mayor parte de la varianza.
5.  **Modelado Baseline:** Entrenamiento de un modelo de Regresión Logística con hiperparámetros por defecto.
6.  **Ajuste de Hiperparámetros con Búsqueda Aleatoria:** Optimización de hiperparámetros de la Regresión Logística mediante búsqueda aleatoria y validación cruzada.
7.  **Ajuste de Hiperparámetros con Optuna:** Optimización de hiperparámetros de la Regresión Logística utilizando la biblioteca Optuna (optimización bayesiana) y validación cruzada.
8.  **Comparación de Modelos:** Evaluación y comparación del rendimiento de los tres modelos utilizando la métrica AUC ROC.
9.  **Conclusiones:** Análisis de los resultados y resumen de los hallazgos.

## 4. Resultados

Los resultados de la evaluación de los modelos en el conjunto de prueba (utilizando AUC ROC) fueron los siguientes:

* **Modelo Baseline:** 0.9974
* **Modelo Ajustado con Búsqueda Aleatoria:** 0.9971
* **Modelo Ajustado con Optuna (6 componentes):** 0.9974

El rendimiento en la validación cruzada del conjunto de entrenamiento también se analizó, mostrando una tendencia similar.

## 5. Conclusiones

Los tres modelos de Regresión Logística demostraron una alta capacidad para clasificar la calidad del vino tinto. Sorprendentemente, el modelo baseline ofreció un rendimiento comparable al de los modelos con hiperparámetros ajustados, sugiriendo que para este problema específico, un modelo lineal con la configuración predeterminada es muy efectivo. La optimización de hiperparámetros con Optuna logró igualar el rendimiento del baseline, mientras que la búsqueda aleatoria también produjo un resultado muy competitivo. Este proyecto destaca la importancia de establecer un buen baseline y la efectividad de la Regresión Logística para tareas de clasificación bien definidas.
