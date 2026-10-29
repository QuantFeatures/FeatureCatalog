# TradeLarge
Trade activity summaries for unusually large trades (one and two standard deviations above the mean trade size) and for all other trades.
## Availability
- **Input:** Exchange trades
- **Markets:** Spot and perpetual
- **Feature family:** Trade tails
- **Coverage, Binance:** 2019-12-01 through 2026-10-01 (interval-start dates); 1,992 hourly files per market (3,984 total).
- **Coverage, OKX:** 2020-01-01 through 2026-10-01 (interval-start dates); 1,968 perp hourly files.
- **Coverage, Bybit:** 2020-06-01 through 2026-10-01 (interval-start dates); 1,848 perp hourly files.
- **Coverage, Hyperliquid:** 2024-11-01 through 2026-10-01 (interval-start dates); 576 perp hourly files.
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Notes
- `1sigma`: trades at least one standard deviation larger than the interval's mean trade size. `2sigma`: trades at least two standard deviations larger (a subset of `1sigma`). `rest`: all other trades. Every measure is computed within its group.
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `open_1sigma` | `double` | First trade price in the interval. Trades at least one standard deviation larger than the interval's mean trade size. |
| `open_2sigma` | `double` | First trade price in the interval. Trades at least two standard deviations larger than the interval's mean trade size. |
| `open_rest` | `double` | First trade price in the interval. Trades less than one standard deviation larger than the interval's mean trade size. |
| `high_1sigma` | `double` | Highest trade price in the interval. Trades at least one standard deviation larger than the interval's mean trade size. |
| `high_2sigma` | `double` | Highest trade price in the interval. Trades at least two standard deviations larger than the interval's mean trade size. |
| `high_rest` | `double` | Highest trade price in the interval. Trades less than one standard deviation larger than the interval's mean trade size. |
| `low_1sigma` | `double` | Lowest trade price in the interval. Trades at least one standard deviation larger than the interval's mean trade size. |
| `low_2sigma` | `double` | Lowest trade price in the interval. Trades at least two standard deviations larger than the interval's mean trade size. |
| `low_rest` | `double` | Lowest trade price in the interval. Trades less than one standard deviation larger than the interval's mean trade size. |
| `close_1sigma` | `double` | Last trade price in the interval. Trades at least one standard deviation larger than the interval's mean trade size. |
| `close_2sigma` | `double` | Last trade price in the interval. Trades at least two standard deviations larger than the interval's mean trade size. |
| `close_rest` | `double` | Last trade price in the interval. Trades less than one standard deviation larger than the interval's mean trade size. |
| `volume_1sigma` | `double` | Total traded quantity in the interval. Trades at least one standard deviation larger than the interval's mean trade size. |
| `volume_2sigma` | `double` | Total traded quantity in the interval. Trades at least two standard deviations larger than the interval's mean trade size. |
| `volume_rest` | `double` | Total traded quantity in the interval. Trades less than one standard deviation larger than the interval's mean trade size. |
| `tradeval_1sigma` | `double` | Total traded value (sum of price × quantity). Trades at least one standard deviation larger than the interval's mean trade size. |
| `tradeval_2sigma` | `double` | Total traded value (sum of price × quantity). Trades at least two standard deviations larger than the interval's mean trade size. |
| `tradeval_rest` | `double` | Total traded value (sum of price × quantity). Trades less than one standard deviation larger than the interval's mean trade size. |
| `ntrade_1sigma` | `int32` | Number of trades in the interval. Trades at least one standard deviation larger than the interval's mean trade size. |
| `ntrade_2sigma` | `int32` | Number of trades in the interval. Trades at least two standard deviations larger than the interval's mean trade size. |
| `ntrade_rest` | `int32` | Number of trades in the interval. Trades less than one standard deviation larger than the interval's mean trade size. |
| `ntrade_up_1sigma` | `int32` | Number of up-tick trades in the interval. Trades at least one standard deviation larger than the interval's mean trade size. |
| `ntrade_up_2sigma` | `int32` | Number of up-tick trades in the interval. Trades at least two standard deviations larger than the interval's mean trade size. |
| `ntrade_up_rest` | `int32` | Number of up-tick trades in the interval. Trades less than one standard deviation larger than the interval's mean trade size. |
| `ntrade_flat_1sigma` | `int32` | Number of flat-tick trades in the interval. Trades at least one standard deviation larger than the interval's mean trade size. |
| `ntrade_flat_2sigma` | `int32` | Number of flat-tick trades in the interval. Trades at least two standard deviations larger than the interval's mean trade size. |
| `ntrade_flat_rest` | `int32` | Number of flat-tick trades in the interval. Trades less than one standard deviation larger than the interval's mean trade size. |
| `ntrade_down_1sigma` | `int32` | Number of down-tick trades in the interval. Trades at least one standard deviation larger than the interval's mean trade size. |
| `ntrade_down_2sigma` | `int32` | Number of down-tick trades in the interval. Trades at least two standard deviations larger than the interval's mean trade size. |
| `ntrade_down_rest` | `int32` | Number of down-tick trades in the interval. Trades less than one standard deviation larger than the interval's mean trade size. |
| `vwap_1sigma` | `double` | Volume-weighted average trade price. Trades at least one standard deviation larger than the interval's mean trade size. |
| `vwap_2sigma` | `double` | Volume-weighted average trade price. Trades at least two standard deviations larger than the interval's mean trade size. |
| `vwap_rest` | `double` | Volume-weighted average trade price. Trades less than one standard deviation larger than the interval's mean trade size. |
| `twap_1sigma` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Trades at least one standard deviation larger than the interval's mean trade size. |
| `twap_2sigma` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Trades at least two standard deviations larger than the interval's mean trade size. |
| `twap_rest` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Trades less than one standard deviation larger than the interval's mean trade size. |
| `awap_1sigma` | `double` | Arithmetic average trade price, each trade weighted equally. Trades at least one standard deviation larger than the interval's mean trade size. |
| `awap_2sigma` | `double` | Arithmetic average trade price, each trade weighted equally. Trades at least two standard deviations larger than the interval's mean trade size. |
| `awap_rest` | `double` | Arithmetic average trade price, each trade weighted equally. Trades less than one standard deviation larger than the interval's mean trade size. |
| `open_buy_1sigma` | `double` | First trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `open_buy_2sigma` | `double` | First trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `open_buy_rest` | `double` | First trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `high_buy_1sigma` | `double` | Highest trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `high_buy_2sigma` | `double` | Highest trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `high_buy_rest` | `double` | Highest trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `low_buy_1sigma` | `double` | Lowest trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `low_buy_2sigma` | `double` | Lowest trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `low_buy_rest` | `double` | Lowest trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `close_buy_1sigma` | `double` | Last trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `close_buy_2sigma` | `double` | Last trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `close_buy_rest` | `double` | Last trade price in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `volume_buy_1sigma` | `double` | Total traded quantity in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `volume_buy_2sigma` | `double` | Total traded quantity in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `volume_buy_rest` | `double` | Total traded quantity in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `tradeval_buy_1sigma` | `double` | Total traded value (sum of price × quantity). Buyer-initiated trades only (the buyer was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `tradeval_buy_2sigma` | `double` | Total traded value (sum of price × quantity). Buyer-initiated trades only (the buyer was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `tradeval_buy_rest` | `double` | Total traded value (sum of price × quantity). Buyer-initiated trades only (the buyer was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `ntrade_buy_1sigma` | `int32` | Number of trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `ntrade_buy_2sigma` | `int32` | Number of trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `ntrade_buy_rest` | `int32` | Number of trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `ntrade_buy_up_1sigma` | `int32` | Number of up-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `ntrade_buy_up_2sigma` | `int32` | Number of up-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `ntrade_buy_up_rest` | `int32` | Number of up-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `ntrade_buy_flat_1sigma` | `int32` | Number of flat-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `ntrade_buy_flat_2sigma` | `int32` | Number of flat-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `ntrade_buy_flat_rest` | `int32` | Number of flat-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `ntrade_buy_down_1sigma` | `int32` | Number of down-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `ntrade_buy_down_2sigma` | `int32` | Number of down-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `ntrade_buy_down_rest` | `int32` | Number of down-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `vwap_buy_1sigma` | `double` | Volume-weighted average trade price. Buyer-initiated trades only (the buyer was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `vwap_buy_2sigma` | `double` | Volume-weighted average trade price. Buyer-initiated trades only (the buyer was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `vwap_buy_rest` | `double` | Volume-weighted average trade price. Buyer-initiated trades only (the buyer was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `twap_buy_1sigma` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Buyer-initiated trades only (the buyer was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `twap_buy_2sigma` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Buyer-initiated trades only (the buyer was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `twap_buy_rest` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Buyer-initiated trades only (the buyer was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `awap_buy_1sigma` | `double` | Arithmetic average trade price, each trade weighted equally. Buyer-initiated trades only (the buyer was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `awap_buy_2sigma` | `double` | Arithmetic average trade price, each trade weighted equally. Buyer-initiated trades only (the buyer was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `awap_buy_rest` | `double` | Arithmetic average trade price, each trade weighted equally. Buyer-initiated trades only (the buyer was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `open_sell_1sigma` | `double` | First trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `open_sell_2sigma` | `double` | First trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `open_sell_rest` | `double` | First trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `high_sell_1sigma` | `double` | Highest trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `high_sell_2sigma` | `double` | Highest trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `high_sell_rest` | `double` | Highest trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `low_sell_1sigma` | `double` | Lowest trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `low_sell_2sigma` | `double` | Lowest trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `low_sell_rest` | `double` | Lowest trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `close_sell_1sigma` | `double` | Last trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `close_sell_2sigma` | `double` | Last trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `close_sell_rest` | `double` | Last trade price in the interval. Seller-initiated trades only (the seller was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `volume_sell_1sigma` | `double` | Total traded quantity in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `volume_sell_2sigma` | `double` | Total traded quantity in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `volume_sell_rest` | `double` | Total traded quantity in the interval. Seller-initiated trades only (the seller was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `tradeval_sell_1sigma` | `double` | Total traded value (sum of price × quantity). Seller-initiated trades only (the seller was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `tradeval_sell_2sigma` | `double` | Total traded value (sum of price × quantity). Seller-initiated trades only (the seller was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `tradeval_sell_rest` | `double` | Total traded value (sum of price × quantity). Seller-initiated trades only (the seller was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `ntrade_sell_1sigma` | `int32` | Number of trades in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `ntrade_sell_2sigma` | `int32` | Number of trades in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `ntrade_sell_rest` | `int32` | Number of trades in the interval. Seller-initiated trades only (the seller was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `ntrade_sell_up_1sigma` | `int32` | Number of up-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `ntrade_sell_up_2sigma` | `int32` | Number of up-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `ntrade_sell_up_rest` | `int32` | Number of up-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `ntrade_sell_flat_1sigma` | `int32` | Number of flat-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `ntrade_sell_flat_2sigma` | `int32` | Number of flat-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `ntrade_sell_flat_rest` | `int32` | Number of flat-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `ntrade_sell_down_1sigma` | `int32` | Number of down-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `ntrade_sell_down_2sigma` | `int32` | Number of down-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `ntrade_sell_down_rest` | `int32` | Number of down-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `vwap_sell_1sigma` | `double` | Volume-weighted average trade price. Seller-initiated trades only (the seller was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `vwap_sell_2sigma` | `double` | Volume-weighted average trade price. Seller-initiated trades only (the seller was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `vwap_sell_rest` | `double` | Volume-weighted average trade price. Seller-initiated trades only (the seller was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `twap_sell_1sigma` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Seller-initiated trades only (the seller was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `twap_sell_2sigma` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Seller-initiated trades only (the seller was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `twap_sell_rest` | `double` | Time-weighted average trade price: each price weighted by how long it stood as the last trade price. Seller-initiated trades only (the seller was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |
| `awap_sell_1sigma` | `double` | Arithmetic average trade price, each trade weighted equally. Seller-initiated trades only (the seller was the aggressor). Trades at least one standard deviation larger than the interval's mean trade size. |
| `awap_sell_2sigma` | `double` | Arithmetic average trade price, each trade weighted equally. Seller-initiated trades only (the seller was the aggressor). Trades at least two standard deviations larger than the interval's mean trade size. |
| `awap_sell_rest` | `double` | Arithmetic average trade price, each trade weighted equally. Seller-initiated trades only (the seller was the aggressor). Trades less than one standard deviation larger than the interval's mean trade size. |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
