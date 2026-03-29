# Google Stock Return Forecasting — SARIMAX + ML Models

**Project completed:** March 2026  
**Tools:** Python · Statsmodels · Scikit-learn · Pandas · Matplotlib  
**Domain:** Time Series Forecasting · Financial Data · Machine Learning

---

## Overview

An end-to-end time series forecasting system built on 2 years of Google (GOOGL) stock data.  
The project compares statistical models (SARIMAX) against machine learning models (Random Forest, XGBoost)  
to forecast **daily stock returns** — not raw prices, which are inherently non-stationary.

**Key result:** Random Forest achieved **R² = 0.8489** on the test set,  
significantly outperforming the SARIMAX baseline.

---

## Problem Statement

Raw stock prices are non-stationary and highly autocorrelated — making direct price prediction  
misleading and statistically invalid. This project pivots to **return-based forecasting**,  
which is both more statistically sound and more practically useful for trading decisions.

---

## Methodology

### 1. Stationarity & Causality Testing
- Applied **ADF Test** to confirm non-stationarity of raw prices
- Transformed to log returns to achieve stationarity
- Used **Granger Causality Test** to identify valid lag-based exogenous features

### 2. Feature Engineering
- Lag features (returns at t-1, t-2, t-5)
- Rolling volatility (7-day, 14-day standard deviation)
- Momentum indicators
- Volume-price interaction features
- Technical indicators (moving averages, rate of change)

### 3. Models Compared

| Model | Test R² |
|---|---|
| SARIMAX (baseline) | ~0.00 (near random on raw prices) |
| SARIMAX on returns | Moderate |
| Random Forest | **0.8489** |
| XGBoost | Competitive |

### 4. Validation Strategy
- **TimeSeriesSplit cross-validation** (no data leakage)
- Walk-forward validation to simulate real forecasting conditions

---

## Key Findings

- **Feature engineering > model tuning** in financial time series
- Transforming prices to returns was the single biggest performance jump (R² from -10 to 0.84)
- Random Forest handled non-linearity and feature interactions better than SARIMAX
- Volatility and lag features were the most important predictors (confirmed via feature importance plot)

---

## Repository Structure

```
google-stock-forecasting/
├── google_stock_forecasting.ipynb       # Full analysis notebook
├── google_2year_data.xls                # GOOGL historical data (2 years)
├── google_stock_full_documentation.pdf  # Detailed project report
└── README.md
```

---

## How to Run

1. Clone the repository
```bash
git clone https://github.com/Dev-2004-DA/google-stock-forecasting.git
```

2. Install dependencies
```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels xgboost
```

3. Open the notebook
```bash
jupyter notebook google_stock_forecasting.ipynb
```

---

## Skills Demonstrated

`Time Series Analysis` `SARIMAX` `Random Forest` `XGBoost` `Feature Engineering`  
`Granger Causality` `ADF Test` `TimeSeriesSplit` `Python` `Scikit-learn` `Statsmodels`

---

*Part of my Data Analytics portfolio — [github.com/Dev-2004-DA](https://github.com/Dev-2004-DA)*
