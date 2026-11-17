# UBL-TR invoice type codes (e-Fatura)

The `InvoiceTypeCode` values published by GİB for Turkish e-invoices (e-Fatura
and e-Arşiv Fatura). Used for the invoice-type pick list in invoicing software
and to map an internal document type to the code the UBL-TR schematron accepts.

| File | Rows | Description |
| --- | --- | --- |
| [`invoice-type-codes.csv`](invoice-type-codes.csv) | 20 | Guide codes plus two Hal Kayıt codes from the schematron |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `SATIS` | Value for `cbc:InvoiceTypeCode` |
| `name` | `Her türlü mal ve hizmet…` | Turkish description from the guide |
| `in_guide` | `true` | Named in Kod Listeleri §1.4 |
| `in_schematron` | `true` | In `InvoiceTypeCodeList` |
| `yatirim_tesvik_earchive` | `false` | Also in the Yatırım Teşvik e-Arşiv list |

## Notes

- **Descriptions come from prose.** Section 1.4 is a paragraph, not a table; the
  `name` field keeps the meaning of each clause without inventing shorter labels.
- **`HKSSATIS` and `HKSKOMISYONCU`.** Accepted by the schematron but not named in
  §1.4 (the guide only mentions `KOMISYONCU` for Hal Kayıt). `name` is empty;
  do not invent a label.
- **Yatırım Teşvik e-Arşiv.** The five `YTB*` codes are also listed in
  `YatirimTesvikEArsivInvoiceTypeCodeList`.

## Sources

- [UBL-TR Kod Listeleri, version 1.43, July 2026](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/UBLTR_1.2.1_Kilavuzlar.zip),
  section 1.4 InvoiceTypeCode, GİB, retrieved 2026-11-16.
- [e-Fatura Paketi](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/e-FaturaPaketi%20(29).zip),
  `schematron/UBL-TR_Codelist.xml`, retrieved 2026-11-16.

Checked for: 20 unique codes; every `InvoiceTypeCodeList` value present; guide
flags and Yatırım Teşvik flags matching the schematron.
