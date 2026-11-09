# Customs tariff statistical positions of Türkiye (GTİP)

The Gümrük Tarife İstatistik Pozisyonu (GTİP) nomenclature for 2026: the
12-digit product codes used in Turkish customs declarations, together with the
whole hierarchy above them (section, chapter, heading, HS and CN subheadings)
and a Turkish description for every row. Typically used for product
classification pick lists, export e-invoices (UBL-TR `IHRACAT` profile),
customs and logistics software, and for joining foreign trade statistics.

| File | Rows | Description |
| --- | --- | --- |
| [`gtip.csv`](gtip.csv) | 32,567 | One row per code at every level |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `010129100000` | Code without dots; see the levels below |
| `parent_code` | `01012910` | Code one level up; empty for sections |
| `level` | `gtip` | `section`, `chapter`, `heading`, `hs_subheading`, `cn_subheading`, `gtip` |
| `name` | `Atlar; kesimlik olanlar` | Description in Turkish (TÜİK) |
| `statistical_only` | `false` | `true` for statistics-only codes that are not in the tariff schedule |

Rows by level:

| Level | Turkish | Digits | Rows |
| --- | --- | --- | --- |
| `section` | Kısım | Roman numeral | 21 |
| `chapter` | Fasıl | 2 | 98 |
| `heading` | Tarife pozisyonu | 4 | 1,248 |
| `hs_subheading` | Armonize sistem alt pozisyonu | 6 | 5,634 |
| `cn_subheading` | Kombine nomanklatür alt pozisyonu | 8 | 9,813 |
| `gtip` | GTİP | 12 | 15,753 |

To get the codes that can be declared, keep `level = gtip` and
`statistical_only = false`: 15,718 rows.

## Notes

- **Display format.** Codes are stored without separators. Customs documents
  usually print a GTİP as `0101.29.10.00.00` (4.2.2.2.2 digits), and the tariff
  schedule prints headings as `01.01` and HS subheadings as `0101.29`.
- **Descriptions are TÜİK's**, not the legal text. In the tariff schedule a
  12-digit line often reads only `- - - Diğerleri` and takes its meaning from
  the lines above it. TÜİK rewrites each line so it stands alone, for example
  `Diğer ferro - manganez; C > %2` for `7202.11.80.00.00`. Use the Official
  Gazette text for anything with legal effect. Whitespace runs were collapsed
  to a single space in 430 descriptions; spelling, case and punctuation are
  unchanged (section names are upper case in the source).
- **Shortened descriptions.** TÜİK cuts 124 long descriptions (53 of them
  GTİP codes) in 17 chapters, most of them in chapters 29, 48, 44, 84, 85 and
  38, and refers to the Official Gazette with `(devamı Resmi Gazetede)` or `(ayrıntı Resmi
  Gazetede)`. In 18 of them a `?` stands where the cut was made, apparently an
  ellipsis lost by the source. They are kept as TÜİK publishes them; read the
  full text in the tariff schedule.
- **Statistics-only codes.** TÜİK's list has 35 twelve-digit codes that are not
  in the tariff schedule: aggregated codes such as `290000000003`
  (`Organik kimyasallar`) and `279999999999` (`Gizli veri`, confidential
  trade), used in foreign trade statistics. They sit under artificial parents
  such as `2900`, `290000` and `29000000`, which are flagged as well (48 rows
  above the GTİP level). They are kept so that statistics files can be joined,
  but must not be used in declarations.
- **Chapter 77** is reserved in the Harmonized System and has no codes below it.
  Chapters 98 and 99 are left for national use; Türkiye uses only 99, for
  personal effects, ship and aircraft stores and similar.
- **Row order.** Sections first in numeral order (I to XXI), then all numeric
  codes in ascending order, which lists every code directly after its parent.
- **Annual edition.** The nomenclature is replaced every year on 1 January,
  following the EU Combined Nomenclature, and can be amended during the year by
  Presidential decision. This is the 2026 edition (Karar Sayısı 10781) as served
  by TÜİK on 2026-11-09. Codes may be added, split or removed in 2027.
- **Not included.** Duty rates, units of measure, chapter notes and the import
  regime measures are in the tariff schedule and the İthalat Rejimi Kararı but
  are not part of this dataset.

## Sources

- [TÜİK Sınıflama Sunucusu, GTİP 2026](https://siniflama.tuik.gov.tr/Classifications/ClassificationsSatir?surumId=1674)
  (version id 1674), retrieved 2026-11-09: every row, with code, parent code,
  level and description.
- [İstatistik Pozisyonlarına Bölünmüş Türk Gümrük Tarife Cetveli, Karar Sayısı 10781](https://www.resmigazete.gov.tr/eskiler/2025/12/20251230M1-2.pdf),
  Resmî Gazete 33123 (1. Mükerrer), 2025-12-30, and its
  [Excel edition published by the Ministry of Trade](https://ggm.ticaret.gov.tr/duyurular/istatistik-pozisyonlarina-bolunmus-turk-gumruk-tarife-cetveli-karar-sayisi-10781-yayimlanmistir):
  the list of codes in the legal schedule, used for `statistical_only`.

The TÜİK response was converted with a script, not retyped, and checked for:
row counts per level against the counts shown by TÜİK (21, 98, 1,248, 5,634,
9,813, 15,753); unique codes; every `parent_code` present one level up and a
prefix of the code; and the 12-digit codes against the Ministry's Excel
edition. All 15,718 codes in the schedule are present (one of them,
`8462.29.00.00.00`, is printed with spaces instead of dots in the Excel file);
the 35 extra TÜİK codes are the statistics-only codes described above.
