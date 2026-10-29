# TradeFlow
Interval summaries of prices, executed volume, trade counts, and buyer- and seller-initiated activity.
## Availability
- **Input:** Exchange trades
- **Markets:** Spot and perpetual
- **Feature family:** Trade activity
- **Coverage, Binance:** 2019-12-01 through 2026-10-01 (interval-start dates); 1,992 hourly files per market (3,984 total).
- **Coverage, OKX:** 2020-01-01 through 2026-10-01 (interval-start dates); 1,968 perp hourly files.
- **Coverage, Bybit:** 2020-06-01 through 2026-10-01 (interval-start dates); 1,848 perp hourly files.
- **Coverage, Hyperliquid:** 2024-11-01 through 2026-10-01 (interval-start dates); 576 perp hourly files.
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Notes
- Buyer- and seller-initiated trades are identified by the aggressor side reported by the exchange.
- Tick direction compares a trade's price with the previous trade; for `_buy` and `_sell` features, with the previous trade on the same side.
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `open` | `double` | First trade price in the interval. |
| `high` | `double` | Highest trade price in the interval. |
| `low` | `double` | Lowest trade price in the interval. |
| `close` | `double` | Last trade price in the interval. |
| `volume` | `double` | Total traded quantity in the interval. |
| `tradeval` | `double` | Total traded value (sum of price × quantity). |
| `ntrade` | `int32` | Number of trades in the interval. |
| `vwap` | `double` | Volume-weighted average trade price. |
| `twap` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. |
| `awap` | `double` | Arithmetic average trade price, each trade weighted equally. |
| `ntrade_up` | `int32` | Number of up-tick trades in the interval. |
| `ntrade_down` | `int32` | Number of down-tick trades in the interval. |
| `ntrade_flat` | `int32` | Number of flat-tick trades in the interval. |
| `open_buy` | `double` | First trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `high_buy` | `double` | Highest trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `low_buy` | `double` | Lowest trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `close_buy` | `double` | Last trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `volume_buy` | `double` | Total traded quantity in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `tradeval_buy` | `double` | Total traded value (sum of price × quantity). Buyer-initiated trades only (the buyer was the aggressor). |
| `ntrade_buy` | `int32` | Number of trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `vwap_buy` | `double` | Volume-weighted average trade price. Buyer-initiated trades only (the buyer was the aggressor). |
| `twap_buy` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Buyer-initiated trades only (the buyer was the aggressor). |
| `awap_buy` | `double` | Arithmetic average trade price, each trade weighted equally. Buyer-initiated trades only (the buyer was the aggressor). |
| `ntrade_up_buy` | `int32` | Number of up-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `ntrade_down_buy` | `int32` | Number of down-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `ntrade_flat_buy` | `int32` | Number of flat-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `open_sell` | `double` | First trade price in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `high_sell` | `double` | Highest trade price in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `low_sell` | `double` | Lowest trade price in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `close_sell` | `double` | Last trade price in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `volume_sell` | `double` | Total traded quantity in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `tradeval_sell` | `double` | Total traded value (sum of price × quantity). Seller-initiated trades only (the seller was the aggressor). |
| `ntrade_sell` | `int32` | Number of trades in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `vwap_sell` | `double` | Volume-weighted average trade price. Seller-initiated trades only (the seller was the aggressor). |
| `twap_sell` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Seller-initiated trades only (the seller was the aggressor). |
| `awap_sell` | `double` | Arithmetic average trade price, each trade weighted equally. Seller-initiated trades only (the seller was the aggressor). |
| `ntrade_up_sell` | `int32` | Number of up-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `ntrade_down_sell` | `int32` | Number of down-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `ntrade_flat_sell` | `int32` | Number of flat-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
