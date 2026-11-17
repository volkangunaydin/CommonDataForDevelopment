# UBL-TR tax type codes (e-Fatura)

The `TaxTypeCode` values used under `TaxTotal` on Turkish e-invoices for the
tax itself (KDV, ÖTV, damga vergisi and others). Not the withholding codes:
those live in [`withholding-codes`](../withholding-codes/) and apply under
`WithholdingTaxTotal`.

| File | Rows | Description |
| --- | --- | --- |
| [`tax-type-codes.csv`](tax-type-codes.csv) | 31 | Guide list plus two schematron-only codes |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `0015` | Four-digit code for `TaxTypeCode` under `TaxTotal` |
| `name` | `Gerçek Usulde Katma Değer Vergisi` | Turkish name from the guide |
| `abbreviation` | `KDV GERCEK` | Short label from the guide |
| `in_guide` | `true` | In Kod Listeleri §1.9 |
| `in_schematron` | `true` | In schematron `TaxType` |

## Notes

- **Withholding is a different list.** Codes `601`–`627` and `801`–`825` belong
  under `WithholdingTaxTotal`; see [`withholding-codes`](../withholding-codes/).
- **`0059` and `9015`.** Accepted by the schematron `TaxType` list but not named
  in the Vergi Kodları Listesi of the guide (or elsewhere in the e-Fatura
  package retrieved 2026-11-16). `name` and `abbreviation` are empty; do not
  invent labels.
- **Codes are strings.** Keep leading zeros (`0003`, not `3`).

## Sources

- [UBL-TR Kod Listeleri, version 1.43, July 2026](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/UBLTR_1.2.1_Kilavuzlar.zip),
  section 1.9 TaxTypeCode, Vergi Kodları Listesi, GİB, retrieved 2026-11-16.
- [e-Fatura Paketi](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/e-FaturaPaketi%20(29).zip),
  `schematron/UBL-TR_Codelist.xml` (`TaxType`), retrieved 2026-11-16.

Checked for: 31 unique codes matching `TaxType`; 29 named from the guide; two
schematron-only codes left unnamed.
