# 📊 Evaluación del Sesgo en el Algoritmo COMPAS

## Introducción

En este notebook, se llevará a cabo un análisis exhaustivo del sesgo presente en el algoritmo COMPAS (Correctional Offender Management Profiling for Alternative Sanctions). COMPAS es una herramienta ampliamente utilizada en el sistema de justicia penal de los Estados Unidos para evaluar la probabilidad de reincidencia de los acusados. Esta herramienta proporciona puntuaciones de riesgo que son utilizadas por jueces y oficiales de libertad condicional para tomar decisiones informadas sobre la detención, sentencia y liberación de los acusados.

### Contexto del Algoritmo COMPAS

COMPAS utiliza una serie de factores, incluyendo datos demográficos y antecedentes penales, para generar una puntuación de riesgo (campo *decile_score* en el dataset) que varía entre 1 y 10. Esta puntuación indica la probabilidad de que un individuo cometa un nuevo delito en el futuro. Sin embargo, estudios recientes han planteado preocupaciones significativas sobre la equidad de COMPAS, señalando que el algoritmo puede estar sesgado en contra de ciertos grupos demográficos, especialmente los afroamericanos.

### Objetivo del Análisis

El objetivo principal de este análisis es evaluar el sesgo racial en el algoritmo COMPAS, específicamente cómo afecta a los individuos afroamericanos en comparación con otros grupos demográficos. También se investigará otro posible sesgo existente en la característica de género o "sex" en el dataset. Para lograr esto, se llevarán a cabo las siguientes tareas:

1. **🔍 Exploración y Transformación de Datos**: Se analizará el conjunto de datos de manera visual y estadística para comprender su estructura y características. Incluye la eliminación de ciertas variables no útiles, codificación de variables y establecimiento de un umbral para las probabilidades otorgadas por COMPAS. De esta forma se logra una nueva columna *compas_recid* binaria para comparar con el ground truth de reincidencia (*is_recid*).
2. **🤖 Modelo *Custom***: Se creará y entrenará una pipeline con la que después se predice. Esta pipeline incluye un modelo ensamblado binario. Las predicciones de este modelo se usan para comparar y evaluar el sesgo de COMPAS.
3. **📈 Cálculo de Métricas de Rendimiento**: Se evaluará la precisión, recall, F1-score y otras métricas del modelo COMPAS y del modelo custom y se compararán.
4. **🔍 Análisis de la Matriz de Confusión**: Se compararán las tasas de falsos positivos (FP) y falsos negativos (FN) entre diferentes grupos raciales y entre ambos modelos.
5. **📉 Curvas ROC**: Se generarán y analizarán las curvas ROC para distintos grupos demográficos.
6. **⚖️ Identificación de Disparidades**: Se identificarán y cuantificarán las disparidades en las tasas de error de predicción entre los grupos demográficos y entre los géneros.
7. **📝 Recomendaciones**: Se proporcionarán recomendaciones sobre cómo abordar los sesgos identificados en el modelo COMPAS y posibles siguientes pasos.

### Estructura del Notebook

1. **📥 Carga de Datos y Preprocesamiento**: Se importará el conjunto de datos de COMPAS y se realizarán las transformaciones necesarias para su análisis.
2. **📊 Exploración de Datos**: Se visualizarán y describirán las características principales del conjunto de datos.
3. **🏋️‍♂️ Entrenamiento de Modelos**: Se entrenará un modelo "custom" y se comparará su rendimiento con el modelo COMPAS.
4. **🔍 Evaluación de Sesgo**: Se realizarán análisis detallados de las métricas de rendimiento y se evaluará el sesgo racial.
5. **📜 Conclusiones y Recomendaciones**: Se discutirán los resultados obtenidos y se proporcionarán recomendaciones para abordar los sesgos identificados.

### Fuentes de Información

- **COMPAS Dataset**: [ProPublica COMPAS Data](https://github.com/propublica/compas-analysis)
- **Estudios sobre Sesgo en COMPAS**: 
  - [Machine Bias - ProPublica](https://www.propublica.org/article/machine-bias-risk-assessments-in-criminal-sentencing)
  - [Fairness and Machine Learning - O'Reilly Media](https://www.oreilly.com/library/view/fairness-and-machine/9781492071256/)
- **Herramientas Utilizadas**:
  - [AIF360 - A comprehensive toolkit for fairness in AI](https://aif360.mybluemix.net/)
  - [Scikit-Learn - Machine Learning in Python](https://scikit-learn.org/stable/)

A lo largo de este notebook, no solo se buscará identificar los sesgos presentes, sino también proporcionar un marco para mitigarlos, asegurando así que las herramientas de evaluación de riesgos sean más justas y equitativas.

