# Cryptocurrency Momentum and Reversal Model Validation

## Project Overview

This project develops and independently validates cross-sectional momentum and reversal strategies across ten liquid cryptocurrency pairs using hourly Binance Spot OHLCV data from 2023 to 2025.

> **Final result:** The weekly momentum model performed strongly during 2023–2024 development but failed during the untouched 2025 validation period. It underperformed the equal-weight benchmark, produced no statistically significant alpha and remained highly exposed to broad cryptocurrency market movements.

The project was designed as an end-to-end quantitative research and model-validation work. It covers:

- data collection and quality checks;
- exploratory analysis;
- momentum and reversal signal research;
- portfolio construction and backtesting;
- turnover-based transaction-cost modelling;
- benchmark comparison;
- out-of-sample validation;
- alpha and beta attribution;
- sensitivity and robustness analysis;
- formal validation findings and recommendations.

The final model investigated was a weekly long-only momentum strategy. It ranked cryptocurrencies by their previous seven-day returns, selected the three highest-ranked assets, assigned equal weights and rebalanced every Monday at 00:00 UTC.

---



## Research Questions

1. Do liquid cryptocurrencies exhibit short-horizon momentum or reversal?
2. Which signal horizons provide the strongest cross-sectional predictive information?
3. Do statistically positive signals remain economically viable after transaction costs?
4. Can lower-frequency portfolio construction reduce turnover sufficiently?
5. Does the selected model outperform a simple equal-weight cryptocurrency benchmark?
6. Is model performance stable in an untouched out-of-sample period?
7. Does the model generate statistically significant alpha after controlling for broad market exposure?

---

## Data

- **Source:** Binance Spot Market
- **Frequency:** Hourly OHLCV bars
- **Period:** 1 January 2023 to 31 December 2025
- **Time zone:** UTC
- **Quote currency:** USDT
- **Universe:** Ten liquid cryptocurrency pairs
- **Total observations:** Approximately 263,000 asset-hour records

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

---

## Validation Design

The sample was divided chronologically:

- **Model development period:** 1 January 2023 to 31 December 2024
- **Out-of-sample validation period:** 1 January 2025 to 31 December 2025

All final model specifications were frozen before the 2025 validation period was evaluated.

The frozen model specification was:

- **Signal:** Previous 168-hour return
- **Portfolio:** Top three momentum-ranked cryptocurrencies
- **Direction:** Long-only
- **Weighting:** Equal weighted
- **Rebalancing:** Weekly, Monday at 00:00 UTC
- **Transaction cost:** 20 basis points per unit of turnover

---

## Research and Model-Development Findings

### Short-Horizon Reversal

Cross-sectional information coefficients were negative across all tested formation horizons, indicating short-term reversal.

The strongest reversal effect appeared at the shortest horizons. However, hourly portfolio turnover was extremely high and the positive gross returns were eliminated by the assumed 20-basis-point transaction cost.

This demonstrated that statistical predictability did not translate into economic profitability.

### Weekly Long-Only Momentum

A weekly long-only momentum strategy substantially reduced turnover and generated positive development-period net performance.

Development-period results included:

- **Average hourly net return:** approximately 0.0110%
- **Annualized net Sharpe Ratio:** approximately 1.35
- **Maximum Drawdown:** approximately -57.3%
- **Final portfolio value:** approximately 4.14
- **Average turnover:** approximately 0.0079
- **Rebalances:** approximately 52 per year

However, the strategy underperformed the equal-weight cryptocurrency benchmark during the development period.

---

## Out-of-Sample Validation Results

The frozen weekly momentum model failed to maintain its development-period performance during 2025.

| Metric | Development 2023–2024 | Validation 2025 |
|---|---:|---:|
| Average hourly net return | 0.000110 | -0.000036 |
| Hourly net volatility | 0.007648 | 0.007652 |
| Annualized net Sharpe Ratio | 1.3506 | -0.4439 |
| Maximum Drawdown | -57.33% | -55.81% |
| Final portfolio value | 4.1448 | 0.5626 |
| Average turnover | 0.007885 | 0.008409 |
| Rebalances per year | approximately 52 | 52 |

The similar volatility and turnover levels across the two periods indicate that performance deterioration was not caused by a material implementation change.

---

## Benchmark Comparison

During 2025, both the weekly momentum strategy and the equal-weight cryptocurrency benchmark produced negative returns.

However, the momentum model performed worse across the principal metrics:

| Metric | Weekly Momentum | Equal-Weight Benchmark |
|---|---:|---:|
| Average hourly net return | -0.000036 | -0.000024 |
| Annualized net Sharpe Ratio | -0.4439 | -0.2991 |
| Maximum Drawdown | -55.81% | -52.31% |
| Final portfolio value | 0.5626 | 0.6256 |

The top-three momentum selection rule therefore did not add value relative to the simpler diversified benchmark.

---

## Alpha and Beta Attribution

An OLS regression with HAC-robust standard errors was used to regress strategy returns on equal-weight benchmark returns.

Hourly results:

- **Alpha:** slightly negative and statistically insignificant
- **Alpha p-value:** approximately 0.65
- **Beta:** approximately 0.94
- **R-squared:** approximately 87.5%

Daily-return robustness results:

- **Daily alpha:** statistically insignificant
- **Daily beta:** approximately 0.92
- **R-squared:** approximately 85.7%

The results indicate that most strategy-return variation was explained by broad cryptocurrency market exposure rather than persistent momentum-selection alpha.

---

## Sensitivity and Robustness Analysis

### Transaction-Cost Sensitivity

The strategy was evaluated under transaction-cost assumptions ranging from 0 to 30 basis points.

The strategy remained unprofitable even under the zero-cost scenario. Higher transaction costs increased the losses, but execution costs were not the principal cause of model failure.

### Return-Frequency Robustness

The alpha-beta regression was repeated using compounded daily returns instead of hourly returns.

The main conclusions remained unchanged:

- beta remained close to one;
- alpha remained statistically insignificant;
- a large proportion of strategy returns remained explained by the benchmark.

---

## Final Validation Decision

The model implementation was consistent with the documented specification.

However, the model did not demonstrate:

- stable out-of-sample profitability;
- benchmark-relative outperformance;
- statistically significant alpha;
- acceptable downside protection.

The model is therefore **not recommended for standalone production investment use in its current form**.

It should remain classified as a research model pending further redevelopment, broader historical testing, improved diversification, stronger risk controls and additional independent validation.

---

## Key Model Limitations

- The universe contained only ten cryptocurrencies.
- The asset selection may contain survivorship bias.
- The full sample covered only three years.
- The out-of-sample period covered only one year.
- Transaction costs were represented using a fixed basis-point assumption.
- Dynamic bid-ask spreads, market impact and order-size constraints were not modelled.
- The portfolio was concentrated in only three assets.
- The strategy retained substantial broad-market beta.
- The equal-weight benchmark used a simplified implementation.
- Performance appeared dependent on cryptocurrency market regime.

---


## Main Conclusion

The project demonstrates that:

- statistically detectable signals may be economically unviable after realistic transaction costs;
- positive absolute returns do not necessarily represent independent alpha;
- benchmark comparison is essential for evaluating long-only investment models;
- strong development-period performance may fail to persist out of sample;
- high Sharpe Ratio in development does not guarantee model stability;
- independent validation can identify material performance, concentration and market-dependency risks;
- a model may be implemented correctly but still be unsuitable for production use.


## Technical Skills Demonstrated

- Python, pandas and NumPy
- Time-series and cross-sectional analysis
- Cryptocurrency OHLCV data processing
- Momentum, reversal and information-coefficient research
- Portfolio construction and rebalancing
- Turnover and transaction-cost modelling
- Sharpe Ratio and Maximum Drawdown analysis
- Out-of-sample model validation
- Benchmark and challenger analysis
- OLS regression and HAC-robust inference
- Sensitivity and robustness analysis
- Model-risk findings and validation reporting

## Repository Structure

```text
crypto-statistical-arbitrage/
├── data/
│   ├── raw/
│   └── processed/
├── results/
│   ├── model_development/
│   └── signal_research/
├── 01_data_collection.ipynb
├── 02_data_cleaning.ipynb
├── 03_exploratory_analysis.ipynb
├── 04_signal_research.ipynb
├── 05_Model_development_and_exploratory_backtesting.ipynb
├── 06_validation.ipynb
├── validation_report.md
├── README.md
├── LICENSE
└── .gitignore
