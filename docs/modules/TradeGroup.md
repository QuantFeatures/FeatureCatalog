# TradeGroup
Trade activity summaries computed separately for small, medium, and large trades by size percentile.
## Availability
- **Input:** Exchange trades
- **Markets:** Spot and perpetual
- **Feature family:** Trade grouping
- **Coverage, Binance:** 2019-12-01 through 2026-10-01 (interval-start dates); 1,992 hourly files per market (3,984 total).
- **Coverage, OKX:** 2020-01-01 through 2026-10-01 (interval-start dates); 1,968 perp hourly files.
- **Coverage, Bybit:** 2020-06-01 through 2026-10-01 (interval-start dates); 1,848 perp hourly files.
- **Coverage, Hyperliquid:** 2024-11-01 through 2026-10-01 (interval-start dates); 576 perp hourly files.
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Notes
- Each interval's trades are split into three groups by trade size: `bot` (smallest 20%), `mid` (middle 60%), and `top` (largest 20%). Every measure is computed within its group.
- Tick direction compares a trade's price with the previous trade in the same group.
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `open_top` | `double` | First trade price in the interval. Largest 20% of the interval's trades by size. |
| `open_mid` | `double` | First trade price in the interval. Middle 60% of the interval's trades by size. |
| `open_bot` | `double` | First trade price in the interval. Smallest 20% of the interval's trades by size. |
| `high_top` | `double` | Highest trade price in the interval. Largest 20% of the interval's trades by size. |
| `high_mid` | `double` | Highest trade price in the interval. Middle 60% of the interval's trades by size. |
| `high_bot` | `double` | Highest trade price in the interval. Smallest 20% of the interval's trades by size. |
| `low_top` | `double` | Lowest trade price in the interval. Largest 20% of the interval's trades by size. |
| `low_mid` | `double` | Lowest trade price in the interval. Middle 60% of the interval's trades by size. |
| `low_bot` | `double` | Lowest trade price in the interval. Smallest 20% of the interval's trades by size. |
| `close_top` | `double` | Last trade price in the interval. Largest 20% of the interval's trades by size. |
| `close_mid` | `double` | Last trade price in the interval. Middle 60% of the interval's trades by size. |
| `close_bot` | `double` | Last trade price in the interval. Smallest 20% of the interval's trades by size. |
| `volume_top` | `double` | Total traded quantity in the interval. Largest 20% of the interval's trades by size. |
| `volume_mid` | `double` | Total traded quantity in the interval. Middle 60% of the interval's trades by size. |
| `volume_bot` | `double` | Total traded quantity in the interval. Smallest 20% of the interval's trades by size. |
| `tradeval_top` | `double` | Total traded value (sum of price × quantity). Largest 20% of the interval's trades by size. |
| `tradeval_mid` | `double` | Total traded value (sum of price × quantity). Middle 60% of the interval's trades by size. |
| `tradeval_bot` | `double` | Total traded value (sum of price × quantity). Smallest 20% of the interval's trades by size. |
| `ntrade_top` | `int32` | Number of trades in the interval. Largest 20% of the interval's trades by size. |
| `ntrade_mid` | `int32` | Number of trades in the interval. Middle 60% of the interval's trades by size. |
| `ntrade_bot` | `int32` | Number of trades in the interval. Smallest 20% of the interval's trades by size. |
| `ntrade_up_top` | `int32` | Number of up-tick trades in the interval. Largest 20% of the interval's trades by size. |
| `ntrade_up_mid` | `int32` | Number of up-tick trades in the interval. Middle 60% of the interval's trades by size. |
| `ntrade_up_bot` | `int32` | Number of up-tick trades in the interval. Smallest 20% of the interval's trades by size. |
| `ntrade_flat_top` | `int32` | Number of flat-tick trades in the interval. Largest 20% of the interval's trades by size. |
| `ntrade_flat_mid` | `int32` | Number of flat-tick trades in the interval. Middle 60% of the interval's trades by size. |
| `ntrade_flat_bot` | `int32` | Number of flat-tick trades in the interval. Smallest 20% of the interval's trades by size. |
| `ntrade_down_top` | `int32` | Number of down-tick trades in the interval. Largest 20% of the interval's trades by size. |
| `ntrade_down_mid` | `int32` | Number of down-tick trades in the interval. Middle 60% of the interval's trades by size. |
| `ntrade_down_bot` | `int32` | Number of down-tick trades in the interval. Smallest 20% of the interval's trades by size. |
| `vwap_top` | `double` | Volume-weighted average trade price. Largest 20% of the interval's trades by size. |
| `vwap_mid` | `double` | Volume-weighted average trade price. Middle 60% of the interval's trades by size. |
| `vwap_bot` | `double` | Volume-weighted average trade price. Smallest 20% of the interval's trades by size. |
| `twap_top` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Largest 20% of the interval's trades by size. |
| `twap_mid` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Middle 60% of the interval's trades by size. |
| `twap_bot` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Smallest 20% of the interval's trades by size. |
| `awap_top` | `double` | Arithmetic average trade price, each trade weighted equally. Largest 20% of the interval's trades by size. |
| `awap_mid` | `double` | Arithmetic average trade price, each trade weighted equally. Middle 60% of the interval's trades by size. |
| `awap_bot` | `double` | Arithmetic average trade price, each trade weighted equally. Smallest 20% of the interval's trades by size. |
| `open_buy_top` | `double` | First trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Largest 20% of the interval's trades by size. |
| `open_buy_mid` | `double` | First trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Middle 60% of the interval's trades by size. |
| `open_buy_bot` | `double` | First trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Smallest 20% of the interval's trades by size. |
| `high_buy_top` | `double` | Highest trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Largest 20% of the interval's trades by size. |
| `high_buy_mid` | `double` | Highest trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Middle 60% of the interval's trades by size. |
| `high_buy_bot` | `double` | Highest trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Smallest 20% of the interval's trades by size. |
| `low_buy_top` | `double` | Lowest trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Largest 20% of the interval's trades by size. |
| `low_buy_mid` | `double` | Lowest trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Middle 60% of the interval's trades by size. |
| `low_buy_bot` | `double` | Lowest trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Smallest 20% of the interval's trades by size. |
| `close_buy_top` | `double` | Last trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Largest 20% of the interval's trades by size. |
| `close_buy_mid` | `double` | Last trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Middle 60% of the interval's trades by size. |
| `close_buy_bot` | `double` | Last trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Smallest 20% of the interval's trades by size. |
| `volume_buy_top` | `double` | Total traded quantity in the interval. Buyer-initiated trades only (the buyer was the aggressor). Largest 20% of the interval's trades by size. |
| `volume_buy_mid` | `double` | Total traded quantity in the interval. Buyer-initiated trades only (the buyer was the aggressor). Middle 60% of the interval's trades by size. |
| `volume_buy_bot` | `double` | Total traded quantity in the interval. Buyer-initiated trades only (the buyer was the aggressor). Smallest 20% of the interval's trades by size. |
| `tradeval_buy_top` | `double` | Total traded value (sum of price × quantity). Buyer-initiated trades only (the buyer was the aggressor). Largest 20% of the interval's trades by size. |
| `tradeval_buy_mid` | `double` | Total traded value (sum of price × quantity). Buyer-initiated trades only (the buyer was the aggressor). Middle 60% of the interval's trades by size. |
| `tradeval_buy_bot` | `double` | Total traded value (sum of price × quantity). Buyer-initiated trades only (the buyer was the aggressor). Smallest 20% of the interval's trades by size. |
| `ntrade_buy_top` | `int32` | Number of trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Largest 20% of the interval's trades by size. |
| `ntrade_buy_mid` | `int32` | Number of trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Middle 60% of the interval's trades by size. |
| `ntrade_buy_bot` | `int32` | Number of trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Smallest 20% of the interval's trades by size. |
| `ntrade_buy_up_top` | `int32` | Number of up-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Largest 20% of the interval's trades by size. |
| `ntrade_buy_up_mid` | `int32` | Number of up-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Middle 60% of the interval's trades by size. |
| `ntrade_buy_up_bot` | `int32` | Number of up-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Smallest 20% of the interval's trades by size. |
| `ntrade_buy_flat_top` | `int32` | Number of flat-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Largest 20% of the interval's trades by size. |
| `ntrade_buy_flat_mid` | `int32` | Number of flat-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Middle 60% of the interval's trades by size. |
| `ntrade_buy_flat_bot` | `int32` | Number of flat-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Smallest 20% of the interval's trades by size. |
| `ntrade_buy_down_top` | `int32` | Number of down-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Largest 20% of the interval's trades by size. |
| `ntrade_buy_down_mid` | `int32` | Number of down-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Middle 60% of the interval's trades by size. |
| `ntrade_buy_down_bot` | `int32` | Number of down-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Smallest 20% of the interval's trades by size. |
| `vwap_buy_top` | `double` | Volume-weighted average trade price. Buyer-initiated trades only (the buyer was the aggressor). Largest 20% of the interval's trades by size. |
| `vwap_buy_mid` | `double` | Volume-weighted average trade price. Buyer-initiated trades only (the buyer was the aggressor). Middle 60% of the interval's trades by size. |
| `vwap_buy_bot` | `double` | Volume-weighted average trade price. Buyer-initiated trades only (the buyer was the aggressor). Smallest 20% of the interval's trades by size. |
| `twap_buy_top` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Buyer-initiated trades only (the buyer was the aggressor). Largest 20% of the interval's trades by size. |
| `twap_buy_mid` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Buyer-initiated trades only (the buyer was the aggressor). Middle 60% of the interval's trades by size. |
| `twap_buy_bot` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Buyer-initiated trades only (the buyer was the aggressor). Smallest 20% of the interval's trades by size. |
| `awap_buy_top` | `double` | Arithmetic average trade price, each trade weighted equally. Buyer-initiated trades only (the buyer was the aggressor). Largest 20% of the interval's trades by size. |
| `awap_buy_mid` | `double` | Arithmetic average trade price, each trade weighted equally. Buyer-initiated trades only (the buyer was the aggressor). Middle 60% of the interval's trades by size. |
| `awap_buy_bot` | `double` | Arithmetic average trade price, each trade weighted equally. Buyer-initiated trades only (the buyer was the aggressor). Smallest 20% of the interval's trades by size. |
| `open_sell_top` | `double` | First trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Largest 20% of the interval's trades by size. |
| `open_sell_mid` | `double` | First trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Middle 60% of the interval's trades by size. |
| `open_sell_bot` | `double` | First trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Smallest 20% of the interval's trades by size. |
| `high_sell_top` | `double` | Highest trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Largest 20% of the interval's trades by size. |
| `high_sell_mid` | `double` | Highest trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Middle 60% of the interval's trades by size. |
| `high_sell_bot` | `double` | Highest trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Smallest 20% of the interval's trades by size. |
| `low_sell_top` | `double` | Lowest trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Largest 20% of the interval's trades by size. |
| `low_sell_mid` | `double` | Lowest trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Middle 60% of the interval's trades by size. |
| `low_sell_bot` | `double` | Lowest trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Smallest 20% of the interval's trades by size. |
| `close_sell_top` | `double` | Last trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Largest 20% of the interval's trades by size. |
| `close_sell_mid` | `double` | Last trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Middle 60% of the interval's trades by size. |
| `close_sell_bot` | `double` | Last trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Smallest 20% of the interval's trades by size. |
| `volume_sell_top` | `double` | Total traded quantity in the interval. Seller-initiated trades only (the seller was the aggressor). Largest 20% of the interval's trades by size. |
| `volume_sell_mid` | `double` | Total traded quantity in the interval. Seller-initiated trades only (the seller was the aggressor). Middle 60% of the interval's trades by size. |
| `volume_sell_bot` | `double` | Total traded quantity in the interval. Seller-initiated trades only (the seller was the aggressor). Smallest 20% of the interval's trades by size. |
| `tradeval_sell_top` | `double` | Total traded value (sum of price × quantity). Seller-initiated trades only (the seller was the aggressor). Largest 20% of the interval's trades by size. |
| `tradeval_sell_mid` | `double` | Total traded value (sum of price × quantity). Seller-initiated trades only (the seller was the aggressor). Middle 60% of the interval's trades by size. |
| `tradeval_sell_bot` | `double` | Total traded value (sum of price × quantity). Seller-initiated trades only (the seller was the aggressor). Smallest 20% of the interval's trades by size. |
| `ntrade_sell_top` | `int32` | Number of trades in the interval. Seller-initiated trades only (the seller was the aggressor). Largest 20% of the interval's trades by size. |
| `ntrade_sell_mid` | `int32` | Number of trades in the interval. Seller-initiated trades only (the seller was the aggressor). Middle 60% of the interval's trades by size. |
| `ntrade_sell_bot` | `int32` | Number of trades in the interval. Seller-initiated trades only (the seller was the aggressor). Smallest 20% of the interval's trades by size. |
| `ntrade_sell_up_top` | `int32` | Number of up-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Largest 20% of the interval's trades by size. |
| `ntrade_sell_up_mid` | `int32` | Number of up-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Middle 60% of the interval's trades by size. |
| `ntrade_sell_up_bot` | `int32` | Number of up-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Smallest 20% of the interval's trades by size. |
| `ntrade_sell_flat_top` | `int32` | Number of flat-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Largest 20% of the interval's trades by size. |
| `ntrade_sell_flat_mid` | `int32` | Number of flat-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Middle 60% of the interval's trades by size. |
| `ntrade_sell_flat_bot` | `int32` | Number of flat-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Smallest 20% of the interval's trades by size. |
| `ntrade_sell_down_top` | `int32` | Number of down-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Largest 20% of the interval's trades by size. |
| `ntrade_sell_down_mid` | `int32` | Number of down-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Middle 60% of the interval's trades by size. |
| `ntrade_sell_down_bot` | `int32` | Number of down-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Smallest 20% of the interval's trades by size. |
| `vwap_sell_top` | `double` | Volume-weighted average trade price. Seller-initiated trades only (the seller was the aggressor). Largest 20% of the interval's trades by size. |
| `vwap_sell_mid` | `double` | Volume-weighted average trade price. Seller-initiated trades only (the seller was the aggressor). Middle 60% of the interval's trades by size. |
| `vwap_sell_bot` | `double` | Volume-weighted average trade price. Seller-initiated trades only (the seller was the aggressor). Smallest 20% of the interval's trades by size. |
| `twap_sell_top` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Seller-initiated trades only (the seller was the aggressor). Largest 20% of the interval's trades by size. |
| `twap_sell_mid` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Seller-initiated trades only (the seller was the aggressor). Middle 60% of the interval's trades by size. |
| `twap_sell_bot` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Seller-initiated trades only (the seller was the aggressor). Smallest 20% of the interval's trades by size. |
| `awap_sell_top` | `double` | Arithmetic average trade price, each trade weighted equally. Seller-initiated trades only (the seller was the aggressor). Largest 20% of the interval's trades by size. |
| `awap_sell_mid` | `double` | Arithmetic average trade price, each trade weighted equally. Seller-initiated trades only (the seller was the aggressor). Middle 60% of the interval's trades by size. |
| `awap_sell_bot` | `double` | Arithmetic average trade price, each trade weighted equally. Seller-initiated trades only (the seller was the aggressor). Smallest 20% of the interval's trades by size. |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
