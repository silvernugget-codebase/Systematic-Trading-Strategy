# Systematic Trading Strategy: A Bet Against The Market

This project consists of a straightforward portfolio strategy for a stagflation regime, implemented and backtested in R.

## Methodology

Our asset-universe consists of 40 highly liquid US-listed ETFs (equities, bonds, commodities, real estate) with daily data from 2008 through April 2026 fetched from Yahoo Finance via `quantmod::getSymbols()`

**Optimization:** A simple mean-variance optimization via `PortfolioAnalytics`, ROI; long-only, 10% max-weight and group constraints: 20-40% in inflation-sensitive assets and at most 10% in tech.

**Backtest:** 84-month rolling window with quarterly rebalancing. 2008-2014 in-sample and 2015-2026 out-of-sample.

**Comparison:** Comparison against a simple buy-and-hold strategy in the S&P 500, a 1/N and an inverse-volatility portfolio. We looked at absolute return, Shapre ratio, value at risk, expected shortfall and drawdown periods.

## Results
Out of sample, the strategy underperformed all three benchmarks measured by risk-adjusted return. The structural bet on stagflation carries a lot of opportunity cost during a tech-driven bull market. The paper also discusses its limitations. Slippage, transaction costs, bid-ask spreads etc.


## Files

- `STS.Rmd`: source code
- `STS.pdf`: rendered report

## Reproduce

```r
install.packages(
  c(
    "quantmod",
    "PortfolioAnalytics",
    "PerformanceAnalytics",
    "ROI",
    "ROI.plugin.glpk",
    "ROI.plugin.quadprog",
    "knitr",
    "kableExtra"
  )
)

rmarkdown::render("STT.Rmd")

```

