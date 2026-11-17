# UBL-TR INCOTERMS delivery term codes (e-Fatura)

Codes for `DeliveryTerms/ID` with `schemeID="INCOTERMS"` on Turkish e-documents,
with Turkish and English labels from Kod Listeleri §1.14.

| File | Rows | Description |
| --- | --- | --- |
| [`incoterms-codes.csv`](incoterms-codes.csv) | 15 | One row per guide / schematron code |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `FOB` | INCOTERMS code |
| `name` | `Gemide Masrafsız` | Turkish label from the guide |
| `name_en` | `Free On Board` | English label from the guide |
| `in_schematron` | `true` | In `DeliveryTermCodeList` |

## Notes

- English spelling follows the guide (`Cost,İnsurance And Freight` for CIF).
- The list mixes current and withdrawn Incoterms as published by GİB; it is not
  a full ICC Incoterms® edition.

## Sources

- [UBL-TR Kod Listeleri V1.43](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/UBLTR_1.2.1_Kilavuzlar.zip), §1.14, retrieved 2026-11-16.
- [e-Fatura Paketi](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/e-FaturaPaketi%20(29).zip), retrieved 2026-11-16.
