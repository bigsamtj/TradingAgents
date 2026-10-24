
<div align="center">

# TradingAgents FX

### Multi-Agent AI for Intraday Forex & Gold Market Analysis

**Analyze. Correlate. Evaluate.**

An AI-powered adaptation of the TradingAgents framework, focused on
multi-timeframe foreign exchange and gold market analysis.

<br />

![Python](https://img.shields.io/badge/Python-3.11%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![AI](https://img.shields.io/badge/AI-Multi--Agent-7C3AED?style=for-the-badge)
![Market](https://img.shields.io/badge/Market-Forex%20%7C%20Gold-15803D?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-In%20Development-D97706?style=for-the-badge)

</div>

---

## Overview

**TradingAgents FX** is a forex-focused adaptation of the open-source
[TradingAgents](https://github.com/TauricResearch/TradingAgents)
framework.

The project aims to adapt its multi-agent research workflow for
intraday analysis of currency pairs and gold. It is designed to combine
technical evidence, multi-timeframe market context, relevant economic
news, and structured risk assessment into a readable analysis report.

The initial focus is on **analysis and trade setups**, not automatic
trade execution.

> **Development notice:** This is an adaptation in progress.
> Forex-specific data integration, indicators, agent instructions, and
> signal validation must be implemented and tested before the project
> can be considered ready for practical use.

---

## Supported Instruments

| Symbol | Instrument | Market |
|:---:|---|---|
| `XAUUSD` | Gold / US Dollar | Precious Metal |
| `GBPUSD` | British Pound / US Dollar | Forex |
| `EURUSD` | Euro / US Dollar | Forex |
| `USDJPY` | US Dollar / Japanese Yen | Forex |

Instrument availability, symbol mapping, and price specifications
depend on the selected market-data provider.

## Multi-Timeframe Analysis

The intended analysis workflow uses four timeframes.

| Timeframe | Intended Purpose |
|:---:|---|
| `M15` | Intraday setup identification |
| `M30` | Intermediate confirmation |
| `H1` | Intraday trend and market structure |
| `H4` | Higher-timeframe context |

The system is intended to compare evidence across timeframes rather
than treating an isolated indicator as a complete trading signal.

---

## Planned Capabilities

### Market Analysis
- Multi-timeframe price-action analysis
- Trend and market-structure assessment
- Support and resistance evaluation
- Technical indicators and volatility analysis
- Identification of conflicting market evidence

### AI-Assisted Research
- Multi-agent analysis and reasoning
- Technical and fundamental context
- Economic news and event-risk assessment
- Structured trade-setup explanations
- Evidence-based reporting with explicit uncertainty

### Risk Assessment
- Potential entry conditions and invalidation levels
- Stop-loss and target evaluation
- Risk-to-reward calculations
- Spread and volatility considerations
- `NO_TRADE` outcomes when evidence is insufficient

*These are planned capabilities; features remain subject to implementation
and validation.*

---

## Market Data & TradingView

TradingView is the preferred charting and market-analysis environment.

A suitable, authorized market-data integration is required to retrieve
historical and current candles for `XAUUSD`, `GBPUSD`, `EURUSD`, and
`USDJPY`.

Potential integration approaches include:

- TradingView alerts and webhook payloads
- An authorized external market-data API
- A supported charting component connected to a separate datafeed

TradingView charting and alert functionality should not be assumed to
provide unrestricted historical market-data access.

The data layer must account for:

- OHLC candle integrity and timestamps
- Timeframe consistency and candle completeness
- Provider-specific instrument symbols
- Data freshness and missing observations
- Differences between spot gold and gold futures

**Data integrity rule:** The system must not invent prices, market
observations, indicator values, or news events when source data is
unavailable.

---

## Signal Analysis Workflow

The intended workflow is:

1. Retrieve market data from the configured provider.
2. Validate candle integrity, timestamps, and data availability.
3. Calculate technical indicators and volatility measures.
4. Evaluate M15, M30, H1, and H4 evidence.
5. Incorporate relevant, verified economic and news context.
6. Generate a structured analysis using the agent workflow.
7. Assess setup conditions, invalidation, and risk.
8. Report the findings, uncertainty, and missing evidence.

### Intended Report Structure

Each analysis should include:

| Field | Description |
|---|---|
| Instrument | Selected currency pair or gold instrument |
| Timestamp | Analysis time and relevant candle timestamps |
| Market Bias | Bullish, bearish, neutral, or inconclusive |
| Technical Evidence | Indicators and price observations supporting the assessment |
| Timeframe Agreement | Agreement or conflict across the selected timeframes |
| Setup Conditions | Conditions that would support a potential trade |
| Invalidation | Conditions that would invalidate the setup |
| Risk Assessment | Volatility, spread, and risk-to-reward considerations |
| Data Quality | Source, freshness, missing data, and limitations |
| Decision | Potential setup or `NO_TRADE`, with explanation |

A generated signal is an analytical output, not a guarantee of market
direction or trading performance.

---

## Technology

The project builds on the existing TradingAgents codebase.

The forex adaptation is intended to introduce or extend:

- Market-data provider integration
- Forex-specific technical analysis
- Multi-timeframe processing
- Agent instructions for currency and gold markets
- Structured analysis reports
- Automated tests for data quality and signal logic

Existing framework components will be retained where appropriate,
rather than replacing the entire project unnecessarily.

---

## Development Roadmap

- [x] Fork the upstream TradingAgents repository
- [ ] Adapt project documentation for forex analysis
- [ ] Inspect the existing data-provider architecture
- [ ] Implement and validate the forex market-data adapter
- [ ] Add multi-timeframe indicator calculations
- [ ] Adapt agent instructions for forex and gold
- [ ] Add data-quality and analysis tests
- [ ] Validate using historical market data
- [ ] Evaluate signal quality using demo and paper trading
- [ ] Develop a dedicated analysis dashboard

---

## Installation

The existing repository's installation instructions remain the starting
point while the forex-specific dependencies and configuration are being
developed.

See the upstream project's
[README and installation instructions](https://github.com/TauricResearch/TradingAgents)
for the current setup procedure.

Forex-specific setup instructions will be added after the provider
integration and analysis workflow have been verified.

---

## Responsible Use

TradingAgents FX is intended for research, educational use, and
experimental market analysis.

- AI-generated analysis may be incorrect or incomplete.
- Historical performance does not guarantee future results.
- Market prices, spreads, and execution conditions can change rapidly.
- Signals should be independently evaluated and tested before use.
- No automatic live-trading functionality is implied by this project.

**This project does not provide financial advice or guarantee profits.**

---

## Attribution & Licensing

TradingAgents FX is an adaptation of
[TauricResearch/TradingAgents](https://github.com/TauricResearch/TradingAgents).

The original project and its contributors retain their applicable
copyright and attribution rights. Review the repository's `LICENSE`
file and comply with the upstream license when modifying or
redistributing the project.

---

<div align="center">

**TradingAgents FX**

*Evidence-led analysis. Structured reasoning. Disciplined risk assessment.*

</div>
