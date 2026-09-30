# Provinces of Türkiye

The 81 provinces (*il*) of Türkiye.

| File | Rows | Description |
| --- | --- | --- |
| [`provinces.csv`](provinces.csv) | 81 | One row per province |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `34` | Two-digit province code, zero-padded. Identical to the vehicle plate code. Always treat it as a string. |
| `iso_3166_2` | `TR-34` | ISO 3166-2 subdivision code. |
| `name` | `İstanbul` | Official province name in Turkish. |

## Notes

- Names use Turkish spelling (`İstanbul`, `Şanlıurfa`, `Iğdır`). Use a Turkish-aware
  collation (`tr-TR`) for sorting and case conversion: `i`/`İ` and `ı`/`I` are
  different letters.
- ISO 3166-2 spells `TR-30` as "Hakkâri". This dataset uses "Hakkari", the form
  used by Turkish public institutions.

## Source

- [ISO 3166-2:TR](https://www.iso.org/obp/ui/#iso:code:3166:TR)
