# TradeCovar
Covariance and correlation between trade price and trade size across the trades in an interval, overall and by side and tick direction.
## Availability
- **Input:** Exchange trades
- **Markets:** Spot and perpetual
- **Feature family:** Trade relationships
- **Coverage, Binance:** 2019-12-01 through 2026-10-01 (interval-start dates); 1,992 hourly files per market (3,984 total).
- **Coverage, OKX:** 2020-01-01 through 2026-10-01 (interval-start dates); 1,968 perp hourly files.
- **Coverage, Bybit:** 2020-06-01 through 2026-10-01 (interval-start dates); 1,848 perp hourly files.
- **Coverage, Hyperliquid:** 2024-11-01 through 2026-10-01 (interval-start dates); 576 perp hourly files.
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Notes
- Statistics are taken across the individual trades in the interval.
- Tick direction compares a trade's price with the previous trade of either side.
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `cov_pv` | `double` | Covariance between trade price and trade size across trades in the interval. |
| `rho_pv` | `double` | Correlation between trade price and trade size across trades in the interval. |
| `cov_pv_buy` | `double` | Covariance between trade price and trade size across trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `rho_pv_buy` | `double` | Correlation between trade price and trade size across trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). |
| `cov_pv_sell` | `double` | Covariance between trade price and trade size across trades in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `rho_pv_sell` | `double` | Correlation between trade price and trade size across trades in the interval. Seller-initiated trades only (the seller was the aggressor). |
| `cov_pv_price_up` | `double` | Covariance between trade price and trade size across trades in the interval. Up-tick trades only. |
| `rho_pv_price_up` | `double` | Correlation between trade price and trade size across trades in the interval. Up-tick trades only. |
| `cov_pv_price_flat` | `double` | Covariance between trade price and trade size across trades in the interval. Flat-tick trades only. |
| `rho_pv_price_flat` | `double` | Correlation between trade price and trade size across trades in the interval. Flat-tick trades only. |
| `cov_pv_price_down` | `double` | Covariance between trade price and trade size across trades in the interval. Down-tick trades only. |
| `rho_pv_price_down` | `double` | Correlation between trade price and trade size across trades in the interval. Down-tick trades only. |
| `cov_pv_buy_price_up` | `double` | Covariance between trade price and trade size across trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Up-tick trades only. |
| `rho_pv_buy_price_up` | `double` | Correlation between trade price and trade size across trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Up-tick trades only. |
| `cov_pv_buy_price_flat` | `double` | Covariance between trade price and trade size across trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Flat-tick trades only. |
| `rho_pv_buy_price_flat` | `double` | Correlation between trade price and trade size across trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Flat-tick trades only. |
| `cov_pv_buy_price_down` | `double` | Covariance between trade price and trade size across trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Down-tick trades only. |
| `rho_pv_buy_price_down` | `double` | Correlation between trade price and trade size across trades in the interval. Buyer-initiated trades only (the buyer was the aggressor). Down-tick trades only. |
| `cov_pv_sell_price_up` | `double` | Covariance between trade price and trade size across trades in the interval. Seller-initiated trades only (the seller was the aggressor). Up-tick trades only. |
| `rho_pv_sell_price_up` | `double` | Correlation between trade price and trade size across trades in the interval. Seller-initiated trades only (the seller was the aggressor). Up-tick trades only. |
| `cov_pv_sell_price_flat` | `double` | Covariance between trade price and trade size across trades in the interval. Seller-initiated trades only (the seller was the aggressor). Flat-tick trades only. |
| `rho_pv_sell_price_flat` | `double` | Correlation between trade price and trade size across trades in the interval. Seller-initiated trades only (the seller was the aggressor). Flat-tick trades only. |
| `cov_pv_sell_price_down` | `double` | Covariance between trade price and trade size across trades in the interval. Seller-initiated trades only (the seller was the aggressor). Down-tick trades only. |
| `rho_pv_sell_price_down` | `double` | Correlation between trade price and trade size across trades in the interval. Seller-initiated trades only (the seller was the aggressor). Down-tick trades only. |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
