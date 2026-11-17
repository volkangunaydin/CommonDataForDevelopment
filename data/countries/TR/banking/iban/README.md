
# IBAN structure and validation rules of Türkiye

Machine-readable description of the Turkish IBAN as defined by the Central Bank
(TCMB) Communique No. 2008/6 and recorded in the SWIFT IBAN Registry.

| File | Rows | Description |
| --- | --- | --- |
| [`iban-structure.csv`](iban-structure.csv) | 1 | Country-level structure |
| [`iban-fields.csv`](iban-fields.csv) | 5 | Field positions |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Validation (from the Communique)

1. Strip spaces and non-alphanumeric characters.
2. Move the first four characters to the end.
3. Convert A–Z to 10–35 (A=10 … Z=35).
4. Compute the number modulo 97; a valid IBAN yields remainder **1**
   (ISO 7064 MOD 97-10).

The electronic example `TR470000100100000350930001` is the worked example in
the Communique (TCMB bank code `00001`).

## Notes

- Bank codes are those announced by TCMB; see
  [`tr-banking-banks`](../banks/).
- The reserved field is always `0`.
- Letters İ, Ç, Ğ, Ö, Ş, Ü and lowercase letters are not allowed.

## Sources

- [TCMB IBAN Communique (EN)](https://www.tcmb.gov.tr/wps/wcm/connect/EN/TCMB+EN/Bottom+Menu/IBAN/Communique),
  retrieved 2026-11-16.
- [SWIFT IBAN Registry](https://www.swift.com/sites/default/files/files/iban_registry.pdf)
  Release 102, TR entry, retrieved 2026-11-16.
