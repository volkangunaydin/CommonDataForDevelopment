# UBL-TR PartyIdentification schemeID values (e-Fatura)

`schemeID` values for `PartyIdentification/ID` (VKN, TCKN and other party
identifiers) from Kod Listeleri §2.1, cross-checked with the schematron
`PartyIdentificationIDType`.

| File | Rows | Description |
| --- | --- | --- |
| [`party-identification-schemes.csv`](party-identification-schemes.csv) | 30 | Guide list plus `GTB_GCB_TESCILNO` |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `VKN` | `schemeID` value |
| `name` | `Vergi Kimlik Numarası` | Turkish description |
| `in_guide` | `true` | In §2.1 |
| `in_schematron` | `true` | In `PartyIdentificationIDType` |

## Notes

- **`GCB_TESCILNO` vs `GTB_GCB_TESCILNO`.** The guide prints `GCB_TESCILNO`
  (Gümrük Çıkış Belgesi Tescil No). The schematron accepts `GTB_GCB_TESCILNO`
  and does not list `GCB_TESCILNO`. Both rows are kept with flags; use the
  schematron value for validation against the e-Fatura package.
- Natural persons use `TCKN`, legal persons `VKN` (§2.1).

## Sources

- [UBL-TR Kod Listeleri V1.43](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/UBLTR_1.2.1_Kilavuzlar.zip), §2.1, retrieved 2026-11-16.
- [e-Fatura Paketi](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/e-FaturaPaketi%20(29).zip), retrieved 2026-11-16.
