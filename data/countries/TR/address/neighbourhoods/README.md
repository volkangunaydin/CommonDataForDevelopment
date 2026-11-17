# Neighbourhoods and postal codes of Türkiye

Neighbourhoods (mahalle) with PTT postal codes, by province and district.
Street-level rows from the PTT API are aggregated to distinct
neighbourhood–postal-code pairs.

| File | Rows | Description |
| --- | --- | --- |
| [`neighbourhoods.csv`](neighbourhoods.csv) | 72,780 | Neighbourhood + postal code |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Counts (retrieved 2026-11-16)

| Level | Count |
| --- | ---: |
| Provinces | 81 |
| Districts | 973 |
| Distinct neighbourhoods | 72,435 |
| Neighbourhood–postal-code rows | 72,780 |
| Distinct postal codes | 2,777 |

254 neighbourhoods have more than one postal code and appear once per code.

## Notes

- `province_code` and `district_name` match [`tr-address-provinces`](../provinces/)
  and [`tr-address-districts`](../districts/).
- Neighbourhood names are kept as PTT publishes them (often with a `MAH.`
  suffix).
- The old bulk Excel download (`postakodu.ptt.gov.tr/Dosyalar/pk_list.zip`) is
  no longer served; this dataset uses the public
  [Posta Kodu Sorgulama](https://www.ptt.gov.tr/posta-kodu) API instead.
- Streets (`sokak`) from the API are not included.

## Sources

- [PTT Posta Kodu Sorgulama](https://www.ptt.gov.tr/posta-kodu) —
  `POST /api/posta-kodu` with actions `ilceler` and `postakodu`, retrieved
  2026-11-16.

Checked for: 81 provinces; 973 districts; all postal codes 5 digits; every
district name matches `tr-address-districts`; unique composite primary key.
