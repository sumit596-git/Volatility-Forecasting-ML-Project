# Volatility-Forecasting-Time Series-Project
# 📈 S&P 500 Volatility Forecasting & Systematic Trading Pipeline

An end-to-end quantitative finance pipeline that leverages classical time-series analysis (ARIMA) and machine learning (XGBoost) to forecast S&P 500 (SPY) volatility regimes and deploy a risk-managed systematic trading strategy.

---

## 🚀 Live Interactive Environment
This project is built with an automated cloud data streaming architecture. You can run the live, interactive models with a single click without any manual setup:

👉 **[Open Live Notebook in Google Colab](https://colab.research.google.com/drive/1r_woxh6TKoTs0ZIuK5bKrAzEK32Zgsrr#)**

---

## 🧠 Project Architecture & Methodology

This system treats market risk forecasting as a machine learning regression task, predicting next-day historical realized volatility based on engineered technical features.

### 1. Data Pipeline & Feature Engineering
* **Data Sourcing:** Historical daily pricing data for the S&P 500 tracking ETF (SPY).
* **Target Variable:** Mathematical extraction of **Realized Volatility** calculated using a rolling standard deviation of daily logarithmic returns.
* **Feature Extraction:** Standard technical and momentum indicators to give the models contextual market state awareness.

### 2. Predictive Modeling
We evaluated and benchmarked two distinct forecasting methodologies:
* **Baseline Statistical Model (ARIMA):** Captures linear dependencies and long-term historical trends.
* **Machine Learning Regressor (XGBoost):** Deployed to capture complex, non-linear market patterns and sudden structural volatility shocks (such as the 2020 liquidity crunch).

### 3. Systematic Trading Overlay
Rather than leaving the forecasts as numbers on a page, the pipeline feeds the predictions into an active risk-management rule:
* **Low Volatility Regime:** Capital is fully allocated to the index to capture compounding returns.
* **High Volatility Regime:** The system outputs a defensive signal (`0`), dynamically shifting capital to cash to avoid severe market drawdowns.

---

## 📊 Core Performance Metrics & Results

| Model / Strategy | Directional Accuracy | Maximum Drawdown | Sharpe Ratio |
| :--- | :--- | :--- | :--- |
| **Buy & Hold Benchmark** | N/A | High | Baseline |
| **XGBoost Risk Strategy** | Optimized | **Significantly Reduced** | **Outperformed** |

> **Key Takeaway:** By predicting extreme risk regimes ahead of time, the ML-driven trading strategy successfully sidestepped major market collapses, preserving capital and drastically smoothing out the equity curve compared to a traditional buy-and-hold approach.

---

## ⚙️ Technologies Used
* **Languages:** Python
* **Machine Learning & Stats:** XGBoost, Statsmodels (ARIMA), Scikit-Learn
* **Data Engineering:** Pandas, NumPy
* **Cloud & Source Control:** Git, GitHub Cloud Storage, Google Colab
