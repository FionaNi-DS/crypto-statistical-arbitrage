# Independent Model Validation Report

## Weekly Long-Only Cryptocurrency Momentum Model

### Validation Status

**Decision: Not recommended for standalone production use**

---

## 1. Executive Summary

This report presents an independent validation of a weekly long-only cryptocurrency momentum model.

The model ranks ten cryptocurrencies using their previous seven-day returns, selects the top three assets, assigns equal weights and rebalances weekly. A transaction cost of 20 basis points per unit of turnover is applied.

The model generated positive net returns during the 2023–2024 development period. However, it failed to maintain profitability during the untouched 2025 out-of-sample validation period.

The validation identified the following material weaknesses:

- negative out-of-sample gross and net returns;
- benchmark underperformance;
- statistically insignificant alpha;
- high broad-market beta;
- severe Maximum Drawdown;
- concentration risk;
- material market-regime dependence.

The model is therefore not considered sufficiently robust for standalone production investment use.

---

## 2. Model Purpose and Scope

The model is intended to identify medium-horizon cross-sectional momentum across a liquid cryptocurrency universe.

The model specification is:

- Universe: ten USDT-denominated cryptocurrency pairs;
- Signal: previous 168-hour return;
- Selection: three highest-ranked assets;
- Direction: long-only;
- Weighting: equal weighted;
- Rebalancing: every Monday at 00:00 UTC;
- Transaction cost: 20 basis points per unit of turnover.

The validation covered model implementation, performance stability, benchmark-relative value, market exposure, cost sensitivity and robustness.

---

## 3. Data Assessment

The analysis used hourly Binance Spot OHLCV data from 1 January 2023 to 31 December 2025.

Data-quality procedures included:

- chronological sorting;
- duplicate removal;
- missing-value assessment;
- timestamp alignment;
- asset-level return calculation;
- future-return alignment;
- cross-sectional rank checks.

The processed panel contained approximately 263,000 asset-hour observations.

### Data Limitations

- The universe included only ten cryptocurrencies.
- The current-asset selection may introduce survivorship bias.
- The sample covered only three years.
- Exchange-specific operational and data risks were not modelled.

---

## 4. Implementation Verification

Independent implementation checks confirmed that:

- the signal used only previously available information;
- the strategy selected the top three momentum-ranked assets;
- selected assets received equal one-third weights;
- the portfolio remained fully invested and long-only;
- rebalancing occurred weekly;
- turnover was calculated from absolute changes in portfolio weights;
- transaction costs were applied as turnover multiplied by the assumed cost rate;
- no material implementation inconsistency was identified.

**Implementation assessment: Passed**

---

## 5. Performance Validation

### Development and Validation Comparison

| Metric | Development 2023–2024 | Validation 2025 |
|---|---:|---:|
| Average hourly net return | 0.000110 | -0.000036 |
| Hourly net volatility | 0.007648 | 0.007652 |
| Annualized net Sharpe Ratio | 1.3506 | -0.4439 |
| Maximum Drawdown | -57.33% | -55.81% |
| Final portfolio value | 4.1448 | 0.5626 |
| Average turnover | 0.007885 | 0.008409 |

The model's positive development-period performance did not persist in the out-of-sample period.

The deterioration was not attributable to a major increase in volatility or turnover, both of which remained broadly stable.

**Performance-stability assessment: Failed**

---

## 6. Benchmark Analysis

The model was compared with an equal-weight portfolio of the same ten cryptocurrencies.

During 2025, the model underperformed the benchmark in:

- average net return;
- Sharpe Ratio;
- Maximum Drawdown;
- final portfolio value;
- turnover.

The momentum-selection component did not demonstrate incremental value relative to the simpler diversified benchmark.

**Benchmark-relative assessment: Failed**

---

## 7. Alpha and Beta Attribution

The strategy's net returns were regressed on equal-weight benchmark returns.

Hourly regression results:

- Beta: approximately 0.94;
- R-squared: approximately 87.5%;
- Alpha: statistically insignificant;
- Alpha p-value: approximately 0.65.

Daily-return robustness results were consistent:

- Beta: approximately 0.92;
- R-squared: approximately 85.7%;
- Alpha remained statistically insignificant.

The model therefore exhibited substantial broad-market exposure without evidence of persistent independent alpha.

**Alpha assessment: Failed**

---

## 8. Sensitivity and Robustness Testing

### Transaction-Cost Sensitivity

The model was tested under transaction costs of:

- 0 basis points;
- 5 basis points;
- 10 basis points;
- 20 basis points;
- 30 basis points.

The strategy remained unprofitable under every scenario, including the zero-cost case.

This confirms that the validation failure was not primarily caused by the selected transaction-cost assumption.

### Return-Frequency Robustness

The alpha-beta regression was repeated using compounded daily returns.

The results remained materially unchanged, supporting the robustness of the market-dependency finding.

---

## 9. Validation Findings

### Finding 1: Out-of-Sample Performance Failure

**Severity: High**

The model produced negative gross and net returns during 2025 and failed to reproduce its development-period performance.

### Finding 2: No Benchmark-Relative Value

**Severity: High**

The model underperformed the equal-weight benchmark across principal performance and risk metrics.

### Finding 3: No Statistically Significant Alpha

**Severity: High**

Neither hourly nor daily regression identified statistically significant benchmark-relative alpha.

### Finding 4: High Market Dependence

**Severity: Medium to High**

The model exhibited beta close to one, while approximately 86%–88% of return variation was explained by broad cryptocurrency market exposure.

### Finding 5: Severe Drawdown and Concentration Risk

**Severity: High**

Maximum Drawdown remained approximately 56%–57%, while the portfolio held only three assets.

### Finding 6: Market-Regime Dependence

**Severity: High**

Performance differed materially between the development and validation samples despite broadly similar volatility and turnover.

---

## 10. Model Limitations

- Limited asset universe;
- possible survivorship bias;
- short historical sample;
- single one-year validation period;
- fixed execution-cost assumption;
- no dynamic liquidity or market-impact model;
- no volatility targeting;
- no explicit drawdown control;
- concentrated three-asset portfolio;
- simplified equal-weight benchmark;
- substantial broad-market beta;
- limited coverage of independent market cycles.

---

## 11. Validation Decision

The model implementation was consistent with the documented design.

However, the model failed performance-stability, benchmark-relative and alpha validation tests.

The model is therefore:

- not recommended for standalone production investment use;
- not suitable for deployment using material capital in its current form;
- appropriate only as a research or exploratory model pending redevelopment.

---

## 12. Recommendations

1. Extend the historical sample across additional cryptocurrency cycles.
2. Use multiple rolling or expanding out-of-sample validation windows.
3. Expand the asset universe using transparent historical eligibility rules.
4. Reduce concentration through broader diversification or exposure limits.
5. Introduce volatility targeting and drawdown controls.
6. Improve transaction-cost modelling using spread, liquidity and order-size information.
7. Evaluate regime-dependent performance using predefined market-state variables.
8. Use additional challenger benchmarks.
9. Monitor rolling Sharpe Ratio, beta, drawdown and benchmark-relative performance.
10. Require independent revalidation before any production deployment.

---

## 13. Final Validation Opinion

**Implemented as intended, but not sufficiently robust for standalone production use.**
