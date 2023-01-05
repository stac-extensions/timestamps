# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

### Changed

### Deprecated

### Removed

### Fixed

## [v1.1.0] - 2023-01-05

### Changed

- All timestamps must be in UTC ([#1095](https://github.com/radiantearth/stac-spec/issues/1095))
- The extension can now be used mostly everywhere (e.g. Catalog, Collections, Items, Assets, Links), which aligns with STAC common metadata.

### Fixed

- Clarified scope
- Clarified that no field is required, which is also not enforced in the schema
- JSON Schema checks `stac_extensions` field in Collections

## [v1.0.0] - 2021-03-04

### Fixed

- JSON Schema validates assets, item assets definitions and collection assets

[Unreleased]: <https://github.com/stac-extensions/timestamps/compare/v1.1.0...HEAD>
[v1.1.0]: <https://github.com/stac-extensions/timestamps/compare/v1.0.0...v1.1.0>
[v1.0.0]: <https://github.com/stac-extensions/timestamps/tree/v1.0.0>
