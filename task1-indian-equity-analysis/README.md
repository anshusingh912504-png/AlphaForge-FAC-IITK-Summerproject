# Task 1 — Indian Equity Analysis

Analysis of 12 NSE-listed stocks across **Banking, IT, Energy, and Auto** sectors using data sourced via `yfinance`.

## Notebooks

| Notebook | Description |
|----------|-------------|
| [`TASK1_1_Data_Collection_Cleaning.ipynb`](notebooks/TASK1_1_Data_Collection_Cleaning.ipynb) | Download OHLCV data, handle missing values, compute log/simple returns |
| [`TASK1_2_Technical_Analysis.ipynb`](notebooks/TASK1_2_Technical_Analysis.ipynb) | SMA, EMA, RSI, MACD, Bollinger Bands + backtested trading signals |
| [`TASK1_3_Risk_Analytics.ipynb`](notebooks/TASK1_3_Risk_Analytics.ipynb) | Beta estimation, sector correlations, VaR, stress-event analysis, SCL regression |

## Stock Universe

| Ticker | Sector |
|--------|--------|
| HDFCBANK.NS | Banking |
| ICICIBANK.NS | Banking |
| AXISBANK.NS | Banking |
| TCS.NS | IT |
| INFY.NS | IT |
| WIPRO.NS | IT |
| RELIANCE.NS | Energy |
| ONGC.NS | Energy |
| BPCL.NS | Energy |
| M&M.NS | Auto |
| MARUTI.NS | Auto |
| HEROMOTOCO.NS | Auto |

## Key Charts

| Chart | Description |
|-------|-------------|
| `portfolio_technical_dashboard.png` | Full technical indicator dashboard |
| `stock_correlation_heatmap.png` | Cross-stock correlation matrix |
| `sector_correlation_heatmap.png` | Sector-level correlation |
| `risk_return_quadrant_map.png` | Risk-Return scatter plot |
| `beta_bar_chart.png` | Beta values vs Nifty 50 |
| `stress_event_*.png` | Drawdowns during crisis events |
| `SCL_all_stocks.png` | Security Characteristic Line regression |
| `Cumulative_Portfolio_Growth.png` | Equal-weighted portfolio growth |

## Stress Events Analysed
- Russia-Ukraine War (Feb 2022)
- Adani Short-Seller Crisis (Jan 2023)
- RBI Rate Hike Cycle (2022–2023)
