# Countries with Turkish names

Countries and territories with their Turkish names, ISO 3166-1 codes,
international calling code and capital (in Turkish, with coordinates). Typically
used for country pick lists, phone number inputs and address forms in
Turkish-language applications.

| File | Rows | Description |
| --- | --- | --- |
| [`countries.csv`](countries.csv) | 250 | One row per country or territory |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `DE` | ISO 3166-1 alpha-2 code |
| `alpha_3_code` | `DEU` | ISO 3166-1 alpha-3 code |
| `numeric_code` | `276` | ISO 3166-1 numeric code, zero-padded (`004`). Always treat it as a string. |
| `name` | `Almanya` | Country name in Turkish |
| `name_en` | `Germany` | Country name in English |
| `calling_code` | `49` | International calling code without `+`; see notes |
| `capital` | `Berlin` | Capital in Turkish |
| `capital_en` | `Berlin` | Capital in English |
| `capital_latitude` | `52.52437` | Latitude of the capital, WGS 84 |
| `capital_longitude` | `13.41053` | Longitude of the capital, WGS 84 |
| `capital_geonames_id` | `2950159` | GeoNames record of the capital |
| `continent_code` | `EU` | `AF`, `AN`, `AS`, `EU`, `NA`, `OC`, `SA` |
| `currency_code` | `EUR` | Main currency, ISO 4217; see [world-currencies](../../../../world/currencies/) |
| `tld` | `.de` | Country-code internet domain |

## Notes

- **Coverage.** The 249 ISO 3166-1 entries plus Kosovo (`XK`, `XKX`), which has
  user-assigned codes and no numeric code. Dissolved entries that GeoNames still
  lists (Netherlands Antilles `AN`, Serbia and Montenegro `CS`) are left out.
- **Names** are the CLDR defaults, for example `Çin Hong Kong ÖİB`,
  `Filistin Bölgeleri`, `Kongo - Kinşasa`. CLDR also has short or variant forms
  (`Hong Kong`, `Filistin`, `Kongo Demokratik Cumhuriyeti`, `ABD`) that are not
  included. Use a Turkish-aware collation (`tr-TR`) for sorting.
- **Calling codes.** Territories that share a code carry their area code after a
  hyphen: `1-268` is Antigua and Barbuda (+1 268), `44-1481` is Guernsey. Two
  codes are separated by a semicolon (`1-809;1-829` for the Dominican Republic).
  The value is empty for Antarctica, Bouvet Island, South Georgia, Heard and
  McDonald Islands, French Southern Territories and Kosovo, because GeoNames has
  no code for them.
- **Capitals** follow GeoNames, including disputed cases: Jerusalem for Israel and
  East Jerusalem for Palestine. Six entries have no capital (`AQ`, `BQ`, `BV`,
  `HM`, `TK`, `UM`). GeoNames' outdated names are replaced by the name of the
  record it marks as capital: Astana (Kazakhstan), Ngerulmud (Palau).
- **Turkish capital names** come from Wikidata, preferring the title of the
  Turkish Wikipedia article (`Kâbil`, `Vagadugu`, `Punom Pen`), then the Turkish
  label. Names used unchanged in Turkish (`Oslo`, `Abuja`) may only exist as a
  language-neutral label. Empty for South Georgia (Wikidata gives King Edward
  Point, GeoNames Grytviken) and Hong Kong (no matching item).
- **Coordinates** are the point of the GeoNames capital record, not a boundary
  or centroid. Diego Garcia (`IO`) is the atoll.
- **Currency** is the main currency as listed by GeoNames; countries with more
  than one legal tender (Panama, Cuba) show one. Bulgaria is `EUR` following
  ISO 4217, where GeoNames still lists `BGN`.
- The sources are snapshots of 2026-11-05.

## Source

- [GeoNames](https://download.geonames.org/export/dump/) (`countryInfo.txt`,
  `cities500.zip`, `IO.zip`), licensed under CC BY 4.0. Credit: GeoNames,
  https://www.geonames.org
- [Unicode CLDR 49](https://github.com/unicode-org/cldr-json), territory names in
  Turkish and English, under the
  [Unicode License v3](https://www.unicode.org/license.txt). Copyright © Unicode, Inc.
- [Wikidata](https://www.wikidata.org/), CC0
- ISO 4217 List One, via [world-currencies](../../../../world/currencies/)

Capitals were taken from the GeoNames record marked as national capital (PPLC)
for each country; four not marked that way were matched by GeoNames ID
(Laayoune, Jerusalem, East Jerusalem, Diego Garcia). A Turkish name was accepted
only for a Wikidata item that carries the same GeoNames ID or lies within 30 km
of the GeoNames point. Codes were checked against `countryInfo.txt` row by row,
and every currency code against `world-currencies`.
