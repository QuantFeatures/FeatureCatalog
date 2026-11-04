# FundingPaid
The funding rate paid at each hourly settlement and its premium component.
## Availability
- **Input:** Funding settlements (exchange API)
- **Markets:** Perpetual only
- **Feature family:** Funding
- **Coverage, Hyperliquid continuous sample (`3.1.0`):** every UTC day, 2026-01-01 through 2026-11-02; 7,344 perp hourly files.
## Interpretation and disclosure
Each row is one instrument in one interval. Each definition states what the field measures and its unit; computation methods and implementation details are proprietary.
## Notes
- One settlement per interval: Hyperliquid pays funding every hour, at the end of the interval.
- Rates are per hour, not annualised; a positive rate means long positions pay short positions.
- Values are the settlements in the exchange's public funding history. `FundingRate` instead summarises the predicted rate reported between settlements.
## Fields
| Field | Physical type | Public definition |
| --- | --- | --- |
| `start_time_utc` | `timestamp[us, tz=UTC]` | UTC start of the half-open measurement interval. |
| `end_time_utc` | `timestamp[us, tz=UTC]` | UTC end of the half-open measurement interval. |
| `exch` | `string` | Normalized exchange identifier. |
| `type` | `string` | Normalized market type, such as spot or perpetual. |
| `base` | `string` | Base asset symbol. |
| `quote` | `string` | Quote asset symbol. |
| `funding_rate` | `double` | Funding rate paid at the settlement that ends the interval, as a fraction of position value per hour. |
| `premium` | `double` | Premium value the exchange reports with that settlement, as a fraction. |
| `funding_time_utc` | `timestamp[us, tz=UTC]` | UTC time the exchange reports for the settlement; within a second after `end_time_utc`. |

## Use in research

Use `end_time_utc` as the timestamp at which an interval is complete. Treat NaN as unavailable rather than zero, and see the sample-day boundary and data-quality notes in [DATA_SPECIFICATION.md](../DATA_SPECIFICATION.md).
