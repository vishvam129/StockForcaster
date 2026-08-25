# StockForcaster

Django web app that shows live stock charts and predicts future prices with a linear-regression model.

## Features

- **Dashboard** — 1-month Plotly chart for AAPL, AMZN, QCOM, META, NVDA, JPM plus today's prices for popular tickers
- **Ticker search** — look up any symbol from the bundled NASDAQ ticker list (`app/Data/Tickers.csv`)
- **Prediction** — `/predict/<TICKER>/<DAYS>/` downloads 3 months of hourly data via `yfinance`, trains a scikit-learn `LinearRegression`, and forecasts the next N days with a confidence score
- Friendly error pages for invalid tickers, bad day counts, and API outages

## Stack

Django · yfinance · Plotly · pandas · NumPy · scikit-learn · Bootstrap

## Run locally

```bash
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver      # http://127.0.0.1:8000
```

## Routes

| Path | Description |
|---|---|
| `/` | Dashboard |
| `/search/` | Ticker search page |
| `/ticker/` | Full ticker list |
| `/predict/<ticker>/<days>/` | Chart + N-day forecast |
