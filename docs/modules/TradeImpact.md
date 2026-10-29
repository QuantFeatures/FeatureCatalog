# TradeImpact
Covariance and correlation between trade-to-trade price changes and trade size across 60 equal sub-intervals.
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
- Sub-interval features split each interval into 60 equal sub-intervals. A sub-interval without trades carries the last price forward and has zero quantity.
- Price change is a trade's price minus the previous trade's price.
- Subset features (buyer- or seller-initiated, tick direction) use only the trades in that subset.
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `cov_avg_pcv` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. |
| `rho_avg_pcv` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. |
| `cov_avg_pcv_buy` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Buyer-initiated trades only (the buyer was the aggressor). |
| `rho_avg_pcv_buy` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Buyer-initiated trades only (the buyer was the aggressor). |
| `cov_avg_pcv_sell` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Seller-initiated trades only (the seller was the aggressor). |
| `rho_avg_pcv_sell` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Seller-initiated trades only (the seller was the aggressor). |
| `cov_avg_pcv_price_up` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Up-tick trades only. |
| `rho_avg_pcv_price_up` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Up-tick trades only. |
| `cov_avg_pcv_price_down` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Down-tick trades only. |
| `rho_avg_pcv_price_down` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Down-tick trades only. |
| `cov_avg_pcv_buy_price_up` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Buyer-initiated trades only (the buyer was the aggressor). Up-tick trades only. |
| `rho_avg_pcv_buy_price_up` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Buyer-initiated trades only (the buyer was the aggressor). Up-tick trades only. |
| `cov_avg_pcv_buy_price_down` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Buyer-initiated trades only (the buyer was the aggressor). Down-tick trades only. |
| `rho_avg_pcv_buy_price_down` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Buyer-initiated trades only (the buyer was the aggressor). Down-tick trades only. |
| `cov_avg_pcv_sell_price_up` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Seller-initiated trades only (the seller was the aggressor). Up-tick trades only. |
| `rho_avg_pcv_sell_price_up` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Seller-initiated trades only (the seller was the aggressor). Up-tick trades only. |
| `cov_avg_pcv_sell_price_down` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Seller-initiated trades only (the seller was the aggressor). Down-tick trades only. |
| `rho_avg_pcv_sell_price_down` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its average trade size. Seller-initiated trades only (the seller was the aggressor). Down-tick trades only. |
| `cov_bar_pcv` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. |
| `rho_bar_pcv` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. |
| `cov_bar_pcv_buy` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Buyer-initiated trades only (the buyer was the aggressor). |
| `rho_bar_pcv_buy` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Buyer-initiated trades only (the buyer was the aggressor). |
| `cov_bar_pcv_sell` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Seller-initiated trades only (the seller was the aggressor). |
| `rho_bar_pcv_sell` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Seller-initiated trades only (the seller was the aggressor). |
| `cov_bar_pcv_price_up` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Up-tick trades only. |
| `rho_bar_pcv_price_up` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Up-tick trades only. |
| `cov_bar_pcv_price_down` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Down-tick trades only. |
| `rho_bar_pcv_price_down` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Down-tick trades only. |
| `cov_bar_pcv_buy_price_up` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Buyer-initiated trades only (the buyer was the aggressor). Up-tick trades only. |
| `rho_bar_pcv_buy_price_up` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Buyer-initiated trades only (the buyer was the aggressor). Up-tick trades only. |
| `cov_bar_pcv_buy_price_down` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Buyer-initiated trades only (the buyer was the aggressor). Down-tick trades only. |
| `rho_bar_pcv_buy_price_down` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Buyer-initiated trades only (the buyer was the aggressor). Down-tick trades only. |
| `cov_bar_pcv_sell_price_up` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Seller-initiated trades only (the seller was the aggressor). Up-tick trades only. |
| `rho_bar_pcv_sell_price_up` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Seller-initiated trades only (the seller was the aggressor). Up-tick trades only. |
| `cov_bar_pcv_sell_price_down` | `double` | Covariance, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Seller-initiated trades only (the seller was the aggressor). Down-tick trades only. |
| `rho_bar_pcv_sell_price_down` | `double` | Correlation, across the 60 sub-intervals, between each sub-interval's average price change per trade and its total traded quantity. Seller-initiated trades only (the seller was the aggressor). Down-tick trades only. |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
