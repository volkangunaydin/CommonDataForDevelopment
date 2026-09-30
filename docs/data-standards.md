# Data standards

These rules keep every dataset in the repository predictable, so that a
developer or an AI agent who has used one dataset can use any other without
reading its documentation first.

## Dataset layout

A dataset is a folder:

```
<dataset>/
├── datapackage.json   # metadata, sources, field schema
├── README.md          # what it is, how to use it, caveats
└── <resource>.csv     # one or more data files (.csv or .json)
```

Folder and file names are lower case, in English, with words separated by
hyphens: `tax-offices/tax-offices.csv`.

The dataset `name` in `datapackage.json` is its unique id across the repository:

| Scope | Pattern | Example |
| --- | --- | --- |
| World | `world-<dataset>` | `world-currencies` |
| Country | `<cc>-<domain>-<dataset>` | `tr-banking-banks` |
| Topic | `<topic>-<dataset>` | `ubl-document-types` |

## Files

- **Encoding:** UTF-8 without BOM.
- **Line endings:** LF. The file ends with a newline.
- **CSV** for tabular data:
  - Comma separated, header row first.
  - Quote a value with double quotes only when it contains a comma, a quote or a
    line break; escape a quote by doubling it.
  - Empty value means "not applicable" or "unknown". Do not write `NULL`, `N/A`
    or `-`.
- **JSON** for data that is nested by nature:
  - Two-space indentation.
  - The top level is an array of objects, or an object whose purpose is
    documented in the dataset README.
- One canonical file per resource. Do not commit the same data in two formats;
  converted formats can be produced by tooling.

## Fields

- Names are English, `snake_case`, singular: `tax_office_code`, not
  `VergiDairesiKodu` or `codes`.
- Use the same name for the same concept everywhere:

  | Field | Meaning |
  | --- | --- |
  | `code` | The primary code of the row within its own code list |
  | `name` | Name in the local or official language |
  | `name_en` | English name, when one exists and differs |
  | `country_code` | ISO 3166-1 alpha-2 |
  | `valid_from`, `valid_to` | Validity dates of the row |

- A field that references another dataset is named after what it references:
  `province_code` in a districts dataset points to `code` in the provinces
  dataset. Document the reference in the field description.
- Every field has a `description` in `datapackage.json`.

## Values

- **Codes are strings.** Preserve leading zeros and do not strip padding.
- **Text** is kept in the original language and script with correct characters
  (`İstanbul`, not `Istanbul`). Do not upper-case or transliterate. Add a
  separate `name_en` or `name_ascii` field if needed.
- **Dates:** ISO 8601, `YYYY-MM-DD`.
- **Booleans:** `true` / `false`.
- **Numbers:** dot as decimal separator, no thousands separator. Rates are
  written as percentages in a field whose name says so (`rate_percent`: `20`).
- **International codes** where they exist:

  | Concept | Standard |
  | --- | --- |
  | Country | ISO 3166-1 alpha-2 |
  | Subdivision | ISO 3166-2 |
  | Currency | ISO 4217 |
  | Language | ISO 639-1, BCP 47 for locales |
  | Time zone | IANA tz database name |
  | Unit of measure | UN/ECE Recommendation 20 |
  | Bank | BIC (ISO 9362) alongside the national code |

- **Row order** is stable and sorted by the primary key, so diffs show only real
  changes.

## Metadata

`datapackage.json` follows the [Frictionless Data Package](https://datapackage.org/)
standard. Required properties in this repository:

| Property | Notes |
| --- | --- |
| `name` | Unique id, see naming patterns above |
| `title`, `description` | In English |
| `version` | See [Versioning](#versioning) |
| `licenses` | The licence of the data |
| `sources` | At least one, each with `title` and `path` (URL) |
| `resources[].schema.fields` | Every field with `name`, `type`, `description` |
| `resources[].schema.primaryKey` | For tabular resources |

Use [`templates/dataset/datapackage.json`](../templates/dataset/datapackage.json)
as a starting point.

## Versioning

Each dataset has its own `MAJOR.MINOR.PATCH` version:

| Change | Bump |
| --- | --- |
| Field removed or renamed, meaning of a field or code changed, file moved | MAJOR |
| Field added, rows added or retired following a change at the source | MINOR |
| Correction of an error | PATCH |

Datasets below `1.0.0` may still change shape.

## Retired entries

Reference data outlives its entries: old invoices still carry the code of a bank
that has since merged or a tax office that has closed.

- Do not delete a retired entry when the dataset has `valid_from` / `valid_to`
  fields. Set `valid_to` instead.
- Never assign a retired code to a new meaning.
