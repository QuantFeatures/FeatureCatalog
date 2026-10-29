# QuoteGradient
Interval measures describing changes in best bid, best ask, quoted size and value, midprice, and spread, with counts of upward, downward, and unchanged updates.
## Availability
- **Input:** Best-bid/offer quotes
- **Markets:** Spot and perpetual
- **Feature family:** Top-of-book dynamics
- **Coverage, Binance:** 2019-12-01 through 2026-10-01 (interval-start dates); 1,992 hourly files per market (3,984 total).
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Notes
- A quote is a change in the best bid or ask price or size. Changes are measured between consecutive quotes.
- `_up` and `_down` features use only the quotes in which the named quantity rose or fell.
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `awa_bidsize_change` | `double` | Average change in the bid size between consecutive quotes, each quote weighted equally. |
| `awa_asksize_change` | `double` | Average change in the ask size between consecutive quotes, each quote weighted equally. |
| `awa_bidvalue_change` | `double` | Average change in the bid value (bid price × bid size) between consecutive quotes, each quote weighted equally. |
| `awa_askvalue_change` | `double` | Average change in the ask value (ask price × ask size) between consecutive quotes, each quote weighted equally. |
| `awa_bidprice_change` | `double` | Average change in the bid price between consecutive quotes, each quote weighted equally. |
| `awa_askprice_change` | `double` | Average change in the ask price between consecutive quotes, each quote weighted equally. |
| `awa_midprice_change` | `double` | Average change in the midprice between consecutive quotes, each quote weighted equally. |
| `awa_spreadbps_change` | `double` | Average change in the bid-ask spread in basis points between consecutive quotes, each quote weighted equally. |
| `pwa_bidsize_change` | `double` | Average change in the bid size between consecutive quotes, weighted by the bid price. |
| `pwa_asksize_change` | `double` | Average change in the ask size between consecutive quotes, weighted by the ask price. |
| `awa_bidsize_up` | `double` | Average change in the bid size between consecutive quotes, each quote weighted equally. Quotes in which it rose only. |
| `awa_asksize_up` | `double` | Average change in the ask size between consecutive quotes, each quote weighted equally. Quotes in which it rose only. |
| `awa_bidvalue_up` | `double` | Average change in the bid value (bid price × bid size) between consecutive quotes, each quote weighted equally. Quotes in which it rose only. |
| `awa_askvalue_up` | `double` | Average change in the ask value (ask price × ask size) between consecutive quotes, each quote weighted equally. Quotes in which it rose only. |
| `awa_bidprice_up` | `double` | Average change in the bid price between consecutive quotes, each quote weighted equally. Quotes in which it rose only. |
| `awa_askprice_up` | `double` | Average change in the ask price between consecutive quotes, each quote weighted equally. Quotes in which it rose only. |
| `awa_midprice_up` | `double` | Average change in the midprice between consecutive quotes, each quote weighted equally. Quotes in which it rose only. |
| `awa_spreadbps_up` | `double` | Average change in the bid-ask spread in basis points between consecutive quotes, each quote weighted equally. Quotes in which it rose only. |
| `pwa_bidsize_up` | `double` | Average change in the bid size between consecutive quotes, weighted by the bid price. Quotes in which it rose only. |
| `pwa_asksize_up` | `double` | Average change in the ask size between consecutive quotes, weighted by the ask price. Quotes in which it rose only. |
| `awa_bidsize_down` | `double` | Average change in the bid size between consecutive quotes, each quote weighted equally. Quotes in which it fell only. |
| `awa_asksize_down` | `double` | Average change in the ask size between consecutive quotes, each quote weighted equally. Quotes in which it fell only. |
| `awa_bidvalue_down` | `double` | Average change in the bid value (bid price × bid size) between consecutive quotes, each quote weighted equally. Quotes in which it fell only. |
| `awa_askvalue_down` | `double` | Average change in the ask value (ask price × ask size) between consecutive quotes, each quote weighted equally. Quotes in which it fell only. |
| `awa_bidprice_down` | `double` | Average change in the bid price between consecutive quotes, each quote weighted equally. Quotes in which it fell only. |
| `awa_askprice_down` | `double` | Average change in the ask price between consecutive quotes, each quote weighted equally. Quotes in which it fell only. |
| `awa_midprice_down` | `double` | Average change in the midprice between consecutive quotes, each quote weighted equally. Quotes in which it fell only. |
| `awa_spreadbps_down` | `double` | Average change in the bid-ask spread in basis points between consecutive quotes, each quote weighted equally. Quotes in which it fell only. |
| `pwa_bidsize_down` | `double` | Average change in the bid size between consecutive quotes, weighted by the bid price. Quotes in which it fell only. |
| `pwa_asksize_down` | `double` | Average change in the ask size between consecutive quotes, weighted by the ask price. Quotes in which it fell only. |
| `num_bidsize_flat` | `int32` | Number of quotes in which the bid size was unchanged. |
| `num_bidsize_up` | `int32` | Number of quotes in which the bid size rose. |
| `num_bidsize_down` | `int32` | Number of quotes in which the bid size fell. |
| `num_asksize_flat` | `int32` | Number of quotes in which the ask size was unchanged. |
| `num_asksize_up` | `int32` | Number of quotes in which the ask size rose. |
| `num_asksize_down` | `int32` | Number of quotes in which the ask size fell. |
| `num_bidprice_flat` | `int32` | Number of quotes in which the bid price was unchanged. |
| `num_bidprice_up` | `int32` | Number of quotes in which the bid price rose. |
| `num_bidprice_down` | `int32` | Number of quotes in which the bid price fell. |
| `num_askprice_flat` | `int32` | Number of quotes in which the ask price was unchanged. |
| `num_askprice_up` | `int32` | Number of quotes in which the ask price rose. |
| `num_askprice_down` | `int32` | Number of quotes in which the ask price fell. |
| `num_bidvalue_flat` | `int32` | Number of quotes in which the bid value (bid price × bid size) was unchanged. |
| `num_bidvalue_up` | `int32` | Number of quotes in which the bid value (bid price × bid size) rose. |
| `num_bidvalue_down` | `int32` | Number of quotes in which the bid value (bid price × bid size) fell. |
| `num_askvalue_flat` | `int32` | Number of quotes in which the ask value (ask price × ask size) was unchanged. |
| `num_askvalue_up` | `int32` | Number of quotes in which the ask value (ask price × ask size) rose. |
| `num_askvalue_down` | `int32` | Number of quotes in which the ask value (ask price × ask size) fell. |
| `num_mid_flat` | `int32` | Number of quotes in which the midprice was unchanged. |
| `num_mid_up` | `int32` | Number of quotes in which the midprice rose. |
| `num_mid_down` | `int32` | Number of quotes in which the midprice fell. |
| `num_spreadbps_flat` | `int32` | Number of quotes in which the bid-ask spread in basis points was unchanged. |
| `num_spreadbps_up` | `int32` | Number of quotes in which the bid-ask spread in basis points rose. |
| `num_spreadbps_down` | `int32` | Number of quotes in which the bid-ask spread in basis points fell. |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
