# Rainfall Prediction in Australia

This project uses a machine learning pipeline to predict whether it will rain in Australia tomorrow, based on historical weather data. It implements techniques such as exploratory data analysis, feature preprocessing, and model selection. The final model achieves high accuracy using XGBoost and provides insights through global and local feature importance analysis.

## Table of Contents
- [Introduction](#introduction)
- [Project Structure](#project-structure)
- [Setup](#setup)
- [Usage](#usage)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Preprocessing](#preprocessing)
- [Results](#results)
- [License](#license)

## Introduction
Rain plays a crucial role in sustaining life, agriculture, and ecosystems. Accurate rainfall predictions can support better planning and decision-making, especially in regions like Australia with highly variable weather patterns. 

This project is built on the Kaggle "Rain in Australia" dataset, which contains 10 years of daily weather observations from 49 stations. The goal is to predict whether it will rain the next day based on these observations.

## Project Structure
```plaintext
project/
│
├── data/                   # Data files (not included)
├── notebooks/              # Jupyter notebooks for EDA and modeling
├── src/                    # Source code for the ML pipeline
│   ├── preprocessing.py    # Data preprocessing scripts
│   ├── train.py            # Model training scripts
│   └── evaluate.py         # Evaluation scripts
├── requirements.yaml       # Dependency file
├── LICENSE                 # License file
└── README.md               # This file
```

## Dataset Overview

The dataset contains 10 years of daily weather observations from 49 weather stations in Australia. It consists of:

- **145,460 rows** and **23 columns** (16 continuous variables, 6 categorical variables, and 1 target variable).
- **Target Variable:** `RainTomorrow` (binary classification: "Yes" or "No").

### Key Insights:
- The dataset is imbalanced, with ~70% of samples labeled as "No" for rain.
- Missing values are significant, with 21 out of 23 columns containing missing values.
- **Temperature and Wind Direction** are key predictive factors:
  - Minimum temperatures are higher, and maximum temperatures are lower before rainy days.
  - The northwest wind direction has the highest association with rainfall.

### Visualizations:
1. **Class Balance:** Bar plots showing the imbalance in `RainToday` and `RainTomorrow`.
2. **Temperature vs Rain:** Box plots comparing minimum and maximum temperatures between rainy and non-rainy days.
3. **Correlation Plot:** Strong correlations are observed among features like temperatures and pressures.

---

## Preprocessing

The preprocessing pipeline ensures the dataset is ready for training:

### Handling Missing Values:
- **Categorical Variables:** Missing values are imputed with a new class `"other"`.
- **Continuous Variables:** Missing values are not imputed; a reduced-feature method is used to avoid distortion.

### Encoding:
- **Categorical Variables:** One-hot encoded.
- **Continuous Variables:** Normalized using a standard scaler.

### Feature Reduction:
- Highly correlated features (e.g., `Temp9am`, `Temp3pm`, `Pressure3pm`) are removed to avoid redundancy.

### Post-Preprocessing:
- **116 features**
- **142,193 observations**

---

## Results

### Machine Learning Models Tested:
- Logistic Regression (L1 and L2 regularization)
- Random Forest
- K-Nearest Neighbors (KNN)
- XGBoost

### Model Performance:
XGBoost achieved the highest test accuracy of **0.869**, outperforming other models. Below is a comparison:

| **Model**                | **Test Accuracy** |
|--------------------------|--------------------|
| Logistic Regression (L1) | 0.862             |
| Logistic Regression (L2) | 0.858             |
| Random Forest            | 0.864             |
| KNN                      | 0.857             |
| **XGBoost**              | **0.869**         |

---

### Feature Importance:
Global feature importance was analyzed using SHAP values, weight importance, and permutation importance. Key features include:
1. `Humidity3pm`
2. `Pressure9am`
3. `WindGustSpeed`

Local feature importance (e.g., SHAP force plots) confirmed these findings and showed consistent results for individual predictions.

---

### Confusion Matrix:
Despite achieving high accuracy, the model has a relatively high false negative rate. Future work could explore alternative evaluation metrics, such as the **Fβ score**, to balance precision and recall.

