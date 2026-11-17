# Countries (ISO 3166-1)

Alpha-2, alpha-3 and numeric country codes with English and French short names.
Codes come from GeoNames’ ISO 3166-1 fields; names from Unicode CLDR. The set
matches the 250 territories in `tr-address-country` (including user-assigned
XK / Kosovo).

| File | Rows | Description |
| --- | --- | --- |
| [`countries.csv`](countries.csv) | 250 | Current codes and short names |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Notes

- Codes are strings. Keep numeric codes zero-padded (`008`, not `8`).
- `XK` (Kosovo) is a widely used **user-assigned** code, not an officially
  assigned ISO 3166-1 entry; `numeric_code` is empty for it.
- Obsolete GeoNames rows `CS` and `AN` are omitted (no CLDR short name).
- For Turkish names, capitals and calling codes see
  [`tr-address-country`](../../countries/TR/address/country/).

## Sources

- [GeoNames countryInfo.txt](https://download.geonames.org/export/dump/countryInfo.txt)
  (CC BY 4.0), retrieved 2026-11-16
- [Unicode CLDR territories (en, fr)](https://github.com/unicode-org/cldr-json/tree/main/cldr-json/cldr-localenames-full/main)
- [ISO 3166 country codes](https://www.iso.org/iso-3166-country-codes.html)
  (codes may be used freely in lists and software)

Checked for: 250 rows; unique alpha-2/alpha-3; numeric unique where present;
codes align with `tr-address-country`.
