# Timestamps Extension Specification

- **Title:** Timestamps
- **Identifier:** <https://stac-extensions.github.io/timestamps/v1.0.0/schema.json>
- **Field Name Prefix:** -
- **Scope:** Item, Collection
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Pilot
- **Owner**: @m-mohr
- **History**: [Prior to March 2, 2021](https://github.com/radiantearth/stac-spec/commits/v1.0.0-rc.1/extensions/timestamps)

This document explains the fields of the Timestamps Extension to all STAC entities.
Allows to specify numerous timestamps for assets and metadata in addition to [`created`, `updated` and `datetime` (incl. start and end)](https://github.com/radiantearth/stac-spec/tree/master/item-spec/common-metadata.md#date-and-time).

- Examples:
  - [Catalog example](examples/catalog.json)
  - [Collection example](examples/collection.json)
  - [Item example](examples/item.json)
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## Fields

The fields in the table below can be used in these parts of STAC documents:
- [x] Catalogs
- [x] Collections
- [x] Item Properties (incl. Summaries in Collections)
- [x] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections)
- [x] Links

| Field Name  | Type   | Description |
| ----------- | ------ | ----------- |
| published   | string | Date and time the corresponding data (see below) was published the first time, in UTC. |
| expires     | string | Date and time the corresponding data (see below) expires (is not valid any longer), in UTC. |
| unpublished | string | Date and time the corresponding data (see below) was unpublished, in UTC. |

All timestamps MUST be formatted according to [RFC 3339, section 5.6](https://tools.ietf.org/html/rfc3339#section-5.6).

**NOTE:** The timestamps have different meaning depending on where they are used.
If those fields are available in a Collection, in a Catalog (both top-level), or in a Item (in the `properties`),
the fields refer the metadata (e.g., when the STAC metadata was published).
Having those fields in the Assets or Links, they refer to the actual data linked to (e.g., when the asset was published).

### Lifecycle

An overview over the lifecycle of data and their corresponding timestamps:

1. Data capture, start: `start_datetime`
2. Data capture, often center: `datetime`
3. Data capture, end: `end_datetime`
4. Data first modified (stored): `created`
5. Data last modified: `updated`
6. Data first published: `published`
7. Data last published: N/A
8. Data valid until: `expires`
9. Data removed / unpublished: `unpublished`

## Contributing

All contributions are subject to the
[STAC Specification Code of Conduct](https://github.com/radiantearth/stac-spec/blob/master/CODE_OF_CONDUCT.md).
For contributions, please follow the
[STAC specification contributing guide](https://github.com/radiantearth/stac-spec/blob/master/CONTRIBUTING.md) Instructions
for running tests are copied here for convenience.

### Running tests

The same checks that run as checks on PR's are part of the repository and can be run locally to verify that changes are valid. 
To run tests locally, you'll need `npm`, which is a standard part of any [node.js installation](https://nodejs.org/en/download/).

First you'll need to install everything with npm once. Just navigate to the root of this repository and on 
your command line run:
```bash
npm install
```

Then to check markdown formatting and test the examples against the JSON schema, you can run:
```bash
npm test
```

This will spit out the same texts that you see online, and you can then go and fix your markdown or examples.

If the tests reveal formatting problems with the examples, you can fix them with:
```bash
npm run format-examples
```
