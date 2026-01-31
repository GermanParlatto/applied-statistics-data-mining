# Airbnb Madrid - Statistical Analysis and Predictive Modeling

🌐 _[Versión en español](README_ES.md)_

## Overview

This project is a practical exercise in **applied statistics and data mining** focused on Airbnb apartment listings in Madrid. The main objective is to build a predictive model that estimates the **square meters** of apartments based on various features from the dataset.

## Dataset

The data is sourced from the [Airbnb Listings public dataset](https://drive.google.com/file/d/1CCh6EWZdzO5YLdf9lEOAVXzqbxeNxsny/view?usp=drive_link) and filtered to include only:

- Listings in **Madrid**
- Room type: **Entire home/apt**
- Apartments with a valid neighborhood

## Project Workflow

### 1. Data Preparation

- Selection of relevant columns (Price, Bedrooms, Bathrooms, Accommodates, etc.)
- Conversion of Square Feet to Square Meters
- Handling of missing values and outliers (apartments < 20 m² set to NA)

### 2. Exploratory Data Analysis

- Histogram visualization of square meters distribution
- Identification and removal of neighborhoods with no valid square meter data

### 3. Statistical Testing

- **Shapiro-Wilk test** to check for normality
- **Kruskal-Wallis test** to compare square meters across neighborhoods
- **Tukey HSD** for pairwise neighborhood comparisons

### 4. Neighborhood Clustering

- Construction of a similarity matrix based on p-values
- Hierarchical clustering (dendrogram) to group similar neighborhoods
- Creation of a synthetic variable (`neighb_id`) representing neighborhood clusters

### 5. Model Training

- **Train/Test split**: 80% training, 20% testing
- Two linear regression models:
  - **Model 1**: Direct linear regression on Square.Meters
  - **Model 2**: Log-linear regression on log(Square.Meters)

### 6. Model Evaluation

- Metrics: **RMSE**, **MAE**, **R²**
- Residual analysis: histograms, Q-Q plots
- The log-linear model showed better performance with:
  - Lower RMSE
  - Higher R²

### 7. Prediction and Imputation

- Prediction example for a 6-person apartment in Sol neighborhood
- Imputation of missing square meter values using the trained model

## Key Findings

- Significant differences exist in apartment sizes across Madrid neighborhoods
- Log transformation of the target variable improves model accuracy and reduces heteroscedasticity
- The final model can reliably estimate square meters for apartments with missing data

## Technologies Used

- **R** with libraries: `ggplot2`, `dplyr`, `caret`, `dendextend`

## How to Run

1. Place the `airbnb-listings.csv` file in the project directory
2. Open `Practica-GermanParlatto.qmd` in RStudio
3. Render the document to execute all code chunks
