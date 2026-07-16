# Machine Learning-Based Time Series Forecasting of German Electricity Demand

## Overview

This repository contains the implementation of a time series forecasting project completed for the **Advanced Research Topics in Data Science** module.

The objective of this project is to forecast **German electricity demand** using a range of forecasting techniques, including benchmark methods, statistical models, machine learning, and deep learning. The models are compared using forecasting accuracy metrics to determine the most suitable approach for electricity demand prediction.

---

# Assignment Objectives

The project follows the coursework requirements and includes:

- Data collection and preprocessing
- Exploratory Data Analysis (EDA)
- Stationarity testing
- Benchmark forecasting models
- SARIMA forecasting
- SARIMAX forecasting with temperature as an exogenous variable
- Feature-based Machine Learning using Gradient Boosting Regressor
- Deep Learning using Long Short-Term Memory (LSTM)
- Forecast evaluation and model comparison

---

# Dataset

## Electricity Demand

**Source**

Open Power System Data (OPSD)

https://data.open-power-system-data.org/time_series/

Dataset used:

- Country: Germany (DE)
- Time Resolution: Hourly
- Study Period: January 2015 – October 2020

The hourly dataset was converted into weekly observations for statistical and machine learning models, while the original hourly data were used for the LSTM model.

---

## Temperature Data

Temperature data were collected using the Open-Meteo Archive API.

Location used:

- Berlin, Germany

Temperature was incorporated as an **exogenous variable** in the SARIMAX model.

---

# Project Workflow

The complete workflow consists of the following stages:

```
Data Collection
        │
        ▼
Data Cleaning & Preprocessing
        │
        ▼
Exploratory Data Analysis
        │
        ▼
Stationarity Testing
(ADF, KPSS, ACF, PACF)
        │
        ▼
Benchmark Forecast Models
        │
        ▼
SARIMA
        │
        ▼
SARIMAX
        │
        ▼
Gradient Boosting
        │
        ▼
LSTM
        │
        ▼
Performance Evaluation
(RMSE & MAE)
```

---

# Models Implemented

## 1. Benchmark Models

The following baseline forecasting models were implemented:

- Mean Forecast
- Naïve Forecast
- Seasonal Naïve Forecast
- Drift Forecast

These models provide baseline performance for comparison with more advanced approaches.

---

## 2. SARIMA

A Seasonal AutoRegressive Integrated Moving Average (SARIMA) model was developed to capture both autoregressive and seasonal patterns.

Parameter search:

- p = 0–6
- d = 0–2
- q = 0–6

Seasonal Order:

```
(1,1,1,52)
```

The best model was selected using the **Akaike Information Criterion (AIC).**

---

## 3. SARIMAX

The SARIMA model was extended by including **temperature** as an exogenous variable.

Temperature features include:

- Mean Temperature
- Maximum Temperature
- Minimum Temperature
- Heating Degree Days
- Cooling Degree Days

This produces a **conditional forecast** because future observed temperatures are used during testing.

---

## 4. Gradient Boosting Regressor

A feature-based regression model was developed using:

- Lag features
- Temperature variables

The model learns nonlinear relationships between historical electricity demand and weather conditions.

---

## 5. Long Short-Term Memory (LSTM)

An LSTM neural network was implemented using the original hourly electricity demand data.

The workflow includes:

- Data normalization
- Sequence generation
- Chronological train-test split
- Early stopping
- Forecasting of the final two years

---

# Evaluation Metrics

The forecasting models were evaluated using:

- Root Mean Squared Error (RMSE)
- Mean Absolute Error (MAE)

Lower values indicate better forecasting performance.

---

# Model Performance

| Model | RMSE | MAE |
|--------|------:|------:|
| Mean Forecast | 762.12 | 646.91 |
| Naïve Forecast | 762.57 | 652.16 |
| Seasonal Naïve | 424.46 | 325.75 |
| Drift | 978.94 | 833.89 |
| SARIMA | 522.20 | 430.08 |
| SARIMAX | 478.50 | 364.60 |
| Gradient Boosting | 274.12 | 206.16 |
| LSTM | **122.57** | **94.66** |

The LSTM model achieved the best forecasting performance with the lowest prediction error.

---

# Repository Structure

```
Research/
│
├── Data/
│   ├── Electricity Dataset
│   └── Temperature Dataset
│
├── Notebook/
│   └── Research.ipynb
│
├── Figures/
│   ├── EDA
│   ├── SARIMA
│   ├── SARIMAX
│   ├── Gradient Boosting
│   └── LSTM
│
├── Report/
│   └── Assignment_Report.pdf
│
├── README.md
│
└── requirements.txt
```

---

# Key Results

The analysis showed that:

- Electricity demand exhibits strong yearly seasonality.
- Stationarity testing confirmed that SARIMA-based models are appropriate.
- Temperature improved forecasting accuracy when included in SARIMAX.
- Gradient Boosting captured nonlinear relationships better than statistical models.
- LSTM achieved the highest forecasting accuracy among all implemented models.

---

# Future Improvements

Possible future work includes:

- Holiday calendar features
- Renewable energy generation data
- Additional weather variables
- Hyperparameter optimisation
- Transformer-based forecasting models
- Ensemble forecasting methods

---

# Python Libraries

The project was developed using:

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Statsmodels
- TensorFlow / Keras
- SciPy

---

# How to Run the Project

1. Clone the repository

```bash
git clone https://github.com/DharanidharBeere/Researcch.git
```

2. Install the required Python libraries

```bash
pip install -r requirements.txt
```

3. Open the notebook in **Jupyter Notebook** or **Google Colab**.

4. Run all cells sequentially to reproduce the analysis, forecasting models, figures, and evaluation metrics.

---

# Author

**Student Name:** Dharanidhar Beere

**Student ID:** 24077147

**Module:** Advanced Research Topics in Data Science

**Module Code:** 7PAM2016

**University:** University of Hertfordshire

---

# Acknowledgements

- Open Power System Data (OPSD)
- Open-Meteo Archive API
- Statsmodels
- Scikit-learn
- TensorFlow/Keras
