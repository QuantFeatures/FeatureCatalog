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

The same data is also published on Hugging Face, one dataset per venue with one Parquet file per module and market:
[QuantFeatures/binance-hourly-features](https://huggingface.co/datasets/QuantFeatures/binance-hourly-features), [QuantFeatures/okx-hourly-features](https://huggingface.co/datasets/QuantFeatures/okx-hourly-features), [QuantFeatures/bybit-hourly-features](https://huggingface.co/datasets/QuantFeatures/bybit-hourly-features), [QuantFeatures/hyperliquid-hourly-features](https://huggingface.co/datasets/QuantFeatures/hyperliquid-hourly-features).

A missing file, or a missing instrument row within a file, means no published record for that module, instrument, and interval; it must not be interpreted as zero activity.
