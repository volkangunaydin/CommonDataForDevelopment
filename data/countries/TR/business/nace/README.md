
# NACE Rev. 2.1 economic activity codes of Türkiye

The national NACE Rev. 2.1 classification from the TÜİK Sınıflama Sunucusu
(version id 1676, labelled NACE Rev.2.1-Altılı 2026): the full hierarchy from
section to six-digit subclass, with Turkish and English names.

| File | Rows | Description |
| --- | --- | --- |
| [`nace.csv`](nace.csv) | 3,190 | All levels |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Levels

| `level` | Count | Example `code` |
| --- | ---: | --- |
| section | 23 | `A` |
| division | 87 | `01` |
| group | 287 | `01.1` |
| class | 651 | `01.11` |
| subclass | 2,142 | `01.11.07` |

## Notes

- Codes are strings. Keep leading zeros (`01`, not `1`).
- `parent_code` points at `code` in this file.
- An English downloadable workbook is also listed by TÜİK
  (`NACETR Rev. 2.1_INGILIZCE_SS.xlsx`); names here come from the classification
  API rows themselves.

## Sources

- [TÜİK Sınıflama Sunucusu, surumId 1676](https://siniflama.tuik.gov.tr/Classifications/ClassificationsSatir?surumId=1676),
  retrieved 2026-11-16 via `GetSiniflamaSatir`. Attribution:
  [TÜİK Yasal Uyarı](https://www.tuik.gov.tr/Kurumsal/Yasal_Uyari).

Checked for: 3,190 rows; level counts 23/87/287/651/2142; unique codes; every
non-section row has a parent; every row has TR and EN names.
