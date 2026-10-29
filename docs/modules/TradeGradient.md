# TradeGradient
Average trade-to-trade price changes by side, and runs of consecutive same-side trades.
## Availability
- **Input:** Exchange trades
- **Markets:** Spot and perpetual
- **Feature family:** Trade dynamics
- **Coverage, Binance:** 2019-12-01 through 2026-10-01 (interval-start dates); 1,992 hourly files per market (3,984 total).
- **Coverage, OKX:** 2020-01-01 through 2026-10-01 (interval-start dates); 1,968 perp hourly files.
- **Coverage, Bybit:** 2020-06-01 through 2026-10-01 (interval-start dates); 1,848 perp hourly files.
- **Coverage, Hyperliquid:** 2024-11-01 through 2026-10-01 (interval-start dates); 576 perp hourly files.
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Notes
- Price change is a trade's price minus the previous trade's price, of either side.
- A run is a sequence of consecutive trades on the same side. Maximum count, quantity, and value are taken independently and can come from different runs.
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `awa_buy_change` | `double` | Average price change of buyer-initiated trades, each trade weighted equally. |
| `vwa_buy_change` | `double` | Average price change of buyer-initiated trades, weighted by trade size. |
| `awa_buy_change_up` | `double` | Average price change of buyer-initiated trades, each trade weighted equally. Up-tick trades only. |
| `vwa_buy_change_up` | `double` | Average price change of buyer-initiated trades, weighted by trade size. Up-tick trades only. |
| `awa_buy_change_down` | `double` | Average price change of buyer-initiated trades, each trade weighted equally. Down-tick trades only. |
| `vwa_buy_change_down` | `double` | Average price change of buyer-initiated trades, weighted by trade size. Down-tick trades only. |
| `awa_sell_change` | `double` | Average price change of seller-initiated trades, each trade weighted equally. |
| `vwa_sell_change` | `double` | Average price change of seller-initiated trades, weighted by trade size. |
| `awa_sell_change_up` | `double` | Average price change of seller-initiated trades, each trade weighted equally. Up-tick trades only. |
| `vwa_sell_change_up` | `double` | Average price change of seller-initiated trades, weighted by trade size. Up-tick trades only. |
| `awa_sell_change_down` | `double` | Average price change of seller-initiated trades, each trade weighted equally. Down-tick trades only. |
| `vwa_sell_change_down` | `double` | Average price change of seller-initiated trades, weighted by trade size. Down-tick trades only. |
| `awa_buy_changebps` | `double` | Average price change of buyer-initiated trades, each trade weighted equally, in basis points of the previous price. |
| `vwa_buy_changebps` | `double` | Average price change of buyer-initiated trades, weighted by trade size, in basis points of the previous price. |
| `awa_buy_changebps_up` | `double` | Average price change of buyer-initiated trades, each trade weighted equally, in basis points of the previous price. Up-tick trades only. |
| `vwa_buy_changebps_up` | `double` | Average price change of buyer-initiated trades, weighted by trade size, in basis points of the previous price. Up-tick trades only. |
| `awa_buy_changebps_down` | `double` | Average price change of buyer-initiated trades, each trade weighted equally, in basis points of the previous price. Down-tick trades only. |
| `vwa_buy_changebps_down` | `double` | Average price change of buyer-initiated trades, weighted by trade size, in basis points of the previous price. Down-tick trades only. |
| `awa_sell_changebps` | `double` | Average price change of seller-initiated trades, each trade weighted equally, in basis points of the previous price. |
| `vwa_sell_changebps` | `double` | Average price change of seller-initiated trades, weighted by trade size, in basis points of the previous price. |
| `awa_sell_changebps_up` | `double` | Average price change of seller-initiated trades, each trade weighted equally, in basis points of the previous price. Up-tick trades only. |
| `vwa_sell_changebps_up` | `double` | Average price change of seller-initiated trades, weighted by trade size, in basis points of the previous price. Up-tick trades only. |
| `awa_sell_changebps_down` | `double` | Average price change of seller-initiated trades, each trade weighted equally, in basis points of the previous price. Down-tick trades only. |
| `vwa_sell_changebps_down` | `double` | Average price change of seller-initiated trades, weighted by trade size, in basis points of the previous price. Down-tick trades only. |
| `cont_buy_max_count` | `int32` | Largest number of trades in a run of consecutive buyer-initiated trades. |
| `cont_buy_avg_count` | `double` | Average number of trades in a run of consecutive buyer-initiated trades. |
| `cont_buy_max_size` | `double` | Largest traded quantity in a run of consecutive buyer-initiated trades. |
| `cont_buy_avg_size` | `double` | Average traded quantity in a run of consecutive buyer-initiated trades. |
| `cont_buy_max_value` | `double` | Largest traded value in a run of consecutive buyer-initiated trades. |
| `cont_buy_avg_value` | `double` | Average traded value in a run of consecutive buyer-initiated trades. |
| `cont_sell_max_count` | `int32` | Largest number of trades in a run of consecutive seller-initiated trades. |
| `cont_sell_avg_count` | `double` | Average number of trades in a run of consecutive seller-initiated trades. |
| `cont_sell_max_size` | `double` | Largest traded quantity in a run of consecutive seller-initiated trades. |
| `cont_sell_avg_size` | `double` | Average traded quantity in a run of consecutive seller-initiated trades. |
| `cont_sell_max_value` | `double` | Largest traded value in a run of consecutive seller-initiated trades. |
| `cont_sell_avg_value` | `double` | Average traded value in a run of consecutive seller-initiated trades. |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
