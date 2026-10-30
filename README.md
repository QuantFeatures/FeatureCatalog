# Feature Catalog

Public taxonomy and documentation for **interval-based quantitative indicators and summary features**. The underlying implementation is proprietary and is not included here.

## Scope

The current sample dataset publishes hourly features for four venues: Binance USDT spot and perpetual instruments (19 modules), OKX and Bybit USDT perpetuals (17 modules each), and Hyperliquid USDC perpetuals (15 modules). [Coverage](docs/COVERAGE.md) lists each venue's instruments, modules, and sample days. Each module has a page under [docs/modules/](docs/modules/) with its full field list.

| Family | Modules | Inputs | Markets |
| --- | --- | --- | --- |
| Trade activity and flow | TradeFlow, TradeTick, TradeGroup | trades | spot, perpetual |
| Trade distribution and tails | TradeStats, TradeGroupPlus, TradeLarge | trades | spot, perpetual |
| Trade relationships | TradeCovar, TradeCovarPlus, TradeImpact | trades | spot, perpetual |
| Trade dynamics | TradeGradient | trades | spot, perpetual |
| Cross-sectional market activity | TradeRank | trades | spot, perpetual |
| Top of book | QuoteBasic | best bid/offer | spot, perpetual |
| Top-of-book dynamics | QuoteGradient | best bid/offer | spot, perpetual |
| Funding | FundingRate | derivative ticker | perpetual |
| Open interest | OpenIntBasic, OpenIntPlus, OpenIntGradient | derivative ticker | perpetual |
| Liquidations | LiqFlow, LiqStats | liquidation events | perpetual |

Order-book inputs are top-of-book (best bid/offer) only; full-depth order-book features are not part of the current release.

## Documentation contract

Features are organized in two levels: module, then feature name (for example `TradeFlow.vwap_buy`). Each published feature needs: stable module and feature name, description, unit, input schema, interval semantics, look-back, missing-value (NaN) behavior, venue applicability, version, and QA status.

See `templates/feature-definition.yaml`, `FEATURE_VALIDITY.md`, and `FEATURE_VERSIONING.md`.

## Documentation

- [Data dictionary](docs/DATA_DICTIONARY.md): published fields, types, units, and public-safe interpretations.
- [Data specification](docs/DATA_SPECIFICATION.md): timestamps, intervals, identifiers and units, how to read feature names, missing values, the sample-day boundary, and point-in-time use for historical and real-time data.
- [Coverage](docs/COVERAGE.md): venue, market, interval, and availability conventions.
- [Methodology](docs/METHODOLOGY.md): high-level processing and quality controls.
- [Module definitions](docs/modules/): inputs, coverage, and field dictionaries for each published module.

[Feature samples](https://github.com/QuantFeatures/FeatureSamples) · Hugging Face: [Binance](https://huggingface.co/datasets/QuantFeatures/binance-hourly-features), [OKX](https://huggingface.co/datasets/QuantFeatures/okx-hourly-features), [Bybit](https://huggingface.co/datasets/QuantFeatures/bybit-hourly-features), [Hyperliquid](https://huggingface.co/datasets/QuantFeatures/hyperliquid-hourly-features) · Partnerships: [QuantFeatures@gmail.com](mailto:QuantFeatures@gmail.com)
