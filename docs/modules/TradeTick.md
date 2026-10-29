# TradeTick
Trade counts, quantity, and value split by tick direction (up, down, flat), overall and by buyer- or seller-initiated side.
## Availability
- **Input:** Exchange trades
- **Markets:** Spot and perpetual
- **Feature family:** Extended trade activity
- **Coverage, Binance:** 2019-12-01 through 2026-10-01 (interval-start dates); 1,992 hourly files per market (3,984 total).
- **Coverage, OKX:** 2020-01-01 through 2026-10-01 (interval-start dates); 1,968 perp hourly files.
- **Coverage, Bybit:** 2020-06-01 through 2026-10-01 (interval-start dates); 1,848 perp hourly files.
- **Coverage, Hyperliquid:** 2024-11-01 through 2026-10-01 (interval-start dates); 576 perp hourly files.
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Notes
- Tick direction compares a trade's price with the previous trade of either side, including for buyer- and seller-initiated features.
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `ntrade_price_down` | `int32` | Number of down-tick trades in the interval. |
| `ntrade_price_flat` | `int32` | Number of flat-tick trades in the interval. |
| `ntrade_price_up` | `int32` | Number of up-tick trades in the interval. |
| `ntrade_buy_price_down` | `int32` | Number of down-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `ntrade_buy_price_flat` | `int32` | Number of flat-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `ntrade_buy_price_up` | `int32` | Number of up-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `ntrade_sell_price_down` | `int32` | Number of down-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `ntrade_sell_price_flat` | `int32` | Number of flat-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `ntrade_sell_price_up` | `int32` | Number of up-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `volume_price_flat` | `double` | Traded quantity of flat-tick trades in the interval. |
| `volume_price_up` | `double` | Traded quantity of up-tick trades in the interval. |
| `volume_price_down` | `double` | Traded quantity of down-tick trades in the interval. |
| `tradeval_price_flat` | `double` | Traded value (sum of price × quantity) of flat-tick trades in the interval. |
| `tradeval_price_up` | `double` | Traded value (sum of price × quantity) of up-tick trades in the interval. |
| `tradeval_price_down` | `double` | Traded value (sum of price × quantity) of down-tick trades in the interval. |
| `volume_buy_price_flat` | `double` | Traded quantity of flat-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `volume_buy_price_up` | `double` | Traded quantity of up-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `volume_buy_price_down` | `double` | Traded quantity of down-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `tradeval_buy_price_flat` | `double` | Traded value (sum of price × quantity) of flat-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `tradeval_buy_price_up` | `double` | Traded value (sum of price × quantity) of up-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `tradeval_buy_price_down` | `double` | Traded value (sum of price × quantity) of down-tick trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `volume_sell_price_flat` | `double` | Traded quantity of flat-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `volume_sell_price_up` | `double` | Traded quantity of up-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `volume_sell_price_down` | `double` | Traded quantity of down-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `tradeval_sell_price_flat` | `double` | Traded value (sum of price × quantity) of flat-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `tradeval_sell_price_up` | `double` | Traded value (sum of price × quantity) of up-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `tradeval_sell_price_down` | `double` | Traded value (sum of price × quantity) of down-tick trades in the interval. Seller-initiated trades only (the seller was the aggressor). |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
