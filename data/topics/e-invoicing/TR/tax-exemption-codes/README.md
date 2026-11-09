# UBL-TR tax exemption reason codes (e-Fatura)

The codes that Turkish e-documents (e-Fatura, e-Arşiv Fatura) carry in
`cbc:TaxExemptionReasonCode` when a line or invoice is exempt from VAT or another
tax, or is invoiced on a special tax base, together with the official Turkish
description from the Revenue Administration (Gelir İdaresi Başkanlığı, GİB).
Typically used for the exemption reason pick list of invoicing and ERP software.

| File | Rows | Description |
| --- | --- | --- |
| [`tax-exemption-codes.csv`](tax-exemption-codes.csv) | 112 | One row per code |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `301` | Three-digit code; keep leading zeros (`001`) |
| `name` | `11/1-a Mal İhracatı` | Turkish description as printed by GİB |
| `list` | `kdv_full` | Code list the code belongs to, see below |
| `usage_note` | | GİB's usage note, only for `151`, `351` and `555` |
| `schematron_status` | `accepted` | `accepted` or `investment_incentive_only` |

Rows by list:

| `list` | GİB list | Codes | Rows |
| --- | --- | --- | --- |
| `kdv_partial` | Kısmi İstisna Kodları | 201–250 | 39 |
| `kdv_full` | Tam İstisna Kodları | 301–351 | 46 |
| `other` | Diğer İşlem Türü Kodları | 555 | 1 |
| `otv` | ÖTV İstisna Kodları | 101–151 | 9 |
| `accommodation_tax` | Konaklama Vergisi İstisna Kodları | 001 | 1 |
| `special_base` | Özel Matrah Kodları | 801–812 | 12 |
| `export_registered` | İhraç Kayıtlı Satışlar ile DİİB ve Geçici Kabul Rejimi Kapsamındaki Satış Kodları | 701–704 | 4 |

## Notes

- **Which invoice type.** The guide ties the exemption lists to invoices of
  type `ISTISNA`, the special base codes to `OZELMATRAH` and the
  export-registered codes to `IHRACKAYITLI`. The schematron is a little wider:
  the exemption codes (except `151`, `351` and `555`) are accepted on
  `ISTISNA`, `IADE`, `IHRACKAYITLI`, `SGK`, `YTBISTISNA` and `YTBIADE`
  invoices; the special base codes on `OZELMATRAH`, `IADE` and `SGK`; the
  export-registered codes on `IHRACKAYITLI`, `IADE` and `SGK`.
- **Code 555** (KDV Oran Kontrolüne Tabi Olmayan Satışlar) is not an exemption:
  it marks sales for which the activity register has no matching VAT rate, such
  as re-invoiced costs or the sale of a used fixed asset.
- **Codes 351 and 151** are for invoices that must show 0 VAT or 0 ÖTV although
  no exemption applies.
- **Investment incentive.** The schematron accepts `308` and `339` only on
  investment incentive invoices (profile `YATIRIMTESVIK` or e-Arşiv
  `YTBISTISNA`), flagged `investment_incentive_only`.
- **Code 501** is accepted by the schematron but is not described in the code
  list guide, so it is not included.
- **Descriptions** are kept as GİB prints them, including inconsistent case and
  a few typos (`Kiymetli`, `Uygulandığiı`). Several old descriptions name
  ministries by their former names (Gıda, Tarım ve Hayvancılık Bakanlığı,
  Başbakanlık).
- **Updates.** GİB revises the list several times a year; version 1.43
  (2026-07-27) added code `233`. Check the change table of the guide for a
  newer version before relying on this snapshot.

## Sources

- [UBL-TR Kod Listeleri, version 1.43, July 2026](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/UBLTR_1.2.1_Kilavuzlar.zip),
  section 1.8 TaxExemptionReasonCode, GİB, retrieved 2026-11-09.
- [e-Fatura Paketi](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/e-FaturaPaketi%20(29).zip),
  `schematron/UBL-TR_Codelist.xml`, history up to 2026-07-01, retrieved
  2026-11-05: `TaxExemptionReasonCodeType` and
  `YatirimTesvikTaxExemptionReasonCodeType`.

The codes and descriptions were extracted from the PDF text by a script, not
retyped, and checked for: row counts per list against the guide; unique codes;
and every code against the schematron (all 112 are accepted; the schematron's
only extra code is `501`).
