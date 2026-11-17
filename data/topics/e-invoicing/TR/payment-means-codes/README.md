# UBL-TR payment means codes (e-Fatura)

The `PaymentMeansCode` values accepted by the GİB UBL-TR schematron. Kod
Listeleri §1.6 does not print a Turkish table; it requires
[UN/EDIFACT 4461](https://service.unece.org/trade/untdid/d06a/tred/tred4461.htm).
English names come from that directory (D.06A); the code set is the
schematron `PaymentMeansCodeTypeList`.

| File | Rows | Description |
| --- | --- | --- |
| [`payment-means-codes.csv`](payment-means-codes.csv) | 75 | Codes accepted by the schematron |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `30` | Value for `cbc:PaymentMeansCode` |
| `name_en` | `Credit transfer` | UNECE 4461 English name |
| `in_schematron` | `true` | In `PaymentMeansCodeTypeList` |

## Notes

- GİB does not publish Turkish labels for these codes in Kod Listeleri V1.43.
- The schematron subset is 75 codes from 4461 (including `ZZZ`), not the full
  historical directory.

## Sources

- [UBL-TR Kod Listeleri V1.43](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/UBLTR_1.2.1_Kilavuzlar.zip), §1.6, retrieved 2026-11-16.
- [UN/EDIFACT 4461 D.06A](https://service.unece.org/trade/untdid/d06a/tred/tred4461.htm), retrieved 2026-11-16.
- [e-Fatura Paketi](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/e-FaturaPaketi%20(29).zip), `PaymentMeansCodeTypeList`, retrieved 2026-11-16.

Checked for: 75 unique codes; every schematron code has a 4461 name.
