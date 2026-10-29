# OpenIntGradient
Mark price summaries and the distribution of relative changes in reported perpetual open interest.
## Availability
- **Input:** Derivative ticker feed
- **Markets:** Perpetual only
- **Feature family:** Open-interest dynamics
- **Coverage, Binance:** 2019-12-01 through 2026-10-01 (interval-start dates); 1,992 perp hourly files.
- **Coverage, OKX:** 2020-01-01 through 2026-10-01 (interval-start dates); 1,968 perp hourly files.
- **Coverage, Bybit:** 2020-06-01 through 2026-10-01 (interval-start dates); 1,848 perp hourly files.
- **Coverage, Hyperliquid:** 2024-11-01 through 2026-10-01 (interval-start dates); 576 perp hourly files.
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Notes
- `markprice_` features summarize the mark price reported with open interest. `change_` features summarize relative changes in open interest between updates. `_up` and `_down` features use only the updates in which open interest rose or fell.
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
| `markprice_open` | `double` | First mark price in the interval. |
| `markprice_high` | `double` | Highest mark price in the interval. |
| `markprice_low` | `double` | Lowest mark price in the interval. |
| `markprice_close` | `double` | Last mark price in the interval. |
| `markprice_twa` | `double` | Time-weighted average mark price over the interval. |
| `markprice_awa` | `double` | Average mark price across updates, each update weighted equally. |
| `change_sum` | `double` | Sum of relative changes in open interest (as fractions) between updates in the interval. |
| `change_mean` | `double` | Average of relative changes in open interest (as fractions) between updates in the interval. |
| `change_std` | `double` | Standard deviation of relative changes in open interest (as fractions) between updates in the interval. |
| `change_skew` | `double` | Skewness of relative changes in open interest (as fractions) between updates in the interval. |
| `change_kurtosis` | `double` | Excess kurtosis of relative changes in open interest (as fractions) between updates in the interval. |
| `markprice_open_up` | `double` | First mark price in the interval. Updates in which the open interest rose only. |
| `markprice_high_up` | `double` | Highest mark price in the interval. Updates in which the open interest rose only. |
| `markprice_low_up` | `double` | Lowest mark price in the interval. Updates in which the open interest rose only. |
| `markprice_close_up` | `double` | Last mark price in the interval. Updates in which the open interest rose only. |
| `markprice_twa_up` | `double` | Time-weighted average mark price over the interval. Updates in which the open interest rose only. |
| `markprice_awa_up` | `double` | Average mark price across updates, each update weighted equally. Updates in which the open interest rose only. |
| `change_sum_up` | `double` | Sum of relative changes in open interest (as fractions) between updates in the interval. Updates in which the open interest rose only. |
| `change_mean_up` | `double` | Average of relative changes in open interest (as fractions) between updates in the interval. Updates in which the open interest rose only. |
| `change_std_up` | `double` | Standard deviation of relative changes in open interest (as fractions) between updates in the interval. Updates in which the open interest rose only. |
| `change_skew_up` | `double` | Skewness of relative changes in open interest (as fractions) between updates in the interval. Updates in which the open interest rose only. |
| `change_kurtosis_up` | `double` | Excess kurtosis of relative changes in open interest (as fractions) between updates in the interval. Updates in which the open interest rose only. |
| `markprice_open_down` | `double` | First mark price in the interval. Updates in which the open interest fell only. |
| `markprice_high_down` | `double` | Highest mark price in the interval. Updates in which the open interest fell only. |
| `markprice_low_down` | `double` | Lowest mark price in the interval. Updates in which the open interest fell only. |
| `markprice_close_down` | `double` | Last mark price in the interval. Updates in which the open interest fell only. |
| `markprice_twa_down` | `double` | Time-weighted average mark price over the interval. Updates in which the open interest fell only. |
| `markprice_awa_down` | `double` | Average mark price across updates, each update weighted equally. Updates in which the open interest fell only. |
| `change_sum_down` | `double` | Sum of relative changes in open interest (as fractions) between updates in the interval. Updates in which the open interest fell only. |
| `change_mean_down` | `double` | Average of relative changes in open interest (as fractions) between updates in the interval. Updates in which the open interest fell only. |
| `change_std_down` | `double` | Standard deviation of relative changes in open interest (as fractions) between updates in the interval. Updates in which the open interest fell only. |
| `change_skew_down` | `double` | Skewness of relative changes in open interest (as fractions) between updates in the interval. Updates in which the open interest fell only. |
| `change_kurtosis_down` | `double` | Excess kurtosis of relative changes in open interest (as fractions) between updates in the interval. Updates in which the open interest fell only. |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
