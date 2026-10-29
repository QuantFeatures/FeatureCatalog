# Feature versioning

Every dataset carries a feature version, for example `2.0.0`, in its file path and manifest.

- **Released files never change.** A correction or a change in definition is published as a new version; earlier versions remain available unchanged.
- **Version numbers follow semantic versioning.** A major version (`2.0.0`) changes file layout, timestamp labels, or feature definitions in ways that are not backward compatible. A minor version adds modules or features. A patch version fixes data without changing definitions.
- **Features are identified by module and feature name**, for example `TradeFlow.vwap_buy`. A published name keeps its meaning within a major version.

Do not combine files from different versions by filename alone. Version `1.0.0` labels files by interval end time; version `2.0.0` labels them by interval start time (see [Data specification](docs/DATA_SPECIFICATION.md)).
