# LiqFlow
Interval summaries of liquidation counts, quantities, values, and directional composition.
## Availability
- **Input:** Liquidation feed
- **Markets:** Perpetual only
- **Feature family:** Liquidations
- **Coverage, Binance:** 2019-12-01 through 2026-10-01 (interval-start dates); 1,992 perp hourly files.
- **Coverage, OKX:** 2020-01-01 through 2026-10-01 (interval-start dates); 1,968 perp hourly files.
- **Coverage, Bybit:** 2020-06-01 through 2026-10-01 (interval-start dates); 1,848 perp hourly files.
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Notes
- Buy-side liquidations are forced buys that close short positions; sell-side liquidations are forced sells that close long positions.
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `liq_share` | `double` | Total liquidated quantity in the interval. |
| `liq_buy_share` | `double` | Total liquidated quantity in the interval. Buy-side liquidations only. |
| `liq_sell_share` | `double` | Total liquidated quantity in the interval. Sell-side liquidations only. |
| `liq_value` | `double` | Total liquidated value (price × quantity) in the interval. |
| `liq_buy_value` | `double` | Total liquidated value (price × quantity) in the interval. Buy-side liquidations only. |
| `liq_sell_value` | `double` | Total liquidated value (price × quantity) in the interval. Sell-side liquidations only. |
| `liq_count` | `int32` | Number of liquidation orders in the interval. |
| `liq_buy_count` | `int32` | Number of liquidation orders in the interval. Buy-side liquidations only. |
| `liq_sell_count` | `int32` | Number of liquidation orders in the interval. Sell-side liquidations only. |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
