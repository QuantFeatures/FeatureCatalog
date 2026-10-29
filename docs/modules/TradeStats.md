# TradeStats
Standard deviation, skewness, and excess kurtosis of trade prices and trade sizes within an interval.
## Availability
- **Input:** Exchange trades
- **Markets:** Spot and perpetual
- **Feature family:** Trade distribution
- **Coverage, Binance:** 2019-12-01 through 2026-10-01 (interval-start dates); 1,992 hourly files per market (3,984 total).
- **Coverage, OKX:** 2020-01-01 through 2026-10-01 (interval-start dates); 1,968 perp hourly files.
- **Coverage, Bybit:** 2020-06-01 through 2026-10-01 (interval-start dates); 1,848 perp hourly files.
- **Coverage, Hyperliquid:** 2024-11-01 through 2026-10-01 (interval-start dates); 576 perp hourly files.
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Notes
- Statistics are taken across the individual trades in the interval, each trade weighted equally.
- Kurtosis is excess kurtosis: 0 for a normal distribution.
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `stdev_price` | `double` | Standard deviation of trade prices in the interval, each trade weighted equally. |
| `stdev_price_buy` | `double` | Standard deviation of trade prices in the interval, each trade weighted equally. Buyer-initiated trades only (the buyer was the aggressor). |
| `stdev_price_sell` | `double` | Standard deviation of trade prices in the interval, each trade weighted equally. Seller-initiated trades only (the seller was the aggressor). |
| `stdev_volume` | `double` | Standard deviation of trade sizes in the interval, each trade weighted equally. |
| `stdev_volume_buy` | `double` | Standard deviation of trade sizes in the interval, each trade weighted equally. Buyer-initiated trades only (the buyer was the aggressor). |
| `stdev_volume_sell` | `double` | Standard deviation of trade sizes in the interval, each trade weighted equally. Seller-initiated trades only (the seller was the aggressor). |
| `skew_price` | `double` | Skewness of trade prices in the interval, each trade weighted equally. |
| `skew_price_buy` | `double` | Skewness of trade prices in the interval, each trade weighted equally. Buyer-initiated trades only (the buyer was the aggressor). |
| `skew_price_sell` | `double` | Skewness of trade prices in the interval, each trade weighted equally. Seller-initiated trades only (the seller was the aggressor). |
| `skew_volume` | `double` | Skewness of trade sizes in the interval, each trade weighted equally. |
| `skew_volume_buy` | `double` | Skewness of trade sizes in the interval, each trade weighted equally. Buyer-initiated trades only (the buyer was the aggressor). |
| `skew_volume_sell` | `double` | Skewness of trade sizes in the interval, each trade weighted equally. Seller-initiated trades only (the seller was the aggressor). |
| `kurtosis_price` | `double` | Excess kurtosis of trade prices in the interval, each trade weighted equally. |
| `kurtosis_price_buy` | `double` | Excess kurtosis of trade prices in the interval, each trade weighted equally. Buyer-initiated trades only (the buyer was the aggressor). |
| `kurtosis_price_sell` | `double` | Excess kurtosis of trade prices in the interval, each trade weighted equally. Seller-initiated trades only (the seller was the aggressor). |
| `kurtosis_volume` | `double` | Excess kurtosis of trade sizes in the interval, each trade weighted equally. |
| `kurtosis_volume_buy` | `double` | Excess kurtosis of trade sizes in the interval, each trade weighted equally. Buyer-initiated trades only (the buyer was the aggressor). |
| `kurtosis_volume_sell` | `double` | Excess kurtosis of trade sizes in the interval, each trade weighted equally. Seller-initiated trades only (the seller was the aggressor). |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
