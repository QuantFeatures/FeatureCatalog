# FundingRate
Interval summaries of the reported perpetual funding rate and its changes.
## Availability
- **Input:** Derivative ticker feed
- **Markets:** Perpetual only
- **Feature family:** Funding
- **Coverage, Binance:** 2019-12-01 through 2026-10-01 (interval-start dates); 1,992 perp hourly files.
- **Coverage, OKX:** 2020-01-01 through 2026-10-01 (interval-start dates); 1,968 perp hourly files.
- **Coverage, Bybit:** 2020-06-01 through 2026-10-01 (interval-start dates); 1,848 perp hourly files.
- **Coverage, Hyperliquid:** 2024-11-01 through 2026-10-01 (interval-start dates); 576 perp hourly files.
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Notes
- Values are the funding rate as reported by the exchange. An update is a change in the reported value; `_up` and `_down` features use only the updates in which it rose or fell.
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `open` | `double` | First funding rate in the interval. |
| `high` | `double` | Highest funding rate in the interval. |
| `low` | `double` | Lowest funding rate in the interval. |
| `close` | `double` | Last funding rate in the interval. |
| `twa` | `double` | Time-weighted average funding rate over the interval. |
| `awa` | `double` | Average funding rate across updates, each update weighted equally. |
| `num` | `int32` | Number of updates in which the funding rate changed. |
| `num_up` | `int32` | Number of updates in which the funding rate rose. |
| `num_down` | `int32` | Number of updates in which the funding rate fell. |
| `open_up` | `double` | First funding rate in the interval. Updates in which the funding rate rose only. |
| `high_up` | `double` | Highest funding rate in the interval. Updates in which the funding rate rose only. |
| `low_up` | `double` | Lowest funding rate in the interval. Updates in which the funding rate rose only. |
| `close_up` | `double` | Last funding rate in the interval. Updates in which the funding rate rose only. |
| `twa_up` | `double` | Time-weighted average funding rate over the interval. Updates in which the funding rate rose only. |
| `awa_up` | `double` | Average funding rate across updates, each update weighted equally. Updates in which the funding rate rose only. |
| `change_sum_up` | `double` | Sum of changes in funding rate between updates in the interval. Updates in which the funding rate rose only. |
| `change_mean_up` | `double` | Average of changes in funding rate between updates in the interval. Updates in which the funding rate rose only. |
| `change_std_up` | `double` | Standard deviation of changes in funding rate between updates in the interval. Updates in which the funding rate rose only. |
| `open_down` | `double` | First funding rate in the interval. Updates in which the funding rate fell only. |
| `high_down` | `double` | Highest funding rate in the interval. Updates in which the funding rate fell only. |
| `low_down` | `double` | Lowest funding rate in the interval. Updates in which the funding rate fell only. |
| `close_down` | `double` | Last funding rate in the interval. Updates in which the funding rate fell only. |
| `twa_down` | `double` | Time-weighted average funding rate over the interval. Updates in which the funding rate fell only. |
| `awa_down` | `double` | Average funding rate across updates, each update weighted equally. Updates in which the funding rate fell only. |
| `change_sum_down` | `double` | Sum of changes in funding rate between updates in the interval. Updates in which the funding rate fell only. |
| `change_mean_down` | `double` | Average of changes in funding rate between updates in the interval. Updates in which the funding rate fell only. |
| `change_std_down` | `double` | Standard deviation of changes in funding rate between updates in the interval. Updates in which the funding rate fell only. |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
