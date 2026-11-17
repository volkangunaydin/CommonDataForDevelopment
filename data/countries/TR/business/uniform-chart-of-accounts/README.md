# Uniform chart of accounts of Türkiye (Tekdüzen Hesap Planı)

The private-sector Tekdüzen Hesap Planı from **1 Sıra No'lu Muhasebe Sistemi
Uygulama Genel Tebliği** (MSUGT), section B, as published in the GİB
consolidated PDF. Classes 1–9, named groups, and named ledger accounts —
including financial-leasing and inflation-adjustment accounts added by later
MSUGT tebliğler and present in that consolidated text.

This is **not** the public-sector detailed charts on
[muhasebat.hmb.gov.tr/hesap-planlari](https://muhasebat.hmb.gov.tr/hesap-planlari)
(genel bütçe, özel bütçe, üniversiteler, etc.).

| File | Rows | Description |
| --- | --- | --- |
| [`accounts.csv`](accounts.csv) | 352 | Classes, groups and ledger accounts |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Levels

| `level` | Count | Example `code` |
| --- | ---: | --- |
| class | 9 | `1` (Dönen Varlıklar) |
| group | 58 | `10` (Hazır Değerler) |
| account | 285 | `100` (Kasa) |

## Notes

- Codes are strings (`100`, not a number that could lose formatting).
- `parent_code` points at `code` in this file.
- Empty reserved slots in the tebliğ (e.g. `104.`, `14.`) are **not** rows.
- Project ranges `170–177` and `350–357` are expanded to one row per code, with
  the same name as in the tebliğ.
- Class `8` is free (`SERBEST`); class `9` is nazım accounts with no standard
  ledger list in MSUGT.
- `cost_option` is `A` or `B` only under class 7 (7/A vs 7/B).
- Three obvious typesetting errors in the PDF text layer were aligned with the
  spelling used on adjacent lines of the same PDF: group `76` YE→VE, account
  `247` DÜŞÜKLÜGÜ→DÜŞÜKLÜĞÜ, account `721` İŞCİLİK→İŞÇİLİK.

## Sources

- [GİB consolidated PDF of 1 Sıra No'lu MSUGT, section B](https://cdn.gib.gov.tr/api/gibportal-file/file/getFile?objectKey=MEVZUAT_TEBLIGLER%2FUNIVERSAL%2F2025%2Farsiv_yedek_fileadmin_mevzuatek_eski_muhsisteb1ekmuh5_04102019.pdf),
  retrieved 2026-11-16. Original: Resmî Gazete 26.12.1992, 21447 (Mükerrer).

Checked for: 352 rows (9/58/285); unique codes; every non-class row has a
parent; 170–177 and 350–357 expanded; amendments 124, 178, 301–302, 358, 502–503,
648, 658, 697–698 present.
