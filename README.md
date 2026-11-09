# CAPM Alpha Ranking Strategy

### Overview

This project implements and evaluates a quantitative equity strategy based on rolling Capital Asset Pricing Model (CAPM) alpha estimates.

The strategy ranks stocks by their estimated rolling alpha, selects the top 10%, and constructs an equally weighted long-only portfolio with daily rebalancing.

The objective is to investigate whether CAPM alpha rankings contain useful information for cross-sectional stock selection and to evaluate the strategy's historical performance, risk characteristics and implementation limitations.

### Methodology

The research follows the pipeline:

**Data → Rolling CAPM Estimation → Alpha Ranking → Portfolio Construction → Return Calculation → Performance Evaluation**

Key assumptions:

- Investment universe: A retrospectively selected group of US equities across multiple industries.
- Estimation window: 126 trading days.
- Selection rule: Long the top 10% by rolling CAPM alpha.
- Portfolio construction: Equal-weighted, long-only.
- Rebalancing: Daily, using lagged signals.
- Benchmark: S&P 500 Price Index.
- Backtest period: Approximately July 2015 – December 2024.

### Preliminary Results

| Metric | CAPM Strategy | S&P 500 |
|---|---:|---:|
| CAGR | 29.86% | 11.65% |
| Annualized Volatility | 24.71% | 18.08% |
| Annualized Sharpe Ratio | 1.11 | 0.60 |
| Maximum Drawdown | -35.96% | -33.92% |
| Average Daily One-sided Turnover | 9.13% | — |

*All results are preliminary, gross of transaction costs, and subject to the limitations described below.*

### Research Findings

The strategy exhibited higher historical returns and a higher Sharpe Ratio than the selected S&P 500 benchmark, alongside greater annualized volatility.

However, the relatively high portfolio turnover suggests that transaction costs may materially reduce net performance.

The observed outperformance cannot yet be attributed exclusively to stock-selection alpha.

### Limitations

The current implementation has several important limitations:

- The risk-free rate is estimated using the full historical sample, introducing look-ahead bias.
- The investment universe is retrospectively selected and may suffer from survivorship and selection biases.
- The benchmark uses a price-return convention, while stock returns are dividend-adjusted.
- The backtest excludes explicit transaction costs, slippage and market impact.
- Market beta and sector exposures are not explicitly neutralized.
- No genuinely untouched out-of-sample evaluation has yet been completed.

### Future Research

Potential extensions include:

- Correcting data and methodological biases.
- Incorporating transaction costs and testing alternative rebalancing frequencies.
- Investigating time-decayed alpha signals.
- Testing different selection thresholds and portfolio weighting schemes.
- Introducing liquidity filters.
- Evaluating industry-neutral signals and beta-neutral portfolio construction.
- Conducting out-of-sample and robustness tests.

### Technology

Python, Pandas, NumPy, Statsmodels, Matplotlib and yfinance.

### Disclaimer

This project is an educational quantitative research exercise. The results are hypothetical historical backtests and should not be interpreted as verified, implementable investment performance or investment advice.

## Cumulative Performance

![CAPM Alpha Strategy vs S&P 500](main/cumulative_returns.png)
