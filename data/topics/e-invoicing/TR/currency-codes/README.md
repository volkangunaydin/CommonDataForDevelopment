# UBL-TR currency codes (e-Fatura)

The currency codes that the Revenue Administration (GİB) accepts in Turkish
e-documents (e-Fatura, e-Arşiv Fatura and the other UBL-TR documents). A
document whose `DocumentCurrencyCode`, `TaxCurrencyCode`, `PricingCurrencyCode`,
`PaymentCurrencyCode`, `PaymentAlternativeCurrencyCode` or `currencyID`
attribute is not in this list fails the GİB schematron check.

| File | Rows | Description |
| --- | --- | --- |
| [`currency-codes.csv`](currency-codes.csv) | 193 | One row per accepted code |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `TRY` | ISO 4217 alphabetic code, unique |
| `iso_4217_status` | `current` | `current` (in ISO 4217 List One) or `withdrawn` (only in the historic list) |

For names, numeric codes and decimal places join `code` with
[`world-currencies`](../../../../world/currencies/).

## Notes

- **Not identical to ISO 4217.** The list contains all 178 current ISO 4217
  codes and 15 codes that ISO 4217 has withdrawn: `ANG`, `BGN`, `CUC`, `EEK`,
  `GWP`, `HRK`, `LTL`, `LVL`, `SLL`, `STD`, `USS`, `VEF`, `XFU`, `ZMK`, `ZWL`.
  GİB accepts them; a system that validates only against current ISO 4217 will
  reject documents that GİB accepts.
- The list is the `CurrencyCodeList` variable in `schematron/UBL-TR_Codelist.xml`
  of the e-Fatura package. GİB changes it with package updates; check the
  package for changes after the date below.
- `iso_4217_status` reflects the ISO lists used for `world-currencies`
  (List One published 2026-09-17).

## Sources

- [e-Fatura Paketi](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/e-FaturaPaketi%20(29).zip), `schematron/UBL-TR_Codelist.xml`, from [GİB e-Fatura Mevzuat](https://ebelge.gib.gov.tr/efaturamevzuat.html), retrieved 2026-11-05 (package history up to 2026-07-01)
- ISO 4217 List One and List Three, for `iso_4217_status`

The code list was extracted with a script and checked: 193 codes, no duplicates,
every code found in ISO 4217 List One or List Three.
