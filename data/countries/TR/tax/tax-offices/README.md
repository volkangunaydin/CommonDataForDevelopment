# Tax offices of Türkiye

Tax offices (vergi dairesi) of Türkiye as published by the Revenue
Administration (Gelir İdaresi Başkanlığı, GİB), with their accounting unit codes,
province and district. Typically used to populate tax office pick lists in
invoicing and ERP software.

| File | Rows | Description |
| --- | --- | --- |
| [`tax-offices.csv`](tax-offices.csv) | 860 | One row per tax office (859) plus Eskişehir Defterdarlığı (1) |
| [`tax-office-branches.csv`](tax-office-branches.csv) | 233 | One row per branch (şube) of an office; no code |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

### tax-offices.csv

| Field | Example | Description |
| --- | --- | --- |
| `code` | `01201` | Five-digit accounting unit code, unique |
| `province_code` | `01` | Province code, see [tr-address-provinces](../../address/provinces/) |
| `district` | `Ceyhan` | District (ilçe); `Merkez` is the central district |
| `name` | `Ceyhan Vergi Dairesi Müdürlüğü` | Official name |
| `type` | `tax_office` | `tax_office` or `treasury_office` |
| `district_center_by_law_6360` | `true` | Source marks the district with (**) |

### tax-office-branches.csv

`province_code`, `district`, `name` and `district_center_by_law_6360`, as above.

## Notes

- **Count.** The source lists 859 tax office directorates, 1 treasury office acting
  as a tax office and 233 branches (218 under tax offices plus 15 under Eskişehir
  Defterdarlığı). That is 860 coded rows and 1,093 rows in total. It is not 961.
- **Codes are strings** and keep their leading zero. They are not derived from the
  province code, so do not infer the province from the first digits.
- **Branches have no code** in the source and the source does not say which office
  they belong to, so none is given here.
- Names are kept as published, including the full title `Vergi Dairesi Müdürlüğü`.
- **Joining with [tr-address-districts](../../address/districts/).** District
  names are kept as GİB spells them, so two kinds of row do not match by
  `province_code` + `district`:
  - Four districts are spelled differently from the Ministry of the Interior:
    `Doğubeyazıt` (Doğubayazıt, 04), `Balâ` (Bala, 06), `Göroymak` (Güroymak, 13)
    and `Kazım Karabekir` (Kazımkarabekir, 70, branches only). The districts
    dataset lists these spellings in `alternate_names`, so match on `name` or
    `alternate_names`.
  - GİB lists the central offices of the 30 metropolitan provinces under
    `Merkez`, for example in İstanbul and Ankara. The districts dataset has
    `Merkez` only for the 51 other provinces, because metropolitan provinces
    have no district of that name.
- Data is a snapshot of the 2026-06-18 edition. The source has no validity dates, so
  offices closed or opened since then are not reflected. Check for a newer edition
  before relying on it.

## Source

- [Defterdarlık ve Vergi Daireleri Listesi, GİB, 2026-06-18](https://cdn.gib.gov.tr/api/gibportal-file/file/getFileResources?objectKey=arsiv%2Fyardim-kaynaklar%2Fyararli-bilgiler%2FDefterdarl%C4%B1kveVergiDaireleriListesi.pdf)

The rows were extracted from the PDF by reading word coordinates, not by retyping.
The result was checked against the totals printed in the PDF (860 and 859 offices,
218 + 15 branches), against uniqueness of codes, and against the province list
(all 81 provinces present, every name matching `tr-address-provinces`).
