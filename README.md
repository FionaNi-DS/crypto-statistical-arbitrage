# Cryptocurrency Statistical Arbitrage

## Overview

This project investigates cross-sectional momentum and reversal effects in liquid cryptocurrency markets using hourly Binance Spot OHLCV data.

The main objective is to test whether past returns predict future returns across different formation horizons, and whether abnormal trading volume strengthens momentum or mean-reversion signals.

## Research Questions

1. Do liquid cryptocurrencies exhibit short-term momentum or reversal?
2. Which formation horizons produce the strongest predictive signals?
3. Does abnormal trading volume strengthen momentum or reversal effects?
4. Do the strategies remain profitable after transaction costs?
5. Are the results stable out of sample?

## Data

- **Source:** Binance Spot Market
- **Frequency:** 1-hour bars
- **Period:** 2023-01-01 to 2025-12-31
- **Time zone:** UTC
- **Quote currency:** USDT
- **Universe:** 10 liquid cryptocurrency pairs

### Cryptocurrency Universe

- BTCUSDT
- ETHUSDT
- BNBUSDT
- XRPUSDT
- ADAUSDT
- DOGEUSDT
- SOLUSDT
- LTCUSDT
- LINKUSDT
- AVAXUSDT

The dataset contains Open, High, Low, Close and Volume information for each hourly observation.

## Methodology

The project will test cross-sectional momentum and reversal signals over multiple formation horizons:

- 1 hour
- 3 hours
- 6 hours
- 12 hours
- 24 hours
- 72 hours
- 168 hours

At each rebalancing time, cryptocurrencies will be ranked according to their past returns.

The baseline portfolio will:

- Go long the top three cryptocurrencies
- Go short the bottom three cryptocurrencies
- Use equal weights
- Rebalance hourly
- Apply turnover-based transaction costs

The project will also investigate whether abnormal trading volume strengthens momentum or reversal signals.

## Performance Evaluation

The strategies will be evaluated using:

- Annualised Return
- Annualised Volatility
- Sharpe Ratio
- Maximum Drawdown
- Alpha and Beta
- Turnover
- Hit Rate

## Validation Design

The sample will be divided chronologically:

- **In-sample research:** 2023-01-01 to 2024-06-30
- **Validation period:** 2024-07-01 to 2024-12-31
- **Out-of-sample test:** 2025-01-01 to 2025-12-31

This time-based split is designed to reduce look-ahead bias and evaluate the strategy on unseen data.

## Repository Structure

```text
crypto-statistical-arbitrage/
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
├── src/
├── results/
│   ├── figures/
│   └── tables/
├── tests/
├── README.md
├── requirements.txt
└── .gitignore
