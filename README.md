# GARCH Volatility Analysis

This project compares how volatility behaves across four major global equity indices — S&P 500 (^GSPC), EURO STOXX 50 (^STOXX50E), Nikkei 225 (^N225), and FTSE 100 (^FTSE) — using GARCH(1,1) models.

## Project Goal

The notebook demonstrates a full quantitative workflow:
- load financial data for multiple global indices,
- clean and prepare the return series,
- inspect price and return behavior,
- engineer rolling volatility features,
- fit a GARCH(1,1) model per index,
- evaluate residual diagnostics (Ljung-Box),
- compare volatility persistence and model fit across indices,
- and compare Normal vs Student-t error distributions.

## Data Source

The analysis uses Yahoo Finance data (2015-01-01 through 2026-06-21) for four tickers: ^GSPC, ^STOXX50E, ^N225, and ^FTSE.

## Notebook

- `garch_analysis.ipynb` contains the full analysis pipeline.

## Setup

1. Create and activate the environment.
2. Install requirements:
   ```bash
   pip install -r requirements.txt
   ```
3. Open the notebook and run cells in order.

## Methodology

- Daily log returns are computed from adjusted close prices for each index.
- A GARCH(1,1) model (Normal distribution) is fitted per index, then a Student-t variant is fit for comparison.
- Conditional volatility is compared against 20/60-day rolling volatility to check clustering.
- The Ljung-Box test is applied to standardized residuals to check for remaining autocorrelation.
- Volatility persistence (alpha + beta) and AIC/BIC are compared across indices and distribution choices.

## Key Findings

- All four indices show high volatility persistence (alpha + beta close to 1), consistent with slow-decaying volatility shocks.
- Student-t innovations outperform Normal innovations (lower AIC/BIC) for every index, reflecting fat tails in equity returns.

## Notes

This is intended as a portfolio-style quantitative analysis project and can be extended with:
- alternative GARCH specifications (EGARCH, GJR-GARCH),
- rolling/out-of-sample forecasts,
- cross-index volatility spillover analysis,
- and a deployment-ready dashboard.
