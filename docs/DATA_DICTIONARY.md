# Data dictionary
This catalog describes the modules in the public sample dataset. It documents what customers receive without disclosing proprietary feature-engine implementation details.

Features are organized in two levels: module, then feature name. A feature is identified by both, for example `TradeFlow.vwap_buy`; the same feature name can appear in more than one module with a module-specific definition. The module name is also the module id in file paths.

Coverage lists each venue's first and last sample day; file counts are on the module pages.

| Module | Input | Markets | Fields | Coverage by venue | Module page |
| --- | --- | --- | ---: | --- | --- |
| TradeFlow | Exchange trades | Spot and perpetual | 45 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01; Hyperliquid 2024-11-01–2026-10-01 | [details](modules/TradeFlow.md) |
| TradeTick | Exchange trades | Spot and perpetual | 33 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01; Hyperliquid 2024-11-01–2026-10-01 | [details](modules/TradeTick.md) |
| TradeCovar | Exchange trades | Spot and perpetual | 30 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01; Hyperliquid 2024-11-01–2026-10-01 | [details](modules/TradeCovar.md) |
| TradeCovarPlus | Exchange trades | Spot and perpetual | 54 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01; Hyperliquid 2024-11-01–2026-10-01 | [details](modules/TradeCovarPlus.md) |
| TradeStats | Exchange trades | Spot and perpetual | 24 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01; Hyperliquid 2024-11-01–2026-10-01 | [details](modules/TradeStats.md) |
| TradeGroup | Exchange trades | Spot and perpetual | 123 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01; Hyperliquid 2024-11-01–2026-10-01 | [details](modules/TradeGroup.md) |
| TradeGroupPlus | Exchange trades | Spot and perpetual | 124 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01; Hyperliquid 2024-11-01–2026-10-01 | [details](modules/TradeGroupPlus.md) |
| TradeLarge | Exchange trades | Spot and perpetual | 123 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01; Hyperliquid 2024-11-01–2026-10-01 | [details](modules/TradeLarge.md) |
| TradeGradient | Exchange trades | Spot and perpetual | 42 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01; Hyperliquid 2024-11-01–2026-10-01 | [details](modules/TradeGradient.md) |
| TradeImpact | Exchange trades | Spot and perpetual | 42 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01; Hyperliquid 2024-11-01–2026-10-01 | [details](modules/TradeImpact.md) |
| QuoteBasic | Best-bid/offer quotes | Spot and perpetual | 71 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01; Hyperliquid 2024-11-01–2026-10-01 | [details](modules/QuoteBasic.md) |
| FundingRate | Derivative ticker feed | Perpetual only | 33 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01; Hyperliquid 2024-11-01–2026-10-01 | [details](modules/FundingRate.md) |
| LiqFlow | Liquidation feed | Perpetual only | 15 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01 | [details](modules/LiqFlow.md) |
| LiqStats | Liquidation feed | Perpetual only | 77 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01 | [details](modules/LiqStats.md) |
| OpenIntBasic | Derivative ticker feed | Perpetual only | 33 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01; Hyperliquid 2024-11-01–2026-10-01 | [details](modules/OpenIntBasic.md) |
| OpenIntPlus | Derivative ticker feed | Perpetual only | 45 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01; Hyperliquid 2024-11-01–2026-10-01 | [details](modules/OpenIntPlus.md) |
| OpenIntGradient | Derivative ticker feed | Perpetual only | 39 | Binance 2019-12-01–2026-10-01; OKX 2020-01-01–2026-10-01; Bybit 2020-06-01–2026-10-01; Hyperliquid 2024-11-01–2026-10-01 | [details](modules/OpenIntGradient.md) |
| QuoteGradient | Best-bid/offer quotes | Spot and perpetual | 60 | Binance 2019-12-01–2026-10-01 | [details](modules/QuoteGradient.md) |
| TradeRank | Exchange trades | Spot and perpetual | 84 | Binance 2019-12-01–2026-10-01 | [details](modules/TradeRank.md) |
