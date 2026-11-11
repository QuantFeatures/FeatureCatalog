# Coverage

Coverage is explicit rather than implied. The current sample dataset (feature version `3.0.0`) contains hourly features for the first UTC day of each month within each venue's range. Module-level date ranges are in [DATA_DICTIONARY.md](DATA_DICTIONARY.md); file counts are on each module page.

| Venue | Markets | Quote | Instruments | Modules | Sample days |
| --- | --- | --- | --- | --- | --- |
| Binance | spot and perpetual | USDT | BCH, BNB, BTC, ETH, XRP | 19 | 2019-12-01 to 2026-10-01 |
| OKX | perpetual | USDT | BCH, BNB, BTC, ETH, HYPE, XRP | 17 (not `QuoteGradient`, `TradeRank`) | 2020-01-01 to 2026-10-01 |
| Bybit | perpetual | USDT | BCH, BNB, BTC, ETH, HYPE, XRP | 17 (not `QuoteGradient`, `TradeRank`) | 2020-06-01 to 2026-10-01 |
| Hyperliquid | perpetual | USDC (the `quote` column and path label read `usdt`) | BCH, BNB, BTC, ETH, HYPE, XRP | 15 (not `LiqFlow`, `LiqStats`, `QuoteGradient`, `TradeRank`) | 2024-11-01 to 2026-10-01 |

- Every file holds one row per instrument for its interval.
- Funding, liquidation, and open-interest modules cover perpetuals only.
- Intervals are hourly and labelled by interval start time (see [DATA_SPECIFICATION.md](DATA_SPECIFICATION.md)); the time zone is UTC.
- Every venue uses the same schema for a given module.

## Hyperliquid: every UTC day of 2026, and live

Two more Hyperliquid datasets hold every UTC day rather than one day a month, for the BCH, BNB, BTC, ETH, HYPE, XRP perpetuals (feature version `3.1.0`):

| Dataset | Days | Intervals | Update | Published |
| --- | --- | --- | --- | --- |
| Hyperliquid Features 2026 | 2026-01-01 to the previous UTC day | 1 hour and 10 minutes | Daily, after 01:30 UTC, adds the previous UTC day | [Hugging Face](https://huggingface.co/datasets/QuantFeatures/hyperliquid-features), [Kaggle](https://www.kaggle.com/datasets/drdanguo/quantfeatures-hyperliquid-hourly-features) |
| Hyperliquid Live 10-Minute Features | The last 7 UTC days, today included | 10 minutes | Every 10 minutes, a few minutes after each interval ends | [Hugging Face](https://huggingface.co/datasets/QuantFeatures/hyperliquid-live-features), [Kaggle](https://www.kaggle.com/datasets/drdanguo/quantfeatures-hyperliquid-live-features) |

The 2026 dataset changes source on 2026-11-05, so its modules depend on the period:

| Period | Source | Modules |
| --- | --- | --- |
| 2026-01-01 to 2026-11-04 | Hyperliquid's archive of node trade fills (trades only); funding settlements from its public API | 13: `TradeFlow`, `TradeTick`, `TradeCovar`, `TradeCovarPlus`, `TradeStats`, `TradeGroup`, `TradeGroupPlus`, `TradeLarge`, `TradeGradient`, `TradeImpact`, `FundingPaid`, `LiqFlow`, `LiqStats` |
| From 2026-11-05 | QuantFeatures' recording of Hyperliquid's public websocket trade, best bid/offer and asset context streams; funding settlements from its public API | 16: `TradeFlow`, `TradeTick`, `TradeCovar`, `TradeCovarPlus`, `TradeStats`, `TradeGroup`, `TradeGroupPlus`, `TradeLarge`, `TradeGradient`, `TradeImpact`, `QuoteBasic`, `FundingRate`, `FundingPaid`, `OpenIntBasic`, `OpenIntPlus`, `OpenIntGradient` |

The live dataset has the 15 modules recorded from 2026-11-05 except `FundingPaid`.

- `FundingPaid` is the hourly funding settlement, so it has no 10-minute files.
- Days are consecutive, so values carried from one interval to the next, such as the previous price and tick direction, continue across midnight UTC. On 2026-11-05, where the source changes, they start fresh.
- These datasets are published as one Parquet file per module and interval: `data/<Module>/perp.parquet` (1 hour) and `data/10min/<Module>/perp.parquet` (10 minutes); the file layout below applies to the monthly sample.
- Live intervals are computed as each interval ends. The next day the same intervals are computed again from the full day's recording for the 2026 dataset; trade modules match exactly, and quote, funding and open-interest modules differ slightly in a few intervals a day. The 2026 dataset is the reference.
- From 2026-11-05: when our recording is interrupted for 60 seconds or more, every interval that overlaps the interruption has all feature values NaN (count columns null); the rows are kept. The dataset cards and `manifest.json` (`unavailable_intervals`, `unavailable_intervals_10min`) list these intervals. `FundingPaid` comes from the exchange API and is not affected.

## Later listings

Some instruments start after their venue's first sample day because they were not yet listed:

- **Binance:** BCH perpetual from 2020-01-01; XRP perpetual from 2020-02-01; BNB perpetual from 2020-03-01.
- **OKX:** BNB perpetual from 2023-01-01; HYPE perpetual from 2025-03-01.
- **Bybit:** ETH perpetual from 2020-11-01; BCH perpetual from 2021-01-01; XRP perpetual from 2021-06-01; BNB perpetual from 2021-07-01; HYPE perpetual from 2025-01-01.
- **Hyperliquid:** HYPE perpetual from 2025-01-01.

## Intervals with limited or no data

Exchanges and data recorders have outages, maintenance windows, and late listings, so some sample intervals have little or no source data. In these intervals counts are zero and price-type values are NaN.

| Venue | Modules | Day(s) | Instruments | Intervals without source data (UTC hour starts) |
| --- | --- | --- | --- | --- |
| Binance | `OpenIntBasic`, `OpenIntPlus`, `OpenIntGradient` | 2019-12-01 to 2020-05-01 | All | All: the source ticker carries no open-interest values before 2020-06-01 |
| Hyperliquid | `FundingRate`, `OpenIntBasic`, `OpenIntPlus`, `OpenIntGradient` | 2024-11-01 | All | All except 00 and 21 |
| Hyperliquid | same | 2024-12-01 | All | All except 00, 02, 06, 15, 21 |
| Hyperliquid | same | 2025-01-01 | All | All except 00, 04, 13 |
| Hyperliquid | same | 2025-02-01 | All | All except 00 |
| OKX | Trade modules and `QuoteBasic` | 2020-01-01 | BCH | 21 |
| OKX | `LiqFlow`, `LiqStats` | 2020-01-01 to 2020-12-01 | All | All: no liquidation records exist for these days, so zero counts there mean no data, not no liquidations |
| Bybit | `LiqFlow`, `LiqStats` | 2020-06-01 to 2020-10-01, and 2020-12-01 | All | All: no liquidation records exist for these days |

## File layout

```text
data/features/<module>/eod/3.0.0/<exchange>/<spot|perp>/usdt/1h/YYYY/MM/DD/<module>-<exchange>-<spot|perp>-usdt.YYYYMMDD.HHMMSS.pqt.gz
```

`<exchange>` is one of `binance`, `okx`, `bybit`, `hyperliquid`. `YYYY/MM/DD` and `YYYYMMDD.HHMMSS` are the UTC interval start. Each `.pqt.gz` is a gzip-compressed Parquet file.

The same data is also published as one dataset with one Parquet file per module and market, on
[Hugging Face](https://huggingface.co/datasets/QuantFeatures/crypto-hourly-features-monthly) and
[Kaggle](https://www.kaggle.com/datasets/drdanguo/quantfeatures-crypto-hourly-features-monthly).

A missing file, or a missing instrument row within a file, means no published record for that module, instrument, and interval; it must not be interpreted as zero activity.
