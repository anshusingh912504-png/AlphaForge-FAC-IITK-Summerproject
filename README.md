# 🔬 AlphaForge — Finance & Analytics Club, IIT Kanpur
## Summer Project 2025

This repository contains my work for the **AlphaForge Summer Project** under the **Finance & Analytics Club (FAC), IIT Kanpur**. The project covers quantitative finance topics spanning Indian equity analysis, Bitcoin alpha generation via ML, and factor-based long-short portfolio construction on the Nasdaq-100.

---

## 📁 Repository Structure

```
AlphaForge-FAC-Summerproject/
│
├── task1-indian-equity-analysis/       # Indian stock universe — data, technical & risk analysis
│   ├── notebooks/
│   │   ├── TASK1_1_Data_Collection_Cleaning.ipynb
│   │   ├── TASK1_2_Technical_Analysis.ipynb
│   │   └── TASK1_3_Risk_Analytics.ipynb
│   ├── reports/                        # PDF exports of each notebook
│   └── charts/                         # All output visualisations
│
├── task2-btc-alpha-forge/              # Bitcoin alpha generation via On-Chain & Macro ML
│   └── notebooks/
│       └── BTC_Alpha_Forge.ipynb
│
├── task3-factor-ml-portfolio/          # Factor-based ML Long-Short Portfolio — Nasdaq-100
│   ├── notebooks/
│   │   └── Factor_ML_Portfolio_Notebook.ipynb
│   ├── data/
│   │   └── nasdaq100_metrics_ratios.csv
│   ├── outputs/                        # Model artifacts, CSV results, SHAP values
│   │   └── charts/                     # Portfolio performance charts
│   └── reports/
│       └── Factor_ML_Portfolio_Report.pdf
│
├── quantdash-webapp/                   # Group Task — Django quant trading dashboard
│   ├── manage.py
│   ├── requirements.txt
│   ├── quantdash/                      # Django project config
│   ├── marketdata/                     # Live data scraper (yfinance + SQLite cache)
│   ├── signals/                        # Indicator framework (SMA, RSI, MACD…)
│   ├── backtest/                       # Vectorized long/short backtesting engine
│   ├── mlstrategies/                   # ML strategy framework + HMM regime detection
│   └── dashboard/                      # Web frontend (views + HTML template)
│
└── .gitignore
```

---

## 📌 Task Summaries

### Task 1 — Indian Equity Analysis

**Universe:** 12 NSE-listed stocks across Banking, IT, Energy, and Auto sectors  
**Data Source:** `yfinance` (2020–2024)

| Sub-task | Description |
|----------|-------------|
| **1.1 — Data Collection & Cleaning** | Download OHLCV data, handle missing values, compute returns |
| **1.2 — Technical Analysis** | SMA, EMA, RSI, MACD, Bollinger Bands; backtesting strategy signals |
| **1.3 — Risk Analytics** | Beta, sector correlation heatmaps, VaR, stress-event analysis (Russia-Ukraine War, Adani Crisis, RBI Rate Hike), SCL regression |

> **Key outputs:** `portfolio_technical_dashboard.png`, `stock_correlation_heatmap.png`, `risk_return_quadrant_map.png`, `beta_bar_chart.png`, stress-event charts, and per-stock backtests.

---

### Task 2 — Bitcoin Alpha Generation (BTC Alpha Forge)

**Dataset:** `btc_alpha_master_2014_2026.csv` — 4,292 daily observations (Sep 2014 → Jun 2026)  
**Approach:** On-chain metrics + macro features → ML models for daily return prediction

| Step | Description |
|------|-------------|
| 1 | EDA on the Rhode feature set |
| 2 | Data preparation — missing values, normalisation, chronological split |
| 3 | ML models — predicting daily BTC returns |
| 4 | Walk-forward cross-validation |
| 5 | Long/Short signal generation |
| 6 | Strategy backtesting & performance evaluation |

> **Models used:** Ridge Regression, Random Forest, XGBoost, LightGBM  
> **Key metrics:** Sharpe Ratio, Maximum Drawdown, Cumulative Returns vs. Buy-and-Hold

---

### Task 3 — Factor-Based ML Long-Short Portfolio (Nasdaq-100)

**Universe:** Nasdaq-100  |  **Period:** 2017–2022  
**Approach:** Fundamental factor scoring → ML rank prediction → Monthly rebalancing

| Step | Description |
|------|-------------|
| 1 | Yearly fundamental factor rankings (Valuation, Profitability, Growth, Leverage/Quality) |
| 2 | Daily OHLCV simulation |
| 3 | Monthly feature panel — momentum + lagged fundamentals + next-month-return target |
| 4 | ML models — Linear/Ridge, Random Forest, XGBoost, LightGBM |
| 5 | Walk-forward validation & SHAP feature importance |
| 6 | Long-Short portfolio construction & monthly rebalancing |
| 7 | Backtest — returns, drawdown, Sharpe Ratio |
| 8 | Fama-French 3-Factor (FF3) alpha analysis |

> **Key outputs:** `cumulative_returns.png`, `shap_importance.png`, `ff3_betas.png`, `model_comparison_ic.png`, `backtest_summary.json`, `ff3_alpha_results.json`

---

### Group Task — QuantDash Web App

**Type:** Django Web Application  
**Module:** `quantdash-webapp/`

A live quantitative trading dashboard that wires the full pipeline — data scraping → indicator signals → backtesting → ML strategies — into a single web interface.

| Django App | Role |
|------------|------|
| `marketdata` | Pulls live OHLCV + fundamentals from `yfinance`; SQLite-cached after first fetch |
| `signals` | Plug-in indicator framework — SMA crossover, RSI, MACD; `combine_signals()` for composite scoring |
| `backtest` | Vectorized long/short backtester with transaction costs; reports CAGR, Sharpe, max drawdown, win rate |
| `mlstrategies` | ML strategy base class (`fit` + `predict → [-1,1]`) + HMM-based market regime detection |
| `dashboard` | Single JSON endpoint + HTML template — live ticker input, indicator weights, equity curve |

---

## 🛠️ Tech Stack

| Library | Purpose |
|---------|---------|
| `pandas`, `numpy` | Data manipulation |
| `yfinance` | Market data download |
| `matplotlib`, `seaborn` | Visualisation |
| `scikit-learn` | ML models (Ridge, Random Forest) |
| `xgboost`, `lightgbm` | Gradient boosting models |
| `shap` | Feature importance (SHAP values) |
| `scipy` | Statistical analysis |
| `Django >= 5.0` | Web framework (QuantDash app) |
| `hmmlearn` | Hidden Markov Models for regime detection |

---

## 🚀 Getting Started

```bash
# Clone the repo
git clone https://github.com/<your-username>/AlphaForge-FAC-Summerproject.git
cd AlphaForge-FAC-Summerproject

# Install dependencies
pip install pandas numpy matplotlib seaborn yfinance scikit-learn xgboost lightgbm shap scipy

# Open any notebook
jupyter notebook task1-indian-equity-analysis/notebooks/TASK1_1_Data_Collection_Cleaning.ipynb
```

> **Note:** The BTC notebook (`task2-btc-alpha-forge`) requires the dataset file `btc_alpha_master_2014_2026.csv` to be placed in the same directory as the notebook before running.

---

## 👤 Author

**Anshu Singh**  
Finance & Analytics Club — AlphaForge Summer Project 2025  
IIT Kanpur

---

## 📄 License

This project is submitted as part of the FAC AlphaForge Summer Project and is intended for educational and portfolio purposes.
