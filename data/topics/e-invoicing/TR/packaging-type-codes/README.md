# UBL-TR packaging type codes (e-Fatura)

The package and container type codes listed by GİB for
`PackagingTypeCode` on Turkish e-documents, with their official Turkish names.
Typically used for the packaging pick list on despatch advice and invoices that
carry package information.

| File | Rows | Description |
| --- | --- | --- |
| [`packaging-type-codes.csv`](packaging-type-codes.csv) | 27 | One row per code in GİB's short list |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `BX` | Value for `PackagingTypeCode` |
| `name` | `Kutu` | Turkish name from the guide |
| `in_schematron` | `true` | Accepted by `PackageTypeCodeList` |

## Notes

- **Other UNECE codes are allowed.** The guide says codes not in this list may
  be taken from the UNECE/CEFACT package type list. The UBL-TR schematron
  `PackageTypeCodeList` accepts 378 codes; this dataset only carries the 27
  that GİB prints with Turkish names.
- All 27 guide codes are present in the schematron list (package retrieved
  2026-11-16).

## Sources

- [UBL-TR Kod Listeleri, version 1.43, July 2026](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/UBLTR_1.2.1_Kilavuzlar.zip),
  section 1.13 Paket/Kap Cins Kodları, GİB, retrieved 2026-11-16.
- [e-Fatura Paketi](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/e-FaturaPaketi%20(29).zip),
  `schematron/UBL-TR_Codelist.xml` (`PackageTypeCodeList`), retrieved 2026-11-16.

Checked for: 27 unique codes and names from the PDF; every code accepted by the
schematron.
