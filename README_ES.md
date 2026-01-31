# Airbnb Madrid - Análisis Estadístico y Modelado Predictivo

🌐 _[English version](README.md)_

## Descripción General

Este proyecto es un ejercicio práctico de **estadística aplicada y minería de datos** enfocado en los listados de apartamentos de Airbnb en Madrid. El objetivo principal es construir un modelo predictivo que estime los **metros cuadrados** de los apartamentos basándose en diversas características del dataset.

## Dataset

Los datos provienen del [dataset público de Airbnb Listings](https://drive.google.com/file/d/1CCh6EWZdzO5YLdf9lEOAVXzqbxeNxsny/view?usp=drive_link) y se filtran para incluir únicamente:

- Listados en **Madrid**
- Tipo de habitación: **Entire home/apt** (vivienda completa)
- Apartamentos con barrio válido

## Flujo de Trabajo del Proyecto

### 1. Preparación de Datos

- Selección de columnas relevantes (Precio, Dormitorios, Baños, Capacidad, etc.)
- Conversión de pies cuadrados a metros cuadrados
- Tratamiento de valores faltantes y outliers (apartamentos < 20 m² establecidos como NA)

### 2. Análisis Exploratorio de Datos

- Visualización mediante histogramas de la distribución de metros cuadrados
- Identificación y eliminación de barrios sin datos válidos de metros cuadrados

### 3. Tests Estadísticos

- **Test de Shapiro-Wilk** para verificar normalidad
- **Test de Kruskal-Wallis** para comparar metros cuadrados entre barrios
- **Tukey HSD** para comparaciones por pares entre barrios

### 4. Clustering de Barrios

- Construcción de una matriz de similitud basada en p-valores
- Clustering jerárquico (dendrograma) para agrupar barrios similares
- Creación de una variable sintética (`neighb_id`) que representa los clusters de barrios

### 5. Entrenamiento del Modelo

- **División Train/Test**: 80% entrenamiento, 20% prueba
- Dos modelos de regresión lineal:
  - **Modelo 1**: Regresión lineal directa sobre Square.Meters
  - **Modelo 2**: Regresión log-lineal sobre log(Square.Meters)

### 6. Evaluación del Modelo

- Métricas: **RMSE**, **MAE**, **R²**
- Análisis de residuos: histogramas, gráficos Q-Q
- El modelo log-lineal mostró mejor rendimiento con:
  - Menor RMSE
  - Mayor R²

### 7. Predicción e Imputación

- Ejemplo de predicción para un apartamento de 6 personas en el barrio Sol
- Imputación de valores faltantes de metros cuadrados usando el modelo entrenado

## Hallazgos Principales

- Existen diferencias significativas en el tamaño de los apartamentos entre los barrios de Madrid
- La transformación logarítmica de la variable objetivo mejora la precisión del modelo y reduce la heterocedasticidad
- El modelo final puede estimar de forma fiable los metros cuadrados para apartamentos con datos faltantes

## Tecnologías Utilizadas

- **R** con librerías: `ggplot2`, `dplyr`, `caret`, `dendextend`

## Cómo Ejecutar

1. Colocar el archivo `airbnb-listings.csv` en el directorio del proyecto
2. Abrir `Practica-GermanParlatto.qmd` en RStudio
3. Renderizar el documento para ejecutar todos los bloques de código

## Licencia y Atribución

- **Dataset**: Los datos de listados de Airbnb se proporcionan bajo licencia [Creative Commons CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Fuente original: [Inside Airbnb](http://insideairbnb.com/).
- **Código**: Este proyecto tiene fines educativos.
