# Data specification

## Record semantics

Each Parquet file holds the interval-based features of one module for one UTC interval, with one row per instrument. Timestamps are UTC. An interval is half-open: `[start_time_utc, end_time_utc)`. `end_time_utc` is the time at which all information in that interval is known; use it to avoid look-ahead bias.

## File and partition naming

Version 2.0.0 and later label both the partition path and Parquet filename with
the UTC interval start time. For example, the one-hour interval
`[2026-10-01 23:00:00, 2026-10-02 00:00:00)` is stored below
`2026/10/01/` and is named with `20261001.230000`. The label is a storage key,
not an availability timestamp: the interval's information is available only at
its end time.

Version 1.0.0 used interval-end labels. Consumers must not combine the two
versions by filename alone.

The module directory and filename prefix use the module name, for example
`TradeFlow/eod/3.0.0/.../TradeFlow-binance-perp-usdt.20261001.230000.pqt`.

## Identifiers and units

Features are organized in two levels: module, then feature name. A feature is identified by both (for example `TradeFlow.vwap_buy`); the same feature name can appear in more than one module with a module-specific definition. `exch` and `type` identify the venue (`binance`, `okx`, or `hyperliquid`) and market type. Each instrument is a pair of a base asset priced in a quote asset, written `BASE/QUOTE`; for example, `BTC/USDT` is bitcoin priced in USDT. The `base` and `quote` fields hold the two symbols; typical quote assets are USDT, USDC, and BUSD. Hyperliquid perpetuals settle in USDC, but their `quote` field and file path read `usdt`.

Prices, including bid, ask, and mid, are in the quote asset per unit of the base asset. Quantities, including volume and bid or ask size, are in units of the base asset. Value and notional fields are in the quote asset. `_bps` fields are in basis points.

## Reading feature names

Feature names are built from a measure and optional qualifiers. Each module page defines every feature exactly; these conventions help when scanning them.

| Part | Meaning | Example |
| --- | --- | --- |
| `open`, `high`, `low`, `close` | First, highest, lowest, last value in the interval | `close`, `high_bid` |
| `vwap`, `twap`, `awap` | Volume-, time-, and equally weighted average price | `vwap_buy` |
| `vwa`, `twa`, `awa`, `pwa` | Volume-, time-, equally, and price-weighted average of a non-price quantity | `twa_spread` |
| `n`, `num`, `count` | Number of events | `ntrade`, `nquote_bid`, `num_mid_up` |
| `volume`, `size`, `share` | Quantity, in the base asset | `volume_sell`, `close_bidsize` |
| `tradeval`, `value` | Value, price × quantity, in the quote asset | `tradeval_up` |
| `_buy`, `_sell` | Buyer- or seller-initiated trades only; for liquidations, buy- or sell-side orders | `ntrade_buy` |
| `_up`, `_down`, `_flat` | Events in which the price or named quantity rose, fell, or was unchanged | `ntrade_up` |
| `_bps` | Basis points | `close_spread_bps` |
| `_rank`, `_zscore` | Cross-sectional rank and z-score across instruments | `vwps_rank` |
| `stdev`, `skew`, `kurtosis` | Standard deviation, skewness, excess kurtosis | `stdev_price` |
| `cov`, `rho`, `corr` | Covariance and correlation | `rho_pv` |

## Missingness and quality

Every column is always present; there are no null values. In floating-point fields, NaN means unavailable or not validly computable, for example a statistic that needs more trades than the interval had. NaN is never equivalent to zero. Integer count fields are always defined; a zero count means no qualifying events in the interval. Input gaps, exchange resets, duplicate events, and unsupported source fields can also result in NaN. Customers should retain NaN values, inspect coverage, and avoid forward filling unless their research design explicitly supports it.

## Sample-day boundary

This sample covers isolated days (the first UTC day of each month), not consecutive days. Some features use a value from before the interval, for example the previous interval's closing price or the last up or down move. The sample does not include the preceding day, so these values are unknown at the start of each sample day:

- In the first interval (00:00–01:00 UTC), changes are measured from the first observation of the day, so a move across midnight is not included, and time-weighted averages start at the first observation.
- Up and down time-weighted averages start at the first up (or down) move of the day; until that move occurs, which can be after 01:00, they cover less than the full interval.

Datasets built from consecutive days do not have this limitation.

For research that needs strict comparability, exclude the 00:00 UTC interval of each sample day.

## Point-in-time use

QuantFeatures data is designed for point-in-time (as-of) research and use: at any time T, you can know exactly which
values were available, without look-ahead.

- **Availability.** A record describes `[start_time_utc, end_time_utc)` and becomes available at `end_time_utc`. For a
  decision at time T, use only records with `end_time_utc <= T`. File labels are interval start times; they are storage
  keys, not availability times.
- **Event assignment.** Trades, quotes, and other events are assigned to intervals by the exchange's own event timestamp,
  so an interval's content does not depend on where or when the data was received.
- **No silent revisions.** Published values are never changed in place. Corrections or definition changes are released
  as a new feature version (see [Versioning](#versioning)), and earlier versions remain available.
- **Real-time delivery.** Real-time records use the same modules, fields, and definitions as historical files. Each
  interval is published once, shortly after `end_time_utc`, after a brief wait for late exchange messages, and carries
  its publication time, so live use can be replayed exactly as it was known. Messages that reach us after an interval
  is published are not added to that real-time record; this is the only way a real-time record can differ from the
  historical file for the same interval. The publication delay is stated with each real-time product.
- **Tools.** Programmatic access, including the QuantFeatures MCP server for AI agents, supports an *as-of* parameter
  that returns only records available at the given time.

## Versioning

The path includes a feature version. Corrections or definition changes must be published as a new dataset version with a manifest and checksums; previously released files are immutable. The interval-start naming convention begins with version `2.0.0`.

## Compression

Sample dataset files use gzip (`.pqt.gz`). Decompress before opening with a Parquet reader. Production feature output is Parquet with Zstandard compression.
