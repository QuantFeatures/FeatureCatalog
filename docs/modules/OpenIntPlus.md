# OpenIntPlus
Interval summaries of perpetual open interest value (open interest × mark price) and the distribution of its changes.
## Availability
- **Input:** Derivative ticker feed
- **Markets:** Perpetual only
- **Feature family:** Extended open interest
- **Coverage, Binance:** 2019-12-01 through 2026-10-01 (interval-start dates); 1,992 perp hourly files.
- **Coverage, OKX:** 2020-01-01 through 2026-10-01 (interval-start dates); 1,968 perp hourly files.
- **Coverage, Bybit:** 2020-06-01 through 2026-10-01 (interval-start dates); 1,848 perp hourly files.
- **Coverage, Hyperliquid:** 2024-11-01 through 2026-10-01 (interval-start dates); 576 perp hourly files.
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Notes
- Values are open interest value: open interest × mark price, in the quote asset. An update is a change in open interest or mark price; `_up` and `_down` features use only the updates in which the value rose or fell.
- Kurtosis is sample-adjusted excess kurtosis: 0 for a normal distribution.
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `open` | `double` | First open interest value in the interval. |
| `high` | `double` | Highest open interest value in the interval. |
| `low` | `double` | Lowest open interest value in the interval. |
| `close` | `double` | Last open interest value in the interval. |
| `twa` | `double` | Time-weighted average open interest value over the interval. |
| `awa` | `double` | Average open interest value across updates, each update weighted equally. |
| `change_sum` | `double` | Sum of changes in open interest value between updates in the interval. |
| `change_mean` | `double` | Average of changes in open interest value between updates in the interval. |
| `change_std` | `double` | Standard deviation of changes in open interest value between updates in the interval. |
| `change_skew` | `double` | Skewness of changes in open interest value between updates in the interval. |
| `change_kurtosis` | `double` | Excess kurtosis of changes in open interest value between updates in the interval. |
| `num` | `int32` | Number of updates in which the open interest value changed. |
| `num_up` | `int32` | Number of updates in which the open interest value rose. |
| `num_down` | `int32` | Number of updates in which the open interest value fell. |
| `change_abs_std` | `double` | Standard deviation of absolute changes in open interest value between updates in the interval. |
| `change_abs_skew` | `double` | Skewness of absolute changes in open interest value between updates in the interval. |
| `change_abs_kurtosis` | `double` | Excess kurtosis of absolute changes in open interest value between updates in the interval. |
| `open_up` | `double` | First open interest value in the interval. Updates in which the open interest value rose only. |
| `high_up` | `double` | Highest open interest value in the interval. Updates in which the open interest value rose only. |
| `low_up` | `double` | Lowest open interest value in the interval. Updates in which the open interest value rose only. |
| `close_up` | `double` | Last open interest value in the interval. Updates in which the open interest value rose only. |
| `twa_up` | `double` | Time-weighted average open interest value over the interval. Updates in which the open interest value rose only. |
| `awa_up` | `double` | Average open interest value across updates, each update weighted equally. Updates in which the open interest value rose only. |
| `change_sum_up` | `double` | Sum of changes in open interest value between updates in the interval. Updates in which the open interest value rose only. |
| `change_mean_up` | `double` | Average of changes in open interest value between updates in the interval. Updates in which the open interest value rose only. |
| `change_std_up` | `double` | Standard deviation of changes in open interest value between updates in the interval. Updates in which the open interest value rose only. |
| `change_skew_up` | `double` | Skewness of changes in open interest value between updates in the interval. Updates in which the open interest value rose only. |
| `change_kurtosis_up` | `double` | Excess kurtosis of changes in open interest value between updates in the interval. Updates in which the open interest value rose only. |
| `open_down` | `double` | First open interest value in the interval. Updates in which the open interest value fell only. |
| `high_down` | `double` | Highest open interest value in the interval. Updates in which the open interest value fell only. |
| `low_down` | `double` | Lowest open interest value in the interval. Updates in which the open interest value fell only. |
| `close_down` | `double` | Last open interest value in the interval. Updates in which the open interest value fell only. |
| `twa_down` | `double` | Time-weighted average open interest value over the interval. Updates in which the open interest value fell only. |
| `awa_down` | `double` | Average open interest value across updates, each update weighted equally. Updates in which the open interest value fell only. |
| `change_sum_down` | `double` | Sum of changes in open interest value between updates in the interval. Updates in which the open interest value fell only. |
| `change_mean_down` | `double` | Average of changes in open interest value between updates in the interval. Updates in which the open interest value fell only. |
| `change_std_down` | `double` | Standard deviation of changes in open interest value between updates in the interval. Updates in which the open interest value fell only. |
| `change_skew_down` | `double` | Skewness of changes in open interest value between updates in the interval. Updates in which the open interest value fell only. |
| `change_kurtosis_down` | `double` | Excess kurtosis of changes in open interest value between updates in the interval. Updates in which the open interest value fell only. |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
