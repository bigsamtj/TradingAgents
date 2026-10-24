
<div align="center">

# TradingAgents FX

### DXY-Led Multi-Agent Market Analysis & Intraday Trade Planning

**Macro Bias · Market Structure · Multi-Timeframe Confluence**

![Python](https://img.shields.io/badge/Python-3.11%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Framework](https://img.shields.io/badge/Framework-Multi--Agent_AI-7C3AED?style=for-the-badge)
![Markets](https://img.shields.io/badge/Markets-Forex%20%7C%20Gold%20%7C%20Indices-15803D?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-In_Development-D97706?style=for-the-badge)

*A strategy-focused adaptation of the open-source TradingAgents framework.*

</div>

---

## Overview

**TradingAgents FX** is a forex and multi-market analysis adaptation of
[TauricResearch/TradingAgents](https://github.com/TauricResearch/TradingAgents).

The project aims to adapt the framework's multi-agent research and
reasoning workflow to a specific trading methodology built around:

1. **DXY macro bias** — assessing broad US dollar strength or weakness.
2. **Multi-timeframe market direction** — establishing higher-timeframe
   context before looking for entries.
3. **Market structure** — examining liquidity, support and resistance,
   trendlines, Break of Structure (BOS), Change of Character (CHOCH),
   Order Blocks (OB), and PL.
4. **Directional confirmation** — refining the bias on H4 and H1.
5. **Entry refinement** — seeking confluence on M30 and M15.
6. **Fibonacci refinement** — assessing premium and discount zones.
7. **Confluence-based decisions** — avoiding setups that lack sufficient
   supporting evidence.

The objective is to produce structured, evidence-based market analysis
and potential trade setups rather than force a BUY or SELL signal.

> **Development status:** This is an adaptation in progress. The
> strategy described here defines the intended methodology. Features
> are not considered implemented merely because they are documented.

---

## Trading Philosophy

> "Forex is not a get-rich-quick game, it's a psychological
> redistribution system. And if you struggle with money, survive your
> emotions, it is a strategy-proof."

This project follows a disciplined, confluence-first approach to
market analysis. The methodology is based on the author's own months
of backtesting and testing. Its effectiveness is not independently
verified or guaranteed by this software.

The system should prioritize structured reasoning, observable market
evidence, and disciplined risk assessment over isolated indicators
or unsupported predictions.

---

## Preferred Markets & Instruments

The strategy uses the US Dollar Index (DXY) as its primary macro
filter, then evaluates selected markets for opportunities consistent
with the broader bias and each instrument's own structure.

| Symbol | Instrument | Primary Analytical Role |
|:---:|---|---|
| `DXY` | US Dollar Index | Macro USD bias |
| `XAUUSD` | Gold / US Dollar | Gold market analysis |
| `US30` | Dow Jones Industrial Average index | US equity index analysis |
| `NAS100` | Nasdaq 100 index | US technology-heavy index analysis |
| `GBPUSD` | British Pound / US Dollar | Major currency pair |
| `EURUSD` | Euro / US Dollar | Major currency pair |
| `USDJPY` | US Dollar / Japanese Yen | Major currency pair |
| `USDCAD` | US Dollar / Canadian Dollar | Major currency pair |
| `NZDUSD` | New Zealand Dollar / US Dollar | Major currency pair |

Actual ticker names, trading sessions, price precision, and instrument
specifications depend on the selected data provider or broker.

DXY is a directional filter, not an automatic inverse-trade rule.
Different markets may respond differently to USD movements, interest
rates, yields, risk sentiment, and instrument-specific developments.

---

## Core Trading Model

### 1. DXY — Macro USD Bias

Analyze the US Dollar Index to establish the broad directional context
for the US dollar.

The analysis should assess:

- Overall trend and market structure
- Important higher-timeframe support and resistance
- Psychological price levels
- Liquidity zones and potential reactions
- BOS and CHOCH where supported by price evidence
- Agreement or conflict between DXY and the target instrument

The resulting USD bias should be classified as **bullish, bearish,
neutral, or inconclusive**, with supporting evidence.

DXY bias must not override contradictory price action or other
important market drivers without explanation.

### 2. MTF, WTF & DTF — Market Direction

Establish the broader market direction using the relevant higher
timeframes.

The analysis should identify:

- Major support and resistance
- Psychological levels
- Liquidity zones
- Trendlines
- Break of Structure (BOS)
- Change of Character (CHOCH)
- Order Blocks (OB)
- PL, using the author's intended definition

These concepts should be supported by identifiable candle data,
price levels, and explicit detection rules.

**Terminology note:** PL is retained from the author's methodology.
Its precise definition must be confirmed before it is implemented
as a formal programmatic rule.

### 3. H4 — Intermediate Structure

Use H4 to refine the higher-timeframe directional bias.

Evaluate:

- Trendline structure
- BOS and CHOCH
- Order Blocks
- Relevant structural levels
- Alignment with Monthly, Weekly, and Daily context

The 89-period and 200-period moving averages may be used for
**trend alignment only**.

They must not independently generate trade signals or replace
market-structure analysis.

### 4. H1 — Directional Entry

Use H1 to confirm the H4 structure and refine the directional setup.

Evaluate:

- Confirmation or rejection of H4 bias
- Momentum shifts
- Market reaction at key levels
- Short-term trend direction
- Relevant liquidity and structural behaviour

The 7-period and 14-period moving averages may be used for
**entry confirmation and signal precision only**.

They are supporting tools, not standalone entry triggers.

### 5. M30 → M15 — Entry Refinement

Use M30 and M15 to refine entry timing after the higher-timeframe
analysis has established a sufficiently clear directional context.

Evaluate:

- Confluence with H4 and H1 structure
- Reaction at key market levels
- Fair Value Gaps (FVG)
- Local liquidity and price action
- Entry conditions and invalidation
- Whether the potential setup offers an acceptable risk profile

A lower-timeframe pattern should not automatically override the
established higher-timeframe context.

### 6. Fibonacci — Premium & Discount Refinement

Use Fibonacci retracement levels to refine relevant price zones.

The key levels are:

| Level | Value |
|:---:|---:|
| 1 | `0.236` |
| 2 | `0.382` |
| 3 | `0.500` |
| 4 | `0.618` |
| 5 | `0.786` |

Fibonacci levels should be calculated from an explicitly identified
swing or dealing range. The system must document the anchors used
and must not assume a level is significant without supporting
market context.

Premium and discount assessments should be combined with structure,
liquidity, and other relevant confluences.

### 7. Confluence-First Decision

**Only consider a setup when sufficient confluence is present.**

The analysis engine should assess the combined evidence from:

- DXY macro bias
- Higher-timeframe direction
- H4 structure
- H1 directional confirmation
- M30/M15 entry refinement
- Relevant Fibonacci zones
- Risk and data-quality checks

The final outcome should be one of:

- `POTENTIAL_LONG` — evidence supports evaluating a long setup.
- `POTENTIAL_SHORT` — evidence supports evaluating a short setup.
- `NO_TRADE` — confluence is insufficient, contradictory, or unverified.

These outcomes represent analytical classifications, not guaranteed
trade instructions or predictions of profitability.

---

## Timeframe Modes

TradingAgents FX is intended to support two distinct analysis modes.

### Mode A — New Week / New Month Analysis

**Purpose:** Establish the broader directional bias and work down
toward the H1 entry timeframe.

| Sequence | Timeframe | Intended Function |
|:---:|:---:|---|
| 1 | Yearly | Long-term macro structure |
| 2 | Monthly | Major directional context and key zones |
| 3 | Weekly | Intermediate directional structure |
| 4 | Daily | Refined market direction and levels |
| 5 | H4 | Intermediate structure and bias confirmation |
| 6 | H1 | Directional entry assessment |

The analysis should preserve the relationship between the larger
market structure and the lower-timeframe setup.

### Mode B — Daily Refinement

**Purpose:** Refine an established bias and evaluate potential
intraday entries.

| Sequence | Timeframe | Intended Function |
|:---:|:---:|---|
| 1 | H4 | Refine structural bias |
| 2 | H1 | Confirm direction and momentum |
| 3 | M30 | Evaluate intermediate confluence |
| 4 | M15 | Refine entry timing and invalidation |

Daily refinement does not replace the broader macro and
higher-timeframe analysis. It operates within that context.

### Timeframe Configuration Summary

| Setting | New Week / New Month | Daily Refinement |
|---|---|---|
| Starting context | Yearly / Monthly | Existing higher-timeframe bias |
| Core direction | Monthly, Weekly, Daily | H4 |
| Confirmation | H4 | H1 |
| Entry assessment | H1 | M30 → M15 |
| Primary objective | Establish broader direction | Refine an existing setup |

---

## Planned Technical Analysis Components

The forex adaptation is intended to implement or extend the
following analytical components.

| Component | Intended Use |
|---|---|
| Trendlines | Identify directional structure |
| BOS | Identify a break in established structure |
| CHOCH | Identify a potential change in structural behaviour |
| OB | Identify candidate order-block zones using defined rules |
| Liquidity zones | Assess potential areas of liquidity concentration |
| Support / Resistance | Identify relevant reaction levels |
| Psychological levels | Evaluate significant round-number zones |
| FVG | Identify price imbalances for entry refinement |
| Fibonacci | Assess premium and discount zones |
| MA 89 / MA 200 | Higher-timeframe trend alignment |
| MA 7 / MA 14 | Lower-timeframe entry confirmation |

The definitions and detection parameters for these components must
be explicit, testable, and consistent. The presence of an indicator
or pattern alone does not establish a valid trading opportunity.

---

## Market Data & TradingView

TradingView is the preferred charting and market-analysis environment.

The backend requires an authorized source for historical and current
price candles for all supported instruments and timeframes.

Potential integration approaches include:

- TradingView alerts and webhooks
- An authorized external market-data API
- A supported charting component connected to an appropriate datafeed

The availability of a chart or TradingView symbol does not imply
unrestricted programmatic access to its historical data.

### Data Integrity Requirements

The system should validate:

- Instrument identity and provider-specific symbol mapping
- OHLC candle integrity
- Candle timestamps and timeframe alignment
- Data freshness and candle completeness
- Missing, duplicated, or invalid observations
- Availability of sufficient historical data
- Differences between spot gold and gold futures
- Provider-specific specifications for indices and currency pairs

The analysis must not invent prices, candles, indicators, structural
levels, or economic events when the underlying evidence is unavailable.

---

## Analysis Output

Each completed analysis should provide a structured report.

| Field | Required Information |
|---|---|
| Analysis Mode | New Week / New Month or Daily Refinement |
| Instrument | Selected market and provider symbol |
| DXY Bias | Bullish, bearish, neutral, or inconclusive |
| Higher-Timeframe Context | Yearly through Daily, where applicable |
| H4 Structure | Direction, key levels, and supporting evidence |
| H1 Confirmation | Structure, momentum, and directional context |
| M30 / M15 Refinement | Entry confluence, FVG, and timing |
| Fibonacci | Anchors, relevant levels, and zone interpretation |
| Risk Assessment | Invalidation, volatility, spread, and risk-to-reward |
| Data Quality | Source, timestamps, missing data, and limitations |
| Final Classification | Potential long, potential short, or no trade |
| Reasoning | Evidence supporting the conclusion and remaining uncertainty |

Every reported level or indicator should be traceable to source
data and reproducible calculations wherever possible.

---

## Risk & Decision Discipline

The intended system should:

- Prefer evidence-backed conclusions over confident speculation.
- Distinguish observed data from analytical interpretation.
- Identify disagreement between DXY and the target instrument.
- Preserve higher-timeframe context when assessing lower timeframes.
- Avoid generating a setup when essential data is missing.
- Account for spread, volatility, and invalidation conditions where
  the required information is available.
- Avoid treating a moving average, Fibonacci level, or chart pattern
  as a sufficient standalone reason to trade.
- Report uncertainty instead of forcing a directional decision.

The project is designed for analysis and signal research. Automatic
live-trading execution is not implied.

---

## Development Roadmap

- [x] Fork the original TradingAgents repository
- [x] Define the intended DXY-led trading methodology
- [x] Define New Week / New Month and Daily Refinement modes
- [ ] Update the forex-specific project documentation
- [ ] Inspect the existing data-provider architecture
- [ ] Implement an authorized market-data integration
- [ ] Add instrument and timeframe configuration
- [ ] Implement multi-timeframe analysis
- [ ] Define testable BOS, CHOCH, OB, FVG, liquidity, and PL rules
- [ ] Add Fibonacci and moving-average refinement
- [ ] Adapt agent instructions to the trading methodology
- [ ] Implement confluence-based signal classification
- [ ] Add tests for data quality and signal logic
- [ ] Evaluate using historical data and out-of-sample testing
- [ ] Validate through demo or paper trading
- [ ] Develop a dedicated analysis dashboard

Checklist items should be marked complete only after the corresponding
functionality has actually been implemented and verified.

---

## Technology & Project Foundation

TradingAgents FX builds upon the existing
[TauricResearch/TradingAgents](https://github.com/TauricResearch/TradingAgents)
codebase and its multi-agent research workflow.

The adaptation aims to preserve useful upstream components while
adding the market-data, technical-analysis, configuration, and
reporting features required by the author's strategy.

Upstream components, dependencies, and installation instructions
should be checked against the version used by this fork.

---

## Installation

The upstream TradingAgents installation process remains the starting
point until the forex-specific provider integration and dependencies
have been validated.

Refer to the original project's
[README and setup instructions](https://github.com/TauricResearch/TradingAgents).

Forex-specific configuration and setup instructions will be added
as the implementation becomes operational.

---

## Disclaimer

TradingAgents FX is intended for research, education, and experimental
market analysis.

- This software does not provide financial advice.
- AI-generated analysis may be incorrect or incomplete.
- Backtesting results do not guarantee future performance.
- Market conditions, spreads, and execution prices can change rapidly.
- The author's trading methodology has not been independently
  validated by this software.
- Users are responsible for independently evaluating any
  analysis before making financial decisions.

**No strategy or software can guarantee trading profits.**

---

## Attribution & Licensing

TradingAgents FX is an adaptation of
[TauricResearch/TradingAgents](https://github.com/TauricResearch/TradingAgents).

The original project and its contributors retain their applicable
copyright and attribution rights. Review the upstream project's
license and this repository's `LICENSE` file before modifying,
distributing, or publishing the adaptation.

---

<div align="center">

### TradingAgents FX

**Macro Bias. Structural Confirmation. Confluence-Driven Analysis.**

*Built around a DXY-led, multi-timeframe trading methodology.*

</div>
