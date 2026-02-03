# **Análisis del impacto del preprocesamiento de valores atípicos en modelos econométricos aplicados a series temporales económicas**

**Investigación en inteligencia artificial**

I.S.C. Manuel Alejandro Hernandez Marin

# Motivación

En el análisis econométrico de series temporales macroeconómicas y financieras es habitual la presencia de valores atípicos (outliers) debido a errores de medición, shocks económicos extraordinarios o eventos exógenos (crisis financieras, cambios regulatorios, pandemias, etc.). Estos valores atípicos pueden distorsionar significativamente la estimación de parámetros y la capacidad predictiva de los modelos econométricos tradicionales.

Aunque existen modelos econométricos robustos, en la práctica aplicada es frecuente que los analistas recurran a técnicas de preprocesamiento para detectar y corregir outliers antes del modelado. Sin embargo, no existe un consenso claro sobre si este preprocesamiento mejora sistemáticamente los resultados o si, por el contrario, introduce sesgos que alteran la dinámica real de la serie económica. Este vacío metodológico motiva el presente diseño experimental.

# Hipótesis

La hipótesis que se plantea es la siguiente:

* *La aplicación de técnicas de detección y corrección de valores atípicos en la fase de preprocesamiento mejora el desempeño predictivo y la estabilidad de los modelos econométricos clásicos sin alterar de forma significativa la dinámica subyacente de las series económicas*.


El experimento permitirá refutar o no esta hipótesis mediante la comparación sistemática de modelos entrenados con datos originales frente a datos preprocesados.

# Metodología

## Conjunto de datos

Se emplearán series temporales económicas reales obtenidas de fuentes públicas y reconocidas, como el Banco Mundial o el Fondo Monetario Internacional. En particular, se considerarán variables macroeconómicas como la inflación y el tipo de cambio, seleccionadas por su sensibilidad a shocks y eventos extremos.

Las series serán de frecuencia mensual o trimestral y cubrirán un horizonte temporal suficientemente amplio para permitir una modelización robusta.

Para garantizar la representatividad y evitar sesgos geográficos o de desarrollo, se seleccionará una muestra de 30 series temporales. Esta muestra incluirá datos de 15 economías desarrolladas y 15 economías emergentes, cubriendo un periodo de 20 años (2004-2024). Este volumen de datos asegura que la capacidad de generalización del experimento sea estadísticamente significativa y no dependa de un evento aislado en un solo país.

## Preparación de los datos

El preprocesamiento se estructurará en dos escenarios claramente diferenciados:

* Escenario A (sin preprocesamiento): se utilizarán las series originales sin modificación alguna.  
* Escenario B (con preprocesamiento): se aplicarán técnicas de detección y corrección de outliers antes del modelado.

Las técnicas de detección de valores atípicos consideradas incluirán:

* Rango intercuartílico (IQR)  
* Desviación absoluta mediana (MAD)  
* Estimación no paramétrica mediante funciones núcleo (KDE)

Una vez detectados los outliers, se aplicarán métodos de corrección como:

* Winsorización  
* Sustitución por mediana local

Este enfoque permitirá analizar el impacto específico del preprocesamiento sobre la calidad de los datos.

## Modelos econométricos

Sobre ambos escenarios se ajustarán los siguientes modelos econométricos clásicos:

* Regresión lineal por mínimos cuadrados ordinarios (OLS)  
* Modelos ARIMA para series temporales

Los parámetros de cada modelo se seleccionarán siguiendo criterios estándar de la literatura, como el análisis de autocorrelación y los criterios de información AIC y BIC.

## Métricas de evaluación

El desempeño de los modelos se evaluará mediante:

* Error absoluto medio (MAE)  
* Raíz del error cuadrático medio (RMSE)  
* Estabilidad de los parámetros estimados

Estas métricas permitirán comparar de forma objetiva los efectos del preprocesamiento.

## Diseño experimental

El experimento consistirá en entrenar y evaluar los modelos econométricos sobre ambos escenarios de datos. Para cada variable económica y cada modelo, se compararán los resultados obtenidos con y sin preprocesamiento de outliers. Se empleará validación temporal (rolling forecast) para simular condiciones realistas de predicción.  
La validación temporal mediante rolling forecast se ejecutará dividiendo cada serie en una proporción 80/20. El primer 80% de las observaciones se utilizará como conjunto de entrenamiento para el ajuste inicial de los parámetros (ARIMA/OLS). El 20% restante se reservará exclusivamente para la evaluación del desempeño predictivo (Test), asegurando que el preprocesamiento de outliers en el Escenario B no 'contamine' la información futura.

Con el fin de evitar sesgos, todos los modelos se entrenarán y evaluarán bajo las mismas condiciones, manteniendo constante el horizonte de predicción y el tamaño de las ventanas de entrenamiento.

## Comparación con estudios previos

Los resultados obtenidos se contrastarán con trabajos previos que analizan el uso de técnicas robustas y de preprocesamiento en econometría aplicada. Esta comparación permitirá contextualizar los hallazgos dentro del estado del arte y evaluar su coherencia con la literatura existente.

## Reproducibilidad

Para garantizar la reproducibilidad del experimento, se documentará detalladamente el origen de los datos, los criterios de detección de outliers, los métodos de corrección aplicados y los parámetros de los modelos econométricos. Asimismo, se especificará el entorno computacional utilizado para el análisis.

# Bibliografía

* Hampel, F. R., Ronchetti, E. M., Rousseeuw, P. J., & Stahel, W. A. (1986). Robust Statistics: The Approach Based on Influence Functions. Wiley.

* Rousseeuw, P. J., & Leroy, A. M. (2003). Robust Regression and Outlier Detection. Wiley.

* Tsay, R. S. (2010). Analysis of Financial Time Series (3rd ed.). Wiley.

