# Timestamps Extension Specification

- **Title:** Timestamps
- **Identifier:** <https://stac-extensions.github.io/timestamps/v1.0.0/schema.json>
- **Field Name Prefix:** -
- **Scope:** Item, Collection
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @m-mohr
- **History**: [Prior to March 2, 2021](https://github.com/radiantearth/stac-spec/commits/v1.0.0-rc.1/extensions/timestamps)

This document explains the fields of the Timestamps Extension to a STAC Item.
Allows to specify numerous timestamps for assets and metadata in addition to [`created`, `updated` and `datetime` (incl. start and end)](https://github.com/radiantearth/stac-spec/tree/master/item-spec/common-metadata.md#date-and-time).

- Examples:
  - [Item example](examples/item.json): Shows the basic usage of the extension in a STAC Item
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## Item Properties Fields

| Field Name  | Type   | Description |
| ----------- | ------ | ----------- |
| published   | string | Date and time the corresponding data (see below) was published the first time. |
| expires     | string | Date and time the corresponding data (see below) expires (is not valid any longer). |
| unpublished | string | Date and time the corresponding data (see below) was unpublished. |

All timestamps MUST be formatted according to [RFC 3339, section 5.6](https://tools.ietf.org/html/rfc3339#section-5.6).

The timestamps have different meaning depending on where they are used.
If those fields are available in the Item `properties`, it's referencing to the timestamps valid for of the metadata.
Having those fields in the Item `assets` refers to the timestamps valid for the actual data linked to in the Asset Object.

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

## Outlook

Once these fields get broadly adopted, it is planned to move them to Common Metadata and place them together with `created` and `updated`.
As this extension doesn't have a prefix, it doesn't lead to any breaking changes and the thus it is only a structural change for the specification.

This fields - together with `created` and `updated` - also seem relevant for STAC Collections and may be adopted there, too.

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
