# State-Dependent U.S. Equity Sector & Factor Rotation

A systematic investing research project testing whether **state-dependent trend signals can improve active U.S. equity allocation** relative to strategic allocation, conventional time-series momentum, and passive market exposure.

The framework translates my TradingView **Trend Following SuperSmoother – Accumulation Zones [JW]** model from Pine Script into Python for portfolio construction and backtesting.

## Strategy

Rather than treating trend as a binary bullish/bearish signal, the model identifies different stages of a trend:

**Bearish → Early Reversal → Positive Trend → Pullback Accumulation → Profit Taking**

These states dynamically adjust portfolio weights around a strategic allocation.

The core implementation is:

- Weekly signal generation
- 52-week inverse-volatility strategic weights
- Active multipliers from **-50% to +50%**
- 10 percentage-point accumulation/profit-taking steps
- Long-only and fully invested
- No leverage in the core specification
- Friday-close signals executed on the next U.S. trading session

## Research Design

The original universe contains the **11 U.S. GICS sector ETFs**, benchmarked against:

- **SPY** — passive U.S. equity exposure
- **Strategic Inverse Volatility** — allocation without tactical signals
- **12-Month TSMOM** — conventional time-series momentum
- **State-Dependent Rotation** — proposed strategy

The project explicitly separates the performance of the strategic portfolio from the incremental contribution of the state-dependent signal.

## Extensions

Following the frozen core research specification, additional experiments investigate:

- Alternative treatment of bearish sectors
- Constrained and unconstrained capital redistribution
- Long/short portfolios
- Daily VIX and sector-correlation systemic-risk overlays
- State-dependent crisis re-risking
- Fixed and volatility-targeted leverage
- U.S. equity factor rotation
- Combined **sector + factor** allocation

The factor extension applies the same frozen signal parameters to momentum, quality, value, size and minimum-volatility ETFs without re-optimizing the model.

## Findings

The research indicates that the state-dependent signal can add value relative to both the underlying strategic allocation and conventional TSMOM.

The signal also transfers from sectors to U.S. equity factors. A combined **16-ETF sector + factor universe** produces particularly encouraging relative results, suggesting that the model may function as a broader cross-sectional capital-allocation framework rather than solely as a sector-rotation strategy.

Passive SPY nevertheless outperforms the unleveraged active portfolios over the available sample, so the results should be interpreted as evidence of **incremental allocation value**, not universal outperformance of passive equities.

## Methodology

The research emphasizes reproducibility and protection against common backtesting errors through:

- Strict signal/execution timing
- Frozen canonical parameters
- Pine-to-Python parity testing
- Transaction-cost and turnover analysis
- Parameter sensitivity testing
- Subperiod analysis
- Leave-one-sector-out tests
- Concentration diagnostics
- Separation of core hypotheses from subsequent research extensions

## Technology

**Python · Google Colab · pandas · NumPy · yfinance · Matplotlib · TradingView Pine Script**

## Disclaimer

This repository is an independent quantitative research project for educational and research purposes. It does not constitute investment advice. Backtested results are hypothetical and are not indicative of future performance.
