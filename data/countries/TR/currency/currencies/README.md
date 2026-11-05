# Currencies with Turkish names

ISO 4217 currency codes with their Turkish names and the symbols used in
Turkish, for currency pick lists, price formatting and e-invoicing in
Turkish-language applications.

| File | Rows | Description |
| --- | --- | --- |
| [`currencies.csv`](currencies.csv) | 193 | One row per code |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `TRY` | ISO 4217 alphabetic code, unique |
| `numeric_code` | `949` | ISO 4217 numeric code, zero-padded |
| `name` | `Türk lirası` | Turkish name (CLDR) |
| `name_en` | `Turkish Lira` | English name (CLDR) |
| `symbol` | `₺` | Symbol in Turkish (CLDR), may be empty |
| `symbol_narrow` | `₺` | Narrow symbol (CLDR), may be empty |
| `minor_units` | `2` | Decimal places (ISO 4217), may be empty |
| `iso_4217_status` | `current` | `current` or `withdrawn` |
| `e_invoice_accepted` | `true` | Accepted by the GİB UBL-TR schematron |

## Notes

- **Scope.** The 178 current ISO 4217 codes and the 15 withdrawn codes that GİB
  still accepts in e-invoices (`BGN`, `HRK`, `VEF` and others). Other historic
  codes, such as `TRL`, are in
  [`world-currencies`](../../../../world/currencies/) only.
- **Names** follow Turkish capitalisation as in CLDR: `ABD doları`,
  `Türk lirası`, `İngiliz sterlini`. Some names carry a period to tell apart
  codes of the same currency (`Sierra Leone leonesi (1964–2022)`).
- **Missing names.** CLDR 49 has no Turkish name for `UYW`, `VED` and `XAD`, and
  no English name for `XAD`. These fields are left empty rather than
  translated; the ISO 4217 English names are in `world-currencies`.
- **Symbols.** `symbol` is what CLDR shows in Turkish text; it is empty for most
  currencies, which are then shown by code (`AFN`). The narrow symbol is
  ambiguous on purpose (`$` for USD, AUD, CAD) and only suits contexts where the
  currency is known. CLDR also lists `TL` as a variant symbol for `TRY`.
- **minor_units** is empty for precious metals and units of account (ISO gives
  N.A.) and for the withdrawn codes.

## Sources

- [Unicode CLDR 49](https://github.com/unicode-org/cldr-json/tree/49.0.0/cldr-json/cldr-numbers-full/main), `cldr-numbers-full`, `tr` and `en` `currencies.json`: names and symbols (Unicode License v3)
- ISO 4217 List One and List Three, via [`world-currencies`](../../../../world/currencies/): codes, numeric codes, minor units, status
- GİB e-Fatura package, via [`e-invoicing-tr-currency-codes`](../../../../topics/e-invoicing/TR/currency-codes/): `e_invoice_accepted`

Built with a script joining the three on `code` and checked: 193 rows, unique
codes, every code present in ISO 4217, Turkish names for 190 codes.
