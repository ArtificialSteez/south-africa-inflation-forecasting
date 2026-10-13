# South African Inflation Forecasting for 2026

**Comparing classical time-series models and machine learning to forecast South Africa's headline Consumer Price Index (CPI).**

## Overview

This project forecasts monthly South African headline CPI for **January–December 2026**, using historical data available through **December 2025**. It compares whether nonlinear machine-learning models improve on a seasonal statistical benchmark, with model selection based on historical forecasting performance rather than in-sample fit.

The 2026 figures are **forecasts made from a December 2025 information set**, not updated actual CPI readings.

## Methods

1. Prepare the official Statistics South Africa monthly headline CPI index and check gaps and consistency.
2. Explore CPI persistence, trends, seasonality and stationarity with ADF/KPSS and ACF/PACF analysis.
3. Compare **ARIMA/SARIMA**, **RBF Support Vector Regression (SVR)** and **Random Forest Regression**, alongside a naïve benchmark.
4. Tune model settings using historical data, including Optuna-based optimisation for SVR.
5. Evaluate **one-month-ahead** and **1–12-month-ahead** forecasts with expanding-window backtesting.
6. Select a final model and export monthly CPI forecasts, year-on-year inflation and prediction intervals.

## Main findings

- **SARIMA(1,1,2)(1,0,1)₁₂** was selected for the final 2026 forecast.
- Pooled multi-horizon MAE was **0.9316 CPI index points** for SARIMA, versus **1.2477** for Random Forest and **1.7483** for SVR.
- The central forecast put December 2026 CPI at **107.719**, corresponding to approximately **3.98%** year-on-year inflation.
- Uncertainty widened at longer forecast horizons, so the forecast is a baseline rather than a guaranteed outcome.

## Repository contents

- `Question2_Notebook.ipynb` — modelling, tuning, backtesting and forecasts.
- `Question2_Report.docx` — analytical report.
- `Question2_2026_Inflation_Forecast.xlsx` — monthly forecast and model-comparison workbook.

## Running the project

**Note:** the source Stats SA CPI workbook is **not part of the uploaded project files**.

1. Obtain the CPI workbook used by the original analysis (the historical CPI index file labelled `202605`), subject to its terms of use.
2. Install the main dependencies:
   ```bash
   pip install numpy pandas matplotlib scipy scikit-learn statsmodels optuna openpyxl jupyter
   ```
3. Open `Question2_Notebook.ipynb` and **edit `DATA_DIR`**, which currently points to a local Mac folder. Confirm that `CPI_FILENAME` matches your downloaded source file.
4. Run the notebook in order to reproduce the backtests and exports.

## Limitations

CPI-only forecasting does not explicitly model future exchange-rate changes, fuel prices, food supply, interest-rate shocks or new policy developments. Prediction intervals quantify uncertainty under the fitted model, not every possible economic shock.

## Contributors

**Lwazi Nhlapo** and **Fumane Malangabe** — collaborative academic project.
