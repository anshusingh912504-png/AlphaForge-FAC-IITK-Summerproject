# Task 2 — Bitcoin Alpha Generation (BTC Alpha Forge)

**Finance & Analytics Club, IIT Kanpur — AlphaForge**

## Overview

This notebook builds an end-to-end ML pipeline to generate **alpha signals on Bitcoin** using on-chain metrics and macroeconomic features.

**Dataset:** `btc_alpha_master_2014_2026.csv`  
**Period:** 17 Sep 2014 → 18 Jun 2026 (4,292 daily observations)

## Notebook

[`BTC_Alpha_Forge.ipynb`](notebooks/BTC_Alpha_Forge.ipynb)

## Pipeline Steps

1. **EDA** — Exploratory analysis of the Rhode feature set (on-chain + macro)
2. **Data Preparation** — Missing value treatment, normalisation, leak-free chronological train/test split
3. **ML Modelling** — Daily return prediction with Ridge, Random Forest, XGBoost, LightGBM
4. **Walk-Forward Validation** — Time-series cross-validation to prevent look-ahead bias
5. **Signal Generation** — Long / Short / Neutral signals from model predictions
6. **Backtesting** — Strategy performance vs. Buy-and-Hold benchmark

## Key Metrics Reported
- Cumulative Return
- Sharpe Ratio
- Maximum Drawdown
- Win Rate
- Information Coefficient (IC)

## ⚠️ Data File

Place `btc_alpha_master_2014_2026.csv` in the **same directory as the notebook** before running:

```
task2-btc-alpha-forge/notebooks/btc_alpha_master_2014_2026.csv
```

The dataset is not included in this repo due to file size constraints.
