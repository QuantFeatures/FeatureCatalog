# LiqStats
Distributions of liquidation prices, quantities, and values, the largest liquidations, and runs of consecutive same-side liquidations.
## Availability
- **Input:** Liquidation feed
- **Markets:** Perpetual only
- **Feature family:** Extended liquidations
- **Coverage, Binance:** 2019-12-01 through 2026-10-01 (interval-start dates); 1,992 perp hourly files.
- **Coverage, OKX:** 2020-01-01 through 2026-10-01 (interval-start dates); 1,968 perp hourly files.
- **Coverage, Bybit:** 2020-06-01 through 2026-10-01 (interval-start dates); 1,848 perp hourly files.
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Notes
- Buy-side liquidations are forced buys that close short positions; sell-side liquidations are forced sells that close long positions.
- Statistics are taken across individual liquidation orders. Kurtosis is excess kurtosis: 0 for a normal distribution.
- A run is a sequence of consecutive liquidation orders on the same side; the longest run has the most orders.
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `liq_price_mean` | `double` | Average liquidation price across liquidation orders in the interval. |
| `liq_price_stdev` | `double` | Standard deviation of liquidation price across liquidation orders in the interval. |
| `liq_price_skew` | `double` | Skewness of liquidation price across liquidation orders in the interval. |
| `liq_price_kurtosis` | `double` | Excess kurtosis of liquidation price across liquidation orders in the interval. |
| `liq_price_mean_buy` | `double` | Average liquidation price across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_price_stdev_buy` | `double` | Standard deviation of liquidation price across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_price_skew_buy` | `double` | Skewness of liquidation price across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_price_kurtosis_buy` | `double` | Excess kurtosis of liquidation price across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_price_mean_sell` | `double` | Average liquidation price across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_price_stdev_sell` | `double` | Standard deviation of liquidation price across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_price_skew_sell` | `double` | Skewness of liquidation price across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_price_kurtosis_sell` | `double` | Excess kurtosis of liquidation price across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_share_mean` | `double` | Average liquidated quantity across liquidation orders in the interval. |
| `liq_share_stdev` | `double` | Standard deviation of liquidated quantity across liquidation orders in the interval. |
| `liq_share_skew` | `double` | Skewness of liquidated quantity across liquidation orders in the interval. |
| `liq_share_kurtosis` | `double` | Excess kurtosis of liquidated quantity across liquidation orders in the interval. |
| `liq_share_mean_buy` | `double` | Average liquidated quantity across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_share_stdev_buy` | `double` | Standard deviation of liquidated quantity across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_share_skew_buy` | `double` | Skewness of liquidated quantity across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_share_kurtosis_buy` | `double` | Excess kurtosis of liquidated quantity across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_share_mean_sell` | `double` | Average liquidated quantity across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_share_stdev_sell` | `double` | Standard deviation of liquidated quantity across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_share_skew_sell` | `double` | Skewness of liquidated quantity across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_share_kurtosis_sell` | `double` | Excess kurtosis of liquidated quantity across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_value_mean` | `double` | Average liquidated value (price × quantity) across liquidation orders in the interval. |
| `liq_value_stdev` | `double` | Standard deviation of liquidated value (price × quantity) across liquidation orders in the interval. |
| `liq_value_skew` | `double` | Skewness of liquidated value (price × quantity) across liquidation orders in the interval. |
| `liq_value_kurtosis` | `double` | Excess kurtosis of liquidated value (price × quantity) across liquidation orders in the interval. |
| `liq_value_mean_buy` | `double` | Average liquidated value (price × quantity) across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_value_stdev_buy` | `double` | Standard deviation of liquidated value (price × quantity) across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_value_skew_buy` | `double` | Skewness of liquidated value (price × quantity) across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_value_kurtosis_buy` | `double` | Excess kurtosis of liquidated value (price × quantity) across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_value_mean_sell` | `double` | Average liquidated value (price × quantity) across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_value_stdev_sell` | `double` | Standard deviation of liquidated value (price × quantity) across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_value_skew_sell` | `double` | Skewness of liquidated value (price × quantity) across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_value_kurtosis_sell` | `double` | Excess kurtosis of liquidated value (price × quantity) across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_price_max` | `double` | Largest liquidation price across liquidation orders in the interval. |
| `liq_price_max_buy` | `double` | Largest liquidation price across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_price_max_sell` | `double` | Largest liquidation price across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_price_min` | `double` | Smallest liquidation price across liquidation orders in the interval. |
| `liq_price_min_buy` | `double` | Smallest liquidation price across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_price_min_sell` | `double` | Smallest liquidation price across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_share_max` | `double` | Largest liquidated quantity across liquidation orders in the interval. |
| `liq_share_max_buy` | `double` | Largest liquidated quantity across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_share_max_sell` | `double` | Largest liquidated quantity across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_value_max` | `double` | Largest liquidated value (price × quantity) across liquidation orders in the interval. |
| `liq_value_max_buy` | `double` | Largest liquidated value (price × quantity) across liquidation orders in the interval. Buy-side liquidations only. |
| `liq_value_max_sell` | `double` | Largest liquidated value (price × quantity) across liquidation orders in the interval. Sell-side liquidations only. |
| `liq_max_cont_count_buy` | `int32` | Number of liquidation orders in the longest run of consecutive buy-side liquidations. |
| `liq_max_cont_count_sell` | `int32` | Number of liquidation orders in the longest run of consecutive sell-side liquidations. |
| `liq_avg_cont_count_buy` | `double` | Average number of liquidation orders per run of consecutive buy-side liquidations. |
| `liq_avg_cont_count_sell` | `double` | Average number of liquidation orders per run of consecutive sell-side liquidations. |
| `liq_max_cont_share_sum_buy` | `double` | Total liquidated quantity in the longest run of consecutive buy-side liquidations. |
| `liq_max_cont_share_sum_sell` | `double` | Total liquidated quantity in the longest run of consecutive sell-side liquidations. |
| `liq_max_cont_value_sum_buy` | `double` | Total liquidated value in the longest run of consecutive buy-side liquidations. |
| `liq_max_cont_value_sum_sell` | `double` | Total liquidated value in the longest run of consecutive sell-side liquidations. |
| `liq_max_cont_price_chg_buy` | `double` | Cumulative relative price change across the longest run of consecutive buy-side liquidations, as a fraction. |
| `liq_max_cont_price_chg_sell` | `double` | Cumulative relative price change across the longest run of consecutive sell-side liquidations, as a fraction. |
| `liq_max_cont_price_avgchg_buy` | `double` | Average relative price change between consecutive orders in the longest run of consecutive buy-side liquidations, as a fraction. |
| `liq_max_cont_price_avgchg_sell` | `double` | Average relative price change between consecutive orders in the longest run of consecutive sell-side liquidations, as a fraction. |
| `liq_mean_cont_price_chg_buy` | `double` | Average cumulative relative price change per run of consecutive buy-side liquidations, as a fraction. |
| `liq_mean_cont_price_chg_sell` | `double` | Average cumulative relative price change per run of consecutive sell-side liquidations, as a fraction. |
| `liq_price_mean_top` | `double` | Average liquidation price of the largest 25% of liquidation orders by quantity. |
| `liq_price_mean_top_buy` | `double` | Average liquidation price of the largest 25% of liquidation orders by quantity. Buy-side liquidations only. |
| `liq_price_mean_top_sell` | `double` | Average liquidation price of the largest 25% of liquidation orders by quantity. Sell-side liquidations only. |
| `liq_share_mean_top` | `double` | Average liquidated quantity of the largest 25% of liquidation orders by quantity. |
| `liq_share_mean_top_buy` | `double` | Average liquidated quantity of the largest 25% of liquidation orders by quantity. Buy-side liquidations only. |
| `liq_share_mean_top_sell` | `double` | Average liquidated quantity of the largest 25% of liquidation orders by quantity. Sell-side liquidations only. |
| `liq_value_mean_top` | `double` | Average liquidated value (price × quantity) of the largest 25% of liquidation orders by quantity. |
| `liq_value_mean_top_buy` | `double` | Average liquidated value (price × quantity) of the largest 25% of liquidation orders by quantity. Buy-side liquidations only. |
| `liq_value_mean_top_sell` | `double` | Average liquidated value (price × quantity) of the largest 25% of liquidation orders by quantity. Sell-side liquidations only. |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
