# UBL-TR unit of measure codes (e-Fatura)

The units of measure listed by the Revenue Administration (Gelir İdaresi
Başkanlığı, GİB) for the `unitCode` attribute of quantities in Turkish
e-documents, with their official Turkish names. Each unit is linked to its
UN/ECE Recommendation 20 entry and, where it has one, to its unit set and
conversion factor in [world-units-of-measure](../../../../world/units-of-measure/).
Typically used for the unit pick list of invoicing and ERP software and to map
internal units to e-invoice codes.

| File | Rows | Description |
| --- | --- | --- |
| [`unit-codes.csv`](unit-codes.csv) | 39 | One row per unit in GİB's list |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `KGM` | Code for `unitCode` |
| `name` | `KİLOGRAM` | Turkish name as printed by GİB |
| `rec20_name` | `kilogram` | English name in Rec 20 |
| `rec20_status` | `active` | `active`, `deleted` or `deprecated` in Rec 20 |
| `unit_set` | `mass` | Unit set in world-units-of-measure, if any |
| `factor_to_base` | `1` | Factor to the base unit of the set |
| `in_schematron` | `true` | Accepted by the UBL-TR schematron |

16 of the 39 units are in a unit set: ADET, ÇİFT and YÜZ ADET (count); GRAM and
KİLOGRAM (mass); LİTRE, METRE KÜP and STANDART METREKÜP (volume); METRE
(length); DESİMETRE KARE and METRE KARE (area); and the joule and watt hour
units (energy).

## Notes

- **Other codes are allowed.** GİB's guide says the `unitCode` value should be
  taken from this list first, and otherwise from UN/ECE Recommendation 20 or
  the Ministry of Trade's EDI/XML unit code list. The schematron accepts 2,152
  codes: all 2,136 codes of Rec 20 Revision 17 (deleted ones included) and 16
  codes that are not in Rec 20 (`AMVT`, `KFO`, `TWH` and others), which the
  guide does not describe. Common units that are not in GİB's list, such as
  `MGM` milligram, `MLT` millilitre, `CMT` centimetre or `DZN` dozen, are in
  world-units-of-measure.
- **Codes outside Rec 20 Revision 17.** `KFO` (DİFOSFOR PENTAOKSİT KİLOGRAMI)
  is not in Rec 20. `D40` (BİN LİTRE) and `3I` (KİLOGRAM-ADET) are marked for
  deletion and `GT` (GROSS TON) is deprecated there. GİB still accepts all four.
- **Names differ in places.** GİB's names are its own translations and do not
  always match Rec 20: `D30` is BRÜT KALORİ DEĞERİ in the GİB list but
  terajoule in Rec 20, and `CCT` is TON BAŞINA TAŞIMA KAPASİTESİ for Rec 20's
  carrying capacity in metric ton.
- **Units outside the sets.** `T3` (BİN ADET), `SET` and the
  substance-specific kilograms (`KNI` AZOTUN KİLOGRAMI and similar) have no
  conversion factor in Rec 20. `R9` (BİN METRE KÜP, 10³ m³) and `CTM` (KARAT,
  200 mg) have one but are not listed under a quantity in Annex I, so they are
  not in a set; their factors are in `units.csv` of world-units-of-measure.

## Sources

- [UBL-TR Kod Listeleri, version 1.43, July 2026](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/UBLTR_1.2.1_Kilavuzlar.zip),
  section 1.5 InvoicedQuantity, Ölçü Birim Kodları Listesi, GİB, retrieved
  2026-11-09.
- [e-Fatura Paketi](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/e-FaturaPaketi%20(29).zip),
  `schematron/UBL-TR_Codelist.xml` (`UnitCodeList`), retrieved 2026-11-05.
- [world-units-of-measure](../../../../world/units-of-measure/) (UN/CEFACT
  Recommendation 20, Revision 17) for the Rec 20 name, status, unit set and
  factor.

The codes and names were extracted from the PDF text by a script, not retyped,
and checked for: 39 code and name pairs; unique codes; every code accepted by
the schematron; and every code but `KFO` present in Rec 20.
