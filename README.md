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
