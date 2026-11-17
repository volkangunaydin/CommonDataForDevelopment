# UBL-TR scenario / ProfileID codes (e-Fatura)

The `ProfileID` values published by the Revenue Administration (Gelir İdaresi
Başkanlığı, GİB) that name the business process of a Turkish e-document
(e-Fatura, e-Arşiv Fatura, e-İrsaliye). Used to pick the correct scenario when
creating an e-document and to check which processes the UBL-TR schematron
accepts for invoices, e-archive invoices and despatch advice.

| File | Rows | Description |
| --- | --- | --- |
| [`profile-ids.csv`](profile-ids.csv) | 16 | One row per ProfileID in the guide |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `TEMELFATURA` | Value for `cbc:ProfileID` |
| `name` | `Temel Fatura sürecini belirtir.` | Turkish description from the guide |
| `schematron_lists` | `invoice;display` | Which schematron ProfileID lists accept it |

`schematron_lists` values:

| Token | Schematron let | Typical document |
| --- | --- | --- |
| `invoice` | `ProfileIDType` | e-Fatura |
| `earchive` | `ProfileIDTypeEarchive` | e-Arşiv Fatura |
| `despatch` | `ProfileIDTypeDespatchAdvice` | e-İrsaliye |
| `display` | `ProfileIDTypeGoruntuleme` | display / viewing package |

## Notes

- **`STDKODFATURA` is in the guide only.** The code list names Standart Kod
  Fatura, but none of the four schematron ProfileID lists accept it (package
  retrieved 2026-11-16).
- **`EARSIVFATURA` is not in `ProfileIDType`.** The invoice list covers the
  e-Fatura processes; e-Arşiv uses `ProfileIDTypeEarchive` (and
  `ProfileIDTypeGoruntuleme` for display).
- **Despatch advice** uses `TEMELIRSALIYE`, `HKSIRSALIYE` and `IDISIRSALIYE`
  only.

## Sources

- [UBL-TR Kod Listeleri, version 1.43, July 2026](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/UBLTR_1.2.1_Kilavuzlar.zip),
  section 2.2 Senaryo (ProfileID), GİB, retrieved 2026-11-16.
- [e-Fatura Paketi](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/e-FaturaPaketi%20(29).zip),
  `schematron/UBL-TR_Codelist.xml`, retrieved 2026-11-16.

Codes and descriptions were taken from the PDF text and checked against the
schematron lists: 16 guide rows; unique codes; `schematron_lists` matches the
four ProfileID lets.
