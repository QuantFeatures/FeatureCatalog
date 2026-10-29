# QuoteBasic
Interval summaries of best bid, best ask, spread, midprice, and quoted sizes, with quote-update counts.
## Availability
- **Input:** Best-bid/offer quotes
- **Markets:** Spot and perpetual
- **Feature family:** Top of book
- **Coverage, Binance:** 2019-12-01 through 2026-10-01 (interval-start dates); 1,992 hourly files per market (3,984 total).
- **Coverage, OKX:** 2020-01-01 through 2026-10-01 (interval-start dates); 1,968 perp hourly files.
- **Coverage, Bybit:** 2020-06-01 through 2026-10-01 (interval-start dates); 1,848 perp hourly files.
- **Coverage, Hyperliquid:** 2024-11-01 through 2026-10-01 (interval-start dates); 576 perp hourly files.
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `nquote` | `int32` | Number of quotes in the interval; a quote is a change in the best bid or ask price or size (top of book). |
| `nquote_bid` | `int32` | Number of quotes in which the bid price changed. |
| `nquote_bid_up` | `int32` | Number of quotes in which the bid price rose. |
| `nquote_bid_down` | `int32` | Number of quotes in which the bid price fell. |
| `nquote_bidsize` | `int32` | Number of quotes in which the bid size changed. |
| `nquote_bidsize_up` | `int32` | Number of quotes in which the bid size rose. |
| `nquote_bidsize_down` | `int32` | Number of quotes in which the bid size fell. |
| `nquote_ask` | `int32` | Number of quotes in which the ask price changed. |
| `nquote_ask_up` | `int32` | Number of quotes in which the ask price rose. |
| `nquote_ask_down` | `int32` | Number of quotes in which the ask price fell. |
| `nquote_asksize` | `int32` | Number of quotes in which the ask size changed. |
| `nquote_asksize_up` | `int32` | Number of quotes in which the ask size rose. |
| `nquote_asksize_down` | `int32` | Number of quotes in which the ask size fell. |
| `nquote_bid_askflat` | `int32` | Number of quotes in which the bid price changed while the ask price was unchanged. |
| `nquote_bidup_askflat` | `int32` | Number of quotes in which the bid price rose while the ask price was unchanged. |
| `nquote_biddown_askflat` | `int32` | Number of quotes in which the bid price fell while the ask price was unchanged. |
| `nquote_ask_bidflat` | `int32` | Number of quotes in which the ask price changed while the bid price was unchanged. |
| `nquote_askup_bidflat` | `int32` | Number of quotes in which the ask price rose while the bid price was unchanged. |
| `nquote_askdown_bidflat` | `int32` | Number of quotes in which the ask price fell while the bid price was unchanged. |
| `open_spread` | `double` | Bid-ask spread (ask − bid) of the first quote in the interval. |
| `high_spread` | `double` | Highest bid-ask spread (ask − bid) across quotes in the interval. |
| `low_spread` | `double` | Lowest bid-ask spread (ask − bid) across quotes in the interval. |
| `close_spread` | `double` | Bid-ask spread (ask − bid) of the last quote in the interval. |
| `twa_spread` | `double` | Time-weighted average bid-ask spread (ask − bid) over the interval. |
| `awa_spread` | `double` | Average bid-ask spread (ask − bid) across quotes in the interval, each quote weighted equally. |
| `open_spread_bps` | `double` | Bid-ask spread relative to the midprice of the first quote in the interval, in basis points. |
| `high_spread_bps` | `double` | Highest bid-ask spread relative to the midprice across quotes in the interval, in basis points. |
| `low_spread_bps` | `double` | Lowest bid-ask spread relative to the midprice across quotes in the interval, in basis points. |
| `close_spread_bps` | `double` | Bid-ask spread relative to the midprice of the last quote in the interval, in basis points. |
| `twa_spread_bps` | `double` | Time-weighted average bid-ask spread relative to the midprice over the interval, in basis points. |
| `awa_spread_bps` | `double` | Average bid-ask spread relative to the midprice across quotes in the interval, each quote weighted equally, in basis points. |
| `open_mid` | `double` | Midprice ((bid + ask) / 2) of the first quote in the interval. |
| `high_mid` | `double` | Highest midprice ((bid + ask) / 2) across quotes in the interval. |
| `low_mid` | `double` | Lowest midprice ((bid + ask) / 2) across quotes in the interval. |
| `close_mid` | `double` | Midprice ((bid + ask) / 2) of the last quote in the interval. |
| `twap_mid` | `double` | Time-weighted average midprice ((bid + ask) / 2) over the interval. |
| `awap_mid` | `double` | Average midprice ((bid + ask) / 2) across quotes in the interval, each quote weighted equally. |
| `open_bid` | `double` | Bid price of the first quote in the interval. |
| `high_bid` | `double` | Highest bid price across quotes in the interval. |
| `low_bid` | `double` | Lowest bid price across quotes in the interval. |
| `close_bid` | `double` | Bid price of the last quote in the interval. |
| `vwap_bid` | `double` | Bid-size-weighted average bid price across quotes in the interval. |
| `twap_bid` | `double` | Time-weighted average bid price over the interval. |
| `awap_bid` | `double` | Average bid price across quotes in the interval, each quote weighted equally. |
| `open_bidsize` | `double` | Bid size of the first quote in the interval. |
| `high_bidsize` | `double` | Highest bid size across quotes in the interval. |
| `low_bidsize` | `double` | Lowest bid size across quotes in the interval. |
| `close_bidsize` | `double` | Bid size of the last quote in the interval. |
| `vwa_bidsize` | `double` | Bid-price-weighted average bid size across quotes in the interval. |
| `twa_bidsize` | `double` | Time-weighted average bid size over the interval. |
| `awa_bidsize` | `double` | Average bid size across quotes in the interval, each quote weighted equally. |
| `open_ask` | `double` | Ask price of the first quote in the interval. |
| `high_ask` | `double` | Highest ask price across quotes in the interval. |
| `low_ask` | `double` | Lowest ask price across quotes in the interval. |
| `close_ask` | `double` | Ask price of the last quote in the interval. |
| `vwap_ask` | `double` | Ask-size-weighted average ask price across quotes in the interval. |
| `twap_ask` | `double` | Time-weighted average ask price over the interval. |
| `awap_ask` | `double` | Average ask price across quotes in the interval, each quote weighted equally. |
| `open_asksize` | `double` | Ask size of the first quote in the interval. |
| `high_asksize` | `double` | Highest ask size across quotes in the interval. |
| `low_asksize` | `double` | Lowest ask size across quotes in the interval. |
| `close_asksize` | `double` | Ask size of the last quote in the interval. |
| `vwa_asksize` | `double` | Ask-price-weighted average ask size across quotes in the interval. |
| `twa_asksize` | `double` | Time-weighted average ask size over the interval. |
| `awa_asksize` | `double` | Average ask size across quotes in the interval, each quote weighted equally. |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
