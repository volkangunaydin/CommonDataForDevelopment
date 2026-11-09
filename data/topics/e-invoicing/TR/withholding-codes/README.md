# UBL-TR VAT withholding codes (e-Fatura)

The VAT withholding (KDV tevkifatı) codes of Turkish e-invoices, with the
official Turkish description and withholding rate published by the Revenue
Administration (Gelir İdaresi Başkanlığı, GİB). In a `TEVKIFAT` invoice the code
goes to `cac:WithholdingTaxTotal/cac:TaxSubtotal/cac:TaxCategory/cac:TaxScheme/cbc:TaxTypeCode`
and the rate to `cbc:Percent`. Typically used for the withholding pick list of
invoicing and ERP software and to calculate the withheld VAT.

| File | Rows | Description |
| --- | --- | --- |
| [`withholding-codes.csv`](withholding-codes.csv) | 52 | One row per code |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `604` | Three-digit code |
| `name` | `Yemek Servis Hizmeti` | Turkish description as printed by GİB |
| `type` | `partial` | `partial` (6xx) or `full` (8xx) |
| `rate` | `5/10` | Share of the VAT that is withheld, as printed |
| `rate_percent` | `50` | The same as a percentage, the value for `cbc:Percent` |
| `schematron_percents` | `50` | Percentages the schematron accepts, separated by `;` |

The 27 partial codes (`601`–`627`) withhold between 2/10 and 9/10 of the VAT.
The 25 full codes (`801`–`825`) cover the same services and goods with 10/10
withholding, used where the buyer withholds all of the VAT.

## How to calculate

Withheld VAT = VAT × `rate_percent` / 100. For a catering invoice (`604`, 5/10)
with a base of 1,000 and 20% VAT, the VAT is 200, the buyer withholds 100 and
pays 1,100 to the seller.

## Notes

- **Older rates still accepted.** For seven codes the schematron accepts the
  current rate and also a lower, earlier one: `601` (30 and 40), `603`, `609`
  and `615` (50 and 70), `612` and `613` (70 and 90) and `627` (40 and 50).
  `rate` and `rate_percent` are the current rates printed in the guide.
- **Code 650.** The schematron accepts code `650` with 20, 30, 50, 70 or 90
  percent in the percent table, but not in its list of withholding codes, and
  the guide does not describe it. It is not included.
- **Descriptions** are kept as GİB prints them. The 6xx descriptions are
  written without the dotless ı in many words (`Yapim`, `Danişmanlik`,
  `Taşimaciliği`); the 8xx descriptions of the same services are spelled
  correctly. Section references to the KDV Genel Uygulama Tebliği
  (`[KDVGUT-(I/C-2.1.3.2.1)]`) are part of the description where GİB prints
  them.
- **Snapshot.** Version 1.43 of the guide, July 2026. Rates and codes change
  with the KDV Genel Uygulama Tebliği; check for a newer version of the guide
  before relying on this list.

## Sources

- [UBL-TR Kod Listeleri, version 1.43, July 2026](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/UBLTR_1.2.1_Kilavuzlar.zip),
  section 1.9, Tevkifat Kodları Listesi, GİB, retrieved 2026-11-09.
- [e-Fatura Paketi](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/e-FaturaPaketi%20(29).zip),
  `schematron/UBL-TR_Codelist.xml`, history up to 2026-07-01, retrieved
  2026-11-05: `WithholdingTaxType` and `WithholdingTaxTypeWithPercent`.

The codes, descriptions and rates were extracted from the PDF text by a script,
not retyped, and checked for: 27 + 25 rows as in the guide; unique codes; a rate
for every code; and the code list against the schematron (identical, 52 codes).
