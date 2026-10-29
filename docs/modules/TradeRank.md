# TradeRank
Interval trade-activity measures for each instrument, with cross-sectional ranks and z-scores across the published instrument universe.
## Availability
- **Input:** Exchange trades
- **Markets:** Spot and perpetual
- **Feature family:** Cross-sectional market activity
- **Coverage, Binance:** 2019-12-01 through 2026-10-01 (interval-start dates); 1,992 hourly files per market (3,984 total).
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Notes
- `_rank` and `_zscore` features compare each instrument with the other published instruments in the same market and interval.
- Imbalance features range from −1 (all seller-initiated) to +1 (all buyer-initiated).
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `count_skew` | `double` | Buy-sell imbalance of trade counts. |
| `count_skew_rank` | `double` | Cross-sectional rank, in (0, 1], of `count_skew` across the published instruments in the same market and interval. |
| `count_skew_zscore` | `double` | Cross-sectional z-score of `count_skew` across the published instruments in the same market and interval. |
| `count_skew_up` | `double` | Buy-sell imbalance of trade counts. Up-tick trades only. |
| `count_skew_up_rank` | `double` | Cross-sectional rank, in (0, 1], of `count_skew_up` across the published instruments in the same market and interval. |
| `count_skew_up_zscore` | `double` | Cross-sectional z-score of `count_skew_up` across the published instruments in the same market and interval. |
| `count_skew_flat` | `double` | Buy-sell imbalance of trade counts. Flat-tick trades only. |
| `count_skew_flat_rank` | `double` | Cross-sectional rank, in (0, 1], of `count_skew_flat` across the published instruments in the same market and interval. |
| `count_skew_flat_zscore` | `double` | Cross-sectional z-score of `count_skew_flat` across the published instruments in the same market and interval. |
| `count_skew_down` | `double` | Buy-sell imbalance of trade counts. Down-tick trades only. |
| `count_skew_down_rank` | `double` | Cross-sectional rank, in (0, 1], of `count_skew_down` across the published instruments in the same market and interval. |
| `count_skew_down_zscore` | `double` | Cross-sectional z-score of `count_skew_down` across the published instruments in the same market and interval. |
| `volume_skew` | `double` | Buy-sell imbalance of traded quantity. |
| `volume_skew_rank` | `double` | Cross-sectional rank, in (0, 1], of `volume_skew` across the published instruments in the same market and interval. |
| `volume_skew_zscore` | `double` | Cross-sectional z-score of `volume_skew` across the published instruments in the same market and interval. |
| `volume_skew_up` | `double` | Buy-sell imbalance of traded quantity. Up-tick trades only. |
| `volume_skew_up_rank` | `double` | Cross-sectional rank, in (0, 1], of `volume_skew_up` across the published instruments in the same market and interval. |
| `volume_skew_up_zscore` | `double` | Cross-sectional z-score of `volume_skew_up` across the published instruments in the same market and interval. |
| `volume_skew_flat` | `double` | Buy-sell imbalance of traded quantity. Flat-tick trades only. |
| `volume_skew_flat_rank` | `double` | Cross-sectional rank, in (0, 1], of `volume_skew_flat` across the published instruments in the same market and interval. |
| `volume_skew_flat_zscore` | `double` | Cross-sectional z-score of `volume_skew_flat` across the published instruments in the same market and interval. |
| `volume_skew_down` | `double` | Buy-sell imbalance of traded quantity. Down-tick trades only. |
| `volume_skew_down_rank` | `double` | Cross-sectional rank, in (0, 1], of `volume_skew_down` across the published instruments in the same market and interval. |
| `volume_skew_down_zscore` | `double` | Cross-sectional z-score of `volume_skew_down` across the published instruments in the same market and interval. |
| `trade_imb` | `double` | Buy-sell imbalance of traded value. |
| `trade_imb_rank` | `double` | Cross-sectional rank, in (0, 1], of `trade_imb` across the published instruments in the same market and interval. |
| `trade_imb_zscore` | `double` | Cross-sectional z-score of `trade_imb` across the published instruments in the same market and interval. |
| `trade_imb_up` | `double` | Buy-sell imbalance of traded value. Up-tick trades only. |
| `trade_imb_up_rank` | `double` | Cross-sectional rank, in (0, 1], of `trade_imb_up` across the published instruments in the same market and interval. |
| `trade_imb_up_zscore` | `double` | Cross-sectional z-score of `trade_imb_up` across the published instruments in the same market and interval. |
| `trade_imb_flat` | `double` | Buy-sell imbalance of traded value. Flat-tick trades only. |
| `trade_imb_flat_rank` | `double` | Cross-sectional rank, in (0, 1], of `trade_imb_flat` across the published instruments in the same market and interval. |
| `trade_imb_flat_zscore` | `double` | Cross-sectional z-score of `trade_imb_flat` across the published instruments in the same market and interval. |
| `trade_imb_down` | `double` | Buy-sell imbalance of traded value. Down-tick trades only. |
| `trade_imb_down_rank` | `double` | Cross-sectional rank, in (0, 1], of `trade_imb_down` across the published instruments in the same market and interval. |
| `trade_imb_down_zscore` | `double` | Cross-sectional z-score of `trade_imb_down` across the published instruments in the same market and interval. |
| `vwps` | `double` | Buyer-initiated minus seller-initiated traded value, per unit of total traded quantity. |
| `vwps_rank` | `double` | Cross-sectional rank, in (0, 1], of `vwps` across the published instruments in the same market and interval. |
| `vwps_zscore` | `double` | Cross-sectional z-score of `vwps` across the published instruments in the same market and interval. |
| `vwps_up` | `double` | Buyer-initiated minus seller-initiated traded value, per unit of total traded quantity. Up-tick trades only. |
| `vwps_up_rank` | `double` | Cross-sectional rank, in (0, 1], of `vwps_up` across the published instruments in the same market and interval. |
| `vwps_up_zscore` | `double` | Cross-sectional z-score of `vwps_up` across the published instruments in the same market and interval. |
| `vwps_flat` | `double` | Buyer-initiated minus seller-initiated traded value, per unit of total traded quantity. Flat-tick trades only. |
| `vwps_flat_rank` | `double` | Cross-sectional rank, in (0, 1], of `vwps_flat` across the published instruments in the same market and interval. |
| `vwps_flat_zscore` | `double` | Cross-sectional z-score of `vwps_flat` across the published instruments in the same market and interval. |
| `vwps_down` | `double` | Buyer-initiated minus seller-initiated traded value, per unit of total traded quantity. Down-tick trades only. |
| `vwps_down_rank` | `double` | Cross-sectional rank, in (0, 1], of `vwps_down` across the published instruments in the same market and interval. |
| `vwps_down_zscore` | `double` | Cross-sectional z-score of `vwps_down` across the published instruments in the same market and interval. |
| `flow_skew` | `double` | Where the volume-weighted average price sits relative to the average trade price, scaled by the interval's price range; positive when larger trades occur at higher prices. |
| `flow_skew_rank` | `double` | Cross-sectional rank, in (0, 1], of `flow_skew` across the published instruments in the same market and interval. |
| `flow_skew_zscore` | `double` | Cross-sectional z-score of `flow_skew` across the published instruments in the same market and interval. |
| `flow_skew_buy` | `double` | Where the volume-weighted average price sits relative to the average trade price, scaled by the interval's price range; positive when larger trades occur at higher prices. Buyer-initiated trades only (the buyer was the aggressor). |
| `flow_skew_buy_rank` | `double` | Cross-sectional rank, in (0, 1], of `flow_skew_buy` across the published instruments in the same market and interval. |
| `flow_skew_buy_zscore` | `double` | Cross-sectional z-score of `flow_skew_buy` across the published instruments in the same market and interval. |
| `flow_skew_sell` | `double` | Where the volume-weighted average price sits relative to the average trade price, scaled by the interval's price range; positive when larger trades occur at higher prices. Seller-initiated trades only (the seller was the aggressor). |
| `flow_skew_sell_rank` | `double` | Cross-sectional rank, in (0, 1], of `flow_skew_sell` across the published instruments in the same market and interval. |
| `flow_skew_sell_zscore` | `double` | Cross-sectional z-score of `flow_skew_sell` across the published instruments in the same market and interval. |
| `ldi` | `double` | Liquidity density: base-10 logarithm of traded value per unit of price range (high − low). |
| `ldi_rank` | `double` | Cross-sectional rank, in (0, 1], of `ldi` across the published instruments in the same market and interval. |
| `ldi_zscore` | `double` | Cross-sectional z-score of `ldi` across the published instruments in the same market and interval. |
| `ldi_buy` | `double` | Liquidity density: base-10 logarithm of traded value per unit of price range (high − low). Buyer-initiated trades only (the buyer was the aggressor). |
| `ldi_buy_rank` | `double` | Cross-sectional rank, in (0, 1], of `ldi_buy` across the published instruments in the same market and interval. |
| `ldi_buy_zscore` | `double` | Cross-sectional z-score of `ldi_buy` across the published instruments in the same market and interval. |
| `ldi_sell` | `double` | Liquidity density: base-10 logarithm of traded value per unit of price range (high − low). Seller-initiated trades only (the seller was the aggressor). |
| `ldi_sell_rank` | `double` | Cross-sectional rank, in (0, 1], of `ldi_sell` across the published instruments in the same market and interval. |
| `ldi_sell_zscore` | `double` | Cross-sectional z-score of `ldi_sell` across the published instruments in the same market and interval. |
| `tradeval_rank` | `double` | Cross-sectional rank, in (0, 1], of `tradeval` across the published instruments in the same market and interval. |
| `tradeval_zscore` | `double` | Cross-sectional z-score of `tradeval` across the published instruments in the same market and interval. |
| `tradeval_buy_rank` | `double` | Cross-sectional rank, in (0, 1], of `tradeval_buy` across the published instruments in the same market and interval. |
| `tradeval_buy_zscore` | `double` | Cross-sectional z-score of `tradeval_buy` across the published instruments in the same market and interval. |
| `tradeval_sell_rank` | `double` | Cross-sectional rank, in (0, 1], of `tradeval_sell` across the published instruments in the same market and interval. |
| `tradeval_sell_zscore` | `double` | Cross-sectional z-score of `tradeval_sell` across the published instruments in the same market and interval. |
| `tradeval_up_rank` | `double` | Cross-sectional rank, in (0, 1], of `tradeval_up` across the published instruments in the same market and interval. |
| `tradeval_up_zscore` | `double` | Cross-sectional z-score of `tradeval_up` across the published instruments in the same market and interval. |
| `tradeval_flat_rank` | `double` | Cross-sectional rank, in (0, 1], of `tradeval_flat` across the published instruments in the same market and interval. |
| `tradeval_flat_zscore` | `double` | Cross-sectional z-score of `tradeval_flat` across the published instruments in the same market and interval. |
| `tradeval_down_rank` | `double` | Cross-sectional rank, in (0, 1], of `tradeval_down` across the published instruments in the same market and interval. |
| `tradeval_down_zscore` | `double` | Cross-sectional z-score of `tradeval_down` across the published instruments in the same market and interval. |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
