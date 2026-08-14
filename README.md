# 📈 End-to-End Market Volatility Forecasting & Systematic Trading Pipeline
**Author:** SUMIT SONI  
**Asset Focus:** S&P 500 ETF (SPY Proxy)

---

## 🚀 Live Interactive Environment

This system features an automated cloud data streaming architecture. You can execute the live interactive models with a single click:

👉 **[Open Live Notebook in Google Colab](https://colab.research.google.com/drive/1r_woxh6TKoTs0ZIuK5bKrAzEK32Zgsrr#)**

---

## 📌 Executive Summary

Financial risk regimes are inherently non-linear and chaotic, causing classical linear frameworks (ARIMA) to struggle out-of-sample. 

By engineering multi-period rolling risk windows (`hist_vol_10d`, `hist_vol_21d`) paired with historical return shocks, we train an optimized **XGBoost Regressor** that achieves an out-of-sample $R^2$ score of **0.5527**, vastly outperforming the statistical baseline. Routing these predictions into a systematic volatility-targeting backtest yields an annualized Sharpe Ratio of **1.79** (a **163% improvement** over buy-and-hold).

---

## 📊 Core Performance Metrics & Results

| Model / Strategy | Out-of-Sample $R^2$ | Sharpe Ratio | Capital Exposure | Risk-Adjusted Alpha |
| :--- | :--- | :--- | :--- | :--- |
| **Buy & Hold Benchmark (SPY)** | N/A | **0.68** | 100% (Always Exposed) | Baseline |
| **ARIMA Baseline** | ~0.0000 | N/A | N/A | Minimal |
| **XGBoost Volatility Strategy** | **0.5527** | **1.79** | **Dynamic (0% in Panics)** | **+163% Sharpe Boost** |

> **Key Takeaway:** By predicting extreme risk regimes ahead of time, the ML-driven trading overlay successfully shifted capital to cash ahead of severe market collapses (Q4 2018 correction and COVID-19 crash), preserving capital and smoothing out the equity curve.

---

## 🧠 Project Architecture & Methodology

### 1. Data Pipeline & Feature Engineering
* **Data Sourcing:** Historical daily pricing for SPY ETF streamed dynamically via cloud URLs.
* **Target Variable:** Realized Volatility calculated via rolling standard deviation of daily logarithmic returns.
* **Feature Extraction:** Multi-period rolling risk windows (`hist_vol_10d`, `hist_vol_21d`), daily log returns, and autocorrelation diagnostics (ACF/PACF).

### 2. Predictive Modeling & Benchmarking
* **Baseline Statistical Model (ARIMA):** Evaluates linear dependencies and long-term historical mean reversion.
* **Machine Learning Regressor (XGBoost):** Captures non-linear interaction terms and sudden structural regime shocks.

### 3. Systematic Trading Overlay
* **Low Volatility Regime:** 100% capital allocation to the index to capture compounding market returns.
* **High Volatility Regime:** Outputs defensive signal (0% exposure), shifting capital dynamically to cash to prevent severe drawdowns during market panics.

---

## 🛠️ Key Technical Challenges & Solutions

* **Preventing Data Leakage (Look-Ahead Bias):** Standard cross-validation causes future data to leak into past predictions in time-series models. 
  * *Solution:* Enforced strict sequential time-based splitting without shuffling and engineered lagged rolling features strictly grounded in past observations.
* **Overcoming Linear Model Limitations:** Classical ARIMA models failed to adapt during high-variance regime shifts, yielding an $R^2 \approx 0.0000$.
  * *Solution:* Switched to non-linear gradient boosted decision trees (`XGBoost`), capturing complex interaction terms between short-term price shocks and medium-term risk windows to achieve an out-of-sample $R^2$ of **0.5527**.
* **Cloud Architecture & Portability:** Local file dependencies break live interactive notebooks in cloud environments.
  * *Solution:* Structured a dynamic cloud data streaming pipeline fetching data via web endpoints for seamless 1-click execution in Google Colab.

---

## ⚙️ Technologies Used

* **Languages:** Python
* **Machine Learning & Stats:** XGBoost, Statsmodels (ARIMA), Scikit-Learn
* **Data Engineering:** Pandas, NumPy
* **Cloud & Source Control:** Git, GitHub, Google Colab
