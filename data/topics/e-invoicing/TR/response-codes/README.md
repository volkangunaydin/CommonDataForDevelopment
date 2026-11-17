# UBL-TR application response codes (e-Fatura)

`ResponseCode` values for Turkish `ApplicationResponse` documents. Kod Listeleri
§1.7 names acceptance, rejection and return; the schematron also accepts
`S_APR` (system response) and `GUMRUKONAY`.

| File | Rows | Description |
| --- | --- | --- |
| [`response-codes.csv`](response-codes.csv) | 5 | Guide codes plus two schematron-only values |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `KABUL` | Value for `cbc:ResponseCode` |
| `name` | `Faturanın kabul edildiğini gösterir` | Description |
| `in_guide` | `true` | Named in §1.7 |
| `in_schematron` | `true` | In `ResponseCodeType` |
| `usage` | `application` | `application` or `system` |

## Notes

- **`S_APR`.** Not in the guide; GİB sample XML comments it as "System
  application response". Used on SYSTEMENVELOPE responses.
- **`GUMRUKONAY`.** Accepted by the schematron (including POSTBOXENVELOPE) but
  not described in Kod Listeleri V1.43; `name` is empty.
- Numeric system status codes (`1000`, `1200`, …) are a separate schematron list
  (`AppResponseCodeType`) and are not in this dataset: the package does not
  publish their names.

## Sources

- [UBL-TR Kod Listeleri V1.43](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/UBLTR_1.2.1_Kilavuzlar.zip), §1.7, retrieved 2026-11-16.
- [e-Fatura Paketi](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/e-FaturaPaketi%20(29).zip), retrieved 2026-11-16.
