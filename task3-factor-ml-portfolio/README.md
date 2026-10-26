# Task 5 — Factor-Based ML Long-Short Portfolio (Nasdaq-100)

## Overview

An end-to-end **quantitative equity strategy** on the Nasdaq-100 universe (2017–2022) combining:
- Multi-factor fundamental scoring
- ML rank-prediction models
- Monthly-rebalanced long-short portfolio
- Fama-French 3-Factor (FF3) alpha analysis

## Notebook

[`Factor_ML_Portfolio_Notebook.ipynb`](notebooks/Factor_ML_Portfolio_Notebook.ipynb)

## Pipeline

| Step | Description |
|------|-------------|
| 1 | **Fundamental Factor Rankings** — Valuation, Profitability, Growth, Quality/Leverage |
| 2 | **Price Data** — Daily OHLCV for Nasdaq-100 constituents |
| 3 | **Feature Panel** — Monthly momentum + lagged fundamentals → next-month return target |
| 4 | **ML Models** — Linear/Ridge, Random Forest, XGBoost, LightGBM |
| 5 | **Walk-Forward CV + SHAP** — Time-series validation + feature importance |
| 6 | **Portfolio Construction** — Top/Bottom quintile long-short, monthly rebalance |
| 7 | **Backtest** — Cumulative returns, drawdown, Sharpe, monthly bar chart |
| 8 | **FF3 Alpha** — Fama-French 3-Factor regression to isolate true alpha |

## Factors Used

| Category | Sub-metrics |
|----------|-------------|
| **Valuation** (lower = better) | P/E, P/B, EV/EBITDA |
| **Profitability** (higher = better) | ROE, Gross Profit/Assets, Earnings Yield (Greenblatt) |
| **Growth** | Revenue Growth, EPS Growth, Asset Growth |
| **Quality / Leverage** | Debt/Equity, Interest Coverage, Asset Turnover |

## Output Files

| File | Description |
|------|-------------|
| `outputs/backtest_summary.json` | Portfolio performance summary |
| `outputs/ff3_alpha_results.json` | Fama-French alpha & beta coefficients |
| `outputs/model_comparison.json` | IC scores across all models |
| `outputs/shap_feature_importance.csv` | SHAP values per feature |
| `outputs/ml_rebalance_rankings.csv` | Monthly ML-ranked stock scores |
| `outputs/portfolio_monthly_returns.csv` | Monthly strategy returns |
| `outputs/charts/cumulative_returns.png` | Cumulative return curve |
| `outputs/charts/shap_importance.png` | SHAP bar chart |
| `outputs/charts/ff3_betas.png` | FF3 factor exposures |
| `outputs/charts/model_comparison_ic.png` | IC comparison across models |
| `outputs/charts/drawdown.png` | Drawdown chart |
| `outputs/charts/monthly_returns_bar.png` | Monthly returns bar chart |
| `outputs/charts/alpha_comparison.png` | Strategy vs. benchmark alpha |

## Data

`data/nasdaq100_metrics_ratios.csv` — Fundamental annual ratios for Nasdaq-100 stocks (2017–2022)

## Report

[`reports/Factor_ML_Portfolio_Report.pdf`](reports/Factor_ML_Portfolio_Report.pdf)
