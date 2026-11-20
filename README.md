# Equity Volatility Benchmarks

This COMP 576 project compares standard and patch-based Transformers with recurrent networks and simpler baselines for five-day stock volatility forecasting. The benchmark measures forecast accuracy and computational cost across low-, medium-, and high-volatility regimes.

## Data and target

The benchmark uses daily adjusted closing prices and volume from Yahoo Finance for ten U.S. equities from 2018 through 2024. The tickers are AAPL, MSFT, GOOGL, AMZN, TSLA, JPM, GS, BAC, XOM, and CVX.

Models forecast the annualized sample standard deviation of returns over the next five trading days. The primary input window is 20 trading days, with features derived from log returns, trailing five-day volatility, and log-transformed volume.

## Models

- Historical volatility persistence
- GARCH(1,1)
- Random Forest
- LSTM and GRU
- Standard Transformer and compact PatchTST-based Transformer

## Evaluation

The expanding-window evaluation holds out 2021, 2022, 2023, and 2024 in separate rounds. Each test year follows one validation year. Models are scored on the same eligible stock-date pairs, and samples whose target windows cross split boundaries are excluded. Scaling and per-stock regime thresholds are estimated from training data only.

Planned reporting includes RMSE and MAE on volatility, QLIKE on squared forecasts and targets, regime sample counts, variability across neural training seeds, training and inference times, and neural parameter counts.

## Team

- **Keanu Swart** develops and trains the two Transformer models and measures their efficiency.
- **Tolga Destici** handles data preparation, leakage checks, and the statistical baselines.
- **James Vescovo** leads the team and implements Random Forest and the recurrent models, including reproduction of selected baselines from the reference study.

## References

- [Pragadeeshwaran et al., stock-level volatility forecasting benchmark](https://doi.org/10.1371/journal.pone.0354643)
- [Nie et al., PatchTST](https://arxiv.org/abs/2211.14730)
- [yfinance, the data acquisition library](https://github.com/ranaroussi/yfinance)
