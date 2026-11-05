# Districts of Türkiye

The districts (ilçe) of Türkiye by province. Names come from the Ministry of the
Interior's inventory of administrative divisions; coordinates come from GeoNames.
Typically used for address forms, pick lists and joins with other datasets by
province.

| File | Rows | Description |
| --- | --- | --- |
| [`districts.csv`](districts.csv) | 973 | One row per district |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `province_code` | `01` | Province code, see [tr-address-provinces](../provinces/) |
| `name` | `Ceyhan` | District name in Turkish |
| `latitude` | `37.07496` | Approximate latitude, WGS 84 |
| `longitude` | `35.83629` | Approximate longitude, WGS 84 |

## Notes

- **Count.** The Ministry lists 922 districts. In the 51 provinces that are not
  metropolitan municipalities, the central district is listed as `MERKEZ`, which
  adds 51 rows (973 in total). Provinces with a metropolitan municipality
  (30) have named central districts, for example Seyhan and Yüreğir in Adana.
- **Coordinates are approximate** and are not an official boundary or centroid.
  920 rows have them. They are empty for the 51 `Merkez` rows, which have no
  GeoNames district entry, and for Şemdinli (Hakkâri) and 19 Mayıs (Samsun),
  which could not be matched.
- **No official district code.** The source gives names only. Do not use
  `province_code` + `name` as a stable identifier across years: districts are
  created and renamed.
- Names are converted from the source's upper case to Turkish title case. GeoNames
  spells 15 names differently (for example Kâhta, Lâpseki); the Ministry's spelling
  is used.
- The Ministry's page is a snapshot of the day it was read (2026-10-05).

## Source

- [Türkiye Mülki İdare Bölümleri Envanteri, T.C. İçişleri Bakanlığı](https://www.e-icisleri.gov.tr/Anasayfa/MulkiIdariBolumleri.aspx)
- [GeoNames](https://download.geonames.org/export/dump/TR.zip), licensed under
  CC BY 4.0. Credit: GeoNames, https://www.geonames.org

Names were read from the Ministry's page province by province and checked against
its totals (81 provinces, 922 districts). Coordinates were matched to names within
the same province and checked to lie inside Türkiye.
