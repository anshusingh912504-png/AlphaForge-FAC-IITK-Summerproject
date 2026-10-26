# QuantDash Web App — AlphaForge Group Task

A Django-based quantitative trading dashboard that brings the entire alpha pipeline (data → indicators → signals → backtest) into a live web interface.

## Architecture

```
quantdash-webapp/
├── manage.py
├── requirements.txt
├── quantdash/             # Django project settings & URL root
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── asgi.py
├── marketdata/            # Market data scraper & caching layer
│   ├── models.py          # DB models for price & fundamental data
│   ├── services.py        # yfinance wrappers (fetch_price_history, refresh_fundamentals)
│   └── scrapper.py
├── signals/               # Technical indicator framework
│   ├── base.py            # BaseIndicator + IndicatorRegistry
│   └── indicators.py      # SMA crossover, RSI, MACD + combine_signals()
├── backtest/              # Vectorized backtesting engine
│   └── engine.py          # BaseBacktester → CAGR, Sharpe, drawdown, win rate
├── mlstrategies/          # ML strategy framework (mirrors indicator contract)
│   ├── base.py            # BaseMLStrategy: fit(df) + predict(df) → [-1, 1]
│   └── regime.py          # Market regime detection (HMM-based)
└── dashboard/             # Frontend glue
    ├── views.py           # run_backtest endpoint (live data → signal → backtest → JSON)
    ├── urls.py
    └── templates/dashboard/index.html
```

## What Each Module Does

| Module | Responsibility |
|--------|---------------|
| `marketdata` | Pulls live OHLCV + fundamentals from yfinance; caches in SQLite after first fetch |
| `signals` | Subclass `BaseIndicator`, implement `compute(df) → Series[-1,1]`; auto-registered via `@IndicatorRegistry.register` |
| `backtest` | Vectorized long/short backtester with transaction costs; subclass `BaseBacktester` for slippage, position sizing, stop-losses |
| `mlstrategies` | ML strategies plug into the same `BaseBacktester` via `fit(df)` + `predict(df)` |
| `dashboard` | Single JSON endpoint + HTML template — ticker input, indicator weights, equity curve, fundamentals panel |

## Quick Start

```bash
cd quantdash-webapp

# Install dependencies
pip install -r requirements.txt

# Run migrations (creates SQLite DB)
python manage.py migrate

# Optional: create admin user
python manage.py createsuperuser

# Start dev server
python manage.py runserver
```

Then open **http://127.0.0.1:8000** in your browser.

## Adding a New Indicator

```python
# signals/indicators.py
@IndicatorRegistry.register
class BollingerBandSignal(BaseIndicator):
    name = "bollinger"

    def __init__(self, window: int = 20, n_std: float = 2.0, **params):
        super().__init__(window=window, n_std=n_std, **params)
        self.window, self.n_std = window, n_std

    def compute(self, df):
        mid = df['close'].rolling(self.window).mean()
        std = df['close'].rolling(self.window).std()
        z = (df['close'] - mid) / (self.n_std * std)
        return -z.clip(-1, 1)  # price near upper band → bearish
```

No other file changes needed — it auto-appears in `IndicatorRegistry.all()`.

## Tech Stack

| Library | Purpose |
|---------|---------|
| `Django >= 5.0` | Web framework |
| `yfinance >= 0.2.40` | Live market data |
| `pandas >= 2.0` | Data manipulation |
| `numpy >= 1.26` | Numerical computation |
| `hmmlearn >= 0.3.0` | Hidden Markov Models for regime detection |
