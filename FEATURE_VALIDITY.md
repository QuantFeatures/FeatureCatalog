# Feature validity

How to tell valid values from unavailable ones in the published data.

- **Unavailable values are NaN.** Every column is always present; there are no nulls. In floating-point fields, NaN means the value is unavailable or not validly computable, for example a standard deviation in an interval with a single trade. NaN is never zero.
- **Counts are always defined.** Integer count fields (`ntrade`, `nquote`, `num_*`, `liq_count`, …) are never NaN. A zero count is a valid zero: no qualifying events occurred in the interval.
- **Missing rows are not zero activity.** A missing file, or a missing instrument row within a file, means no published record. See [Coverage](docs/COVERAGE.md) for instruments listed after the first sample day.
- **Sample-day boundary.** The sample covers isolated days, so the first interval of each sample day (00:00–01:00 UTC) lacks the preceding day's history. Features that look back before the interval can be NaN or differ there. See [Data specification](docs/DATA_SPECIFICATION.md#sample-day-boundary).

Keep NaN values as they are, inspect coverage before analysis, and avoid forward filling unless your research design explicitly supports it.
