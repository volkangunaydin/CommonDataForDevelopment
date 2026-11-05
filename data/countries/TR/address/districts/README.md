# Districts of Türkiye

The districts (ilçe) of Türkiye by province. Names come from the Ministry of the
Interior's inventory of administrative divisions, district codes from TÜİK and
coordinates from GeoNames.
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
| `tuik_code` | `1219` | TÜİK district code, four digits, unique. Always treat it as a string. |
| `alternate_names` | `Doğubeyazıt` | Other spellings used by GİB or GeoNames, separated by `;`; usually empty |

## Notes

- **Count.** The Ministry lists 922 districts. In the 51 provinces that are not
  metropolitan municipalities, the central district is listed as `MERKEZ`, which
  adds 51 rows (973 in total). Provinces with a metropolitan municipality
  (30) have named central districts, for example Seyhan and Yüreğir in Adana.
- **Coordinates are approximate** and are not an official boundary or centroid.
  920 rows have them. They are empty for the 51 `Merkez` rows, which have no
  GeoNames district entry, and for Şemdinli (Hakkâri) and 19 Mayıs (Samsun),
  which could not be matched.
- **District code.** `tuik_code` is the code TÜİK uses for the district in
  population statistics (code list `CL_IBBS` 1.2). It is the stable key to use;
  `province_code` + `name` is not, because districts are renamed. The code is
  not derived from the province code: Ceyhan (Adana) is `1219`, Aladağ (Adana)
  is `1757`. Every row has one, including the 51 `Merkez` rows.
- **Not the NVİ code.** The address system of the Nüfus ve Vatandaşlık İşleri
  Genel Müdürlüğü (UAVT, used by e-Devlet address queries) numbers districts
  differently. Those codes are not included: the service is protected against
  automated access and publishes no downloadable list.
- Names are converted from the source's upper case to Turkish title case. Where
  another source spells a district differently, `name` keeps the Ministry's
  spelling.
- **Alternate names** help match records from other sources. 13 districts have
  one:
  - From the GİB tax office list ([tr-tax-tax-offices](../../tax/tax-offices/)):
    `Doğubeyazıt` for Doğubayazıt, `Balâ` for Bala, `Göroymak` for Güroymak,
    `Kazım Karabekir` for Kazımkarabekir.
  - From GeoNames: circumflex spellings (`Kâhta`, `Lâpseki`, `Lâlapaşa`,
    `Kâğıthane`, `Şarkîkaraağaç`), split forms (`Şebin Karahisar`,
    `Marmara Ereğlisi`), `Mihalıçcık`, and the historical name `Berkri` for
    Muradiye (Van).

  GeoNames' suffix `İlçesi` and spellings without Turkish letters (`Beypazari`)
  are not counted as alternate names. With these, every district named in the GİB
  list matches a row by `province_code` and `name` or `alternate_names`, except
  `Merkez` in the metropolitan provinces.
- The Ministry's page is a snapshot of the day it was read (2026-10-05).

## Source

- [Türkiye Mülki İdare Bölümleri Envanteri, T.C. İçişleri Bakanlığı](https://www.e-icisleri.gov.tr/Anasayfa/MulkiIdariBolumleri.aspx)
- [GeoNames](https://download.geonames.org/export/dump/TR.zip), licensed under
  CC BY 4.0. Credit: GeoNames, https://www.geonames.org
- [TÜİK Veri Portalı, İl ve İlçelere Göre İl/İlçe Merkezi, Belde/Köy Nüfusu (ADNKS 2025)](https://veriportali.tuik.gov.tr/tr/databrowser/tuik/TR,DF_ADNKS_T22,1.1),
  district dimension, retrieved 2026-11-05. Source: TÜİK. TÜİK permits reuse with
  attribution ([Yasal Uyarı](https://www.tuik.gov.tr/Kurumsal/Yasal_Uyari)).

Names were read from the Ministry's page province by province and checked against
its totals (81 provinces, 922 districts). Coordinates were matched to names within
the same province and checked to lie inside Türkiye. TÜİK codes were matched by
name within the TÜİK province they are listed under: all 973 rows matched one
code each, every province has the same number of districts in both sources, and
no TÜİK district was left over. TÜİK labels 100 districts with the province name
in front (`Şırnak Merkez`, `Balıkesir Gönen`); that prefix was ignored for
matching.
