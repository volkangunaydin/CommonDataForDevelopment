# Currencies (ISO 4217)

ISO 4217 currency and fund codes: the alphabetic code used in prices, invoices
and payment messages (`TRY`, `EUR`), its numeric code and the number of decimal
places, together with the countries that use each code and the codes and names
that have been withdrawn.

| File | Rows | Description |
| --- | --- | --- |
| [`currencies.csv`](currencies.csv) | 178 | One row per current code |
| [`currency-entities.csv`](currency-entities.csv) | 277 | Which countries and entities use which code |
| [`historic-currencies.csv`](historic-currencies.csv) | 169 | Withdrawn codes and names |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

`currencies.csv`

| Field | Example | Description |
| --- | --- | --- |
| `code` | `TRY` | Alphabetic code, unique |
| `numeric_code` | `949` | Numeric code, zero-padded (`008`), unique |
| `name` | `Turkish Lira` | Name as published, in English |
| `minor_units` | `2` | Decimal places; empty for precious metals, units of account, `XTS`, `XXX` |
| `fund` | `false` | `true` for fund codes such as `CLF`, `UYI` |

`currency-entities.csv`

| Field | Example | Description |
| --- | --- | --- |
| `currency_code` | `TRY` | References `code` in `currencies.csv` |
| `entity_name` | `TÜRKİYE` | Entity name as published |

`historic-currencies.csv`

| Field | Example | Description |
| --- | --- | --- |
| `code` | `TRL` | Alphabetic code |
| `numeric_code` | `792` | Numeric code, may be empty |
| `name` | `Old Turkish Lira` | Name as published |
| `entity_name` | `TURKEY` | Entity name at the time of withdrawal |
| `withdrawal_date` | `2005-12` | As published, usually `YYYY-MM` |
| `fund` | `false` | Fund code |

## Notes

- **Codes are strings.** Numeric codes keep their leading zeros.
- **Turkish lira.** `TRY` (949) is current. The historic list has `TRL` (792,
  Old Turkish Lira, withdrawn 2005-12) and `TRY` under its former name New
  Turkish Lira (withdrawn 2009-01, when the name became Turkish Lira). Old
  documents may carry `TRL`.
- **Historic entries are not only dead codes.** An entry is added when a code is
  withdrawn for one entity (`EUR` for Serbia and Montenegro), renamed, or
  replaced. Check `currencies.csv` to see whether a code is still current.
- **Entities** are named exactly as in ISO 4217, upper case with suffixes such as
  `(THE)`. They are not mapped to ISO 3166 country codes. Antarctica, Palestine
  and South Georgia appear in ISO 4217 with "No universal currency" and no code;
  they are not included.
- **Rows are sorted** by code, then entity name, by Unicode code point.
- ISO 4217 is maintained by SIX on behalf of ISO; the codes and names remain
  subject to ISO's terms.

## Sources

- [ISO 4217 List One](https://www.six-group.com/dam/download/financial-information/data-center/iso-currrency/lists/list-one.xml) (current, published 2026-09-17)
- [ISO 4217 List Three](https://www.six-group.com/dam/download/financial-information/data-center/iso-currrency/lists/list-three.xml) (historic, published 2026-01-01)

The XML files were converted with a script and checked against the source: 280
List One entries (277 with a code, 178 distinct codes, each with a single name,
numeric code and minor units), 169 List Three entries, unique numeric codes in
`currencies.csv`.
