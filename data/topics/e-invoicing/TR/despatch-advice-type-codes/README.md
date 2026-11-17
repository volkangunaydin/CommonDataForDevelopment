# UBL-TR despatch advice type codes (e-İrsaliye)

`DespatchAdviceTypeCode` values from the UBL-TR schematron (`SEVK`,
`MATBUDAN`). Kod Listeleri V1.43 has no named table for them, so `name` is
empty. `SEVK` is also the only value in `ReceiptAdviceTypeCodeList`.

| File | Rows | Description |
| --- | --- | --- |
| [`despatch-advice-type-codes.csv`](despatch-advice-type-codes.csv) | 2 | Schematron despatch type codes |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Notes

- When `MATBUDAN` is used, the schematron requires at least one
  `AdditionalDocumentReference` with non-empty `ID` and `IssueDate`.

## Sources

- [e-Fatura Paketi](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/e-FaturaPaketi%20(29).zip),
  `DespatchAdviceTypeCodeList` / `ReceiptAdviceTypeCodeList`, retrieved 2026-11-16.
