# UBL-TR transport mode codes (e-Fatura)

`TransportModeCode` values from Kod Listeleri §1.10 (Taşıma Gönderim Şekli),
with Turkish names, plus codes `0` and `9` that the schematron accepts but the
guide does not name. The guide allows other UNECE Recommendation 19 codes when
not in its short list.

| File | Rows | Description |
| --- | --- | --- |
| [`transport-mode-codes.csv`](transport-mode-codes.csv) | 10 | Codes `0`–`9` |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `3` | Value for `TransportModeCode` |
| `name` | `Karayolu` | Turkish name from the guide |
| `in_guide` | `true` | In §1.10 |
| `in_schematron` | `true` | In `TransportModeCodeList` |

## Notes

- Codes `0` and `9` have empty `name`: they are not in the guide table. Do not
  invent UNECE labels here without quoting Rec 19 as a separate source.

## Sources

- [UBL-TR Kod Listeleri V1.43](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/UBLTR_1.2.1_Kilavuzlar.zip), §1.10, retrieved 2026-11-16.
- [e-Fatura Paketi](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/e-FaturaPaketi%20(29).zip), retrieved 2026-11-16.
