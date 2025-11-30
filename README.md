# Inteligencia_Artificial_TareaAcademica_Grupo8_H783
**Repositorio para la tarea académica del curso de Inteligencia Artificial 1INF24**

Este repositorio contiene el trabajo realizado por los estudiantes del curso de **Inteligencia Artificial (1INF24)**. A continuación, se presentan los miembros del grupo 8:

- **Ariana Burga**, código 20226705
- **John Arzapalo**, código 20202098
- **Alessandro Santé**, código 20223006
- **Ricardo Lara**, código 20221548
- **Juan Zavala**, código 20226608
- **Luis Miranda**, código 20223796

## Descripción del Proyecto

El objetivo principal de este proyecto es **pronosticar la tasa de natalidad en Perú** mediante el uso de **modelos predictivos**. Este desarrollo tiene como base un dataset proporcionado por el **gobierno del Perú** con registros de los últimos 10 años (2015-2025), y se utilizará para apoyar la **planificación estratégica del sector salud, educativo y pensionario**.

## Metodología

Para resolver el problema propuesto, se implementó un pipeline de procesamiento que incluye limpieza, transformación, integración geográfica y agregación espacio-temporal de los datos. Se emplearon y compararon **cinco modelos de machine learning** representando distintos paradigmas algorítmicos.

### Preprocesamiento de Datos

1. **Limpieza y Validación**: Eliminación de registros duplicados, tratamiento de valores inválidos y normalización de variables numéricas especiales.
2. **Integración Geográfica**: Vinculación de nacimientos con el catálogo de Ubigeo del INEI para enriquecimiento con información departamental.
3. **Agregación Espacio-Temporal**: Transformación de registros individuales en un panel trimestral-departamental.
4. **Ingeniería de Características**:
   - Creación de variables temporales: lag1, lag4, ma4 (media móvil de 4 trimestres)
   - Variables sociodemográficas agregadas: edad materna, educación, estado civil, características reproductivas
   - Codificación one-hot para la variable departamento
5. **División Temporal**: 
   - Dev: 2015-2023
   - Prueba: 2024-2025 (excluyendo período COVID-19: 2020-2021-T2)

### Algoritmos Utilizados

- **Regresión Lineal**: Modelo baseline para establecer relaciones lineales
- **K-Nearest Neighbors (KNN)**: Con k=5 y k=10 para capturar patrones de similitud
- **Árbol de Regresión**: Configurado con máxima profundidad 6 para relaciones no lineales
- **Random Forest**: Ensemble de 100 árboles con máxima profundidad 6
- **XGBoost**: Modelo de boosting con 200 estimadores, learning rate 0.05 y máxima profundidad 6

### Evaluación del Modelo

Se utilizaron las métricas de **R2, RMSE y MAE** con **validación cruzada temporal (TimeSeriesSplit)** de 5 folds para evaluar la precisión y robustez de las predicciones en secuencias temporales futuras.

## Resultados Principales

- **Mejor modelo**: XGBoost demostró el mejor desempeño predictivo con R2 = 0.9107 y MAE = 0.1618 en el conjunto de prueba
- **Variables más influyentes**: Las categorías temporal (53.08%) y geográfica (38.77%) explican conjuntamente más del 90% del poder predictivo
- **Departamentos con mayor variabilidad**: Huancavelica y Madre de Dios mostraron la mayor influencia predictiva
- **Impacto COVID-19**: La exclusión del período pandémico mejoró significativamente todas las métricas del modelo

## Conclusiones

El modelo XGBoost validó exitosamente la hipótesis inicial, superando los umbrales establecidos de R2 > 0.7 y MAE < 0.5. El análisis reveló que los patrones espacio-temporales agregados capturan mejor la dinámica demográfica que las variables sociodemográficas individuales. La metodología implementada demuestra que los enfoques de machine learning pueden capturar relaciones no lineales complejas en datos demográficos, ofreciendo una alternativa robusta a los métodos tradicionales de proyección para la planificación descentralizada de políticas públicas.

## Trabajo Futuro

- Incorporar indicadores de empleo, pobreza y migración para capturar determinantes estructurales
- Desarrollar predictores específicos para costa, sierra y selva considerando sus dinámicas particulares
- Implementar modelos que detecten cambios abruptos usando técnicas de detección de anomalías
- Combinar XGBoost con modelos de series temporales profundas (LSTM, Transformer)
- Desarrollar un dashboard en tiempo real para tomadores de decisiones

## Contribuciones de los Miembros del Equipo

- **John Arzapalo**: Cálculo de la población trimestral y documentación de datasets
- **Ariana Burga**: Búsqueda bibliográfica, análisis comparativo COVID-19, análisis de variables influyentes y redacción
- **Ricardo Lara**: Preprocesamiento, exploración de modelos, elaboración de presentación e inciso de modelos
- **Luis Miranda**: Preprocesamiento, documentación de datasets y notebooks, redacción del informe
- **Alessandro Santé**: Preprocesamiento del dataset original, cálculo de variable target, adición de variables lag, investigación de TimeSeriesSplit
- **Juan Zavala**: Búsqueda bibliográfica, resúmenes críticos de fuentes y ejecución del preprocesamiento completo

## Repositorio

El código, datasets y recursos utilizados en este proyecto están disponibles en el siguiente repositorio: 
**[https://github.com/LuisMirandaMallqui/Inteligencia_Artificial_TareaAcademica_Grupo8_H783.git](https://github.com/LuisMirandaMallqui/Inteligencia_Artificial_TareaAcademica_Grupo8_H783)**
