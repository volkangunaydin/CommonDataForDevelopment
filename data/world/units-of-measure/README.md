# Units of measure (UN/ECE Recommendation 20)

The codes for units of measure used in international trade, from UN/CEFACT
Recommendation 20 (Revision 17, 2021). These are the codes used in UBL, EDIFACT,
e-invoices (`unitCode="KGM"`) and customs messages. Besides the codes, the
dataset gives each unit's conversion factor to SI units as a number, and groups
the units into sets with a factor to a base unit, which is what ERP and
inventory software need for unit sets and sub-units (kilogram, gram, tonne).

| File | Rows | Description |
| --- | --- | --- |
| [`units.csv`](units.csv) | 2,136 | Every code in Annexes II and III, including deleted and deprecated ones |
| [`unit-quantities.csv`](unit-quantities.csv) | 1,635 | The physical quantity each unit is listed under in Annex I |
| [`unit-sets.csv`](unit-sets.csv) | 153 | Units of six sets with their factor to the set's base unit |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Unit sets

| Set | Base | Units | Examples (factor to base) |
| --- | --- | --- | --- |
| `count` | `C62` one | 12 | `PR` pair 2, `DZN` dozen 12, `CEN` hundred 100, `GRO` gross 144, `MIL` thousand 1000 |
| `mass` | `KGM` kilogram | 24 | `MGM` milligram 0.000001, `GRM` gram 0.001, `TNE` tonne 1000, `LBR` pound 0.45359237 |
| `volume` | `MTQ` cubic metre | 52 | `MLT` millilitre 0.000001, `LTR` litre 0.001, `GLL` US gallon 0.003785412 |
| `length` | `MTR` metre | 31 | `MMT` millimetre 0.001, `CMT` centimetre 0.01, `KMT` kilometre 1000, `INH` inch 0.0254 |
| `area` | `MTK` square metre | 15 | `CMK` square centimetre 0.0001, `DAA` decare 1000, `ACR` acre |
| `energy` | `JOU` joule | 19 | `KWH` kilowatt hour 3600000, `MWH` megawatt hour 3600000000 |

Quantity in the base unit = quantity × `factor_to_base`. To convert between two
units of a set, divide their factors: 1 tonne in grams is 1000 / 0.001 =
1,000,000. To use another base, such as litre for volume, divide every factor by
the factor of the new base (0.001).

How the sets are built:

- **mass, volume, length, area, energy**: the active units that Annex I lists
  under the quantity `mass`, `volume`, `length, breadth, height, …`, `area` and
  `work, energy, potential energy, kinetic energy`, and whose conversion factor
  is a plain multiple of the base unit. Compound units listed under the same
  quantity (pound per degree Fahrenheit, litre per bar) and units expressed in
  another unit (electronvolt, square mile in km²) are left out.
- **count**: the unit `C62` (one, synonym unit) and the active units of
  category 3.7 whose conversion factor is a pure number greater than 1. Rec 20
  has no count category of its own; category 3.7 also holds ratios such as
  percent and parts per million, which have factors below 1 and are left out.
  `H87` (piece), `NAR` (number of articles), `T3` (thousand piece) and `SET`
  have no conversion factor in Rec 20 and are therefore not in the set,
  although many systems treat a piece as one unit.

Units marked deleted (`X`) or deprecated (`D`) are not in any set; litre, gram
and the others above are all active. `HAR` (hectare) is deprecated in Rec 20.

## Fields

### units.csv

| Field | Example | Description |
| --- | --- | --- |
| `code` | `GRM` | Common code |
| `name` | `gram` | English name |
| `description` | | Description, often empty |
| `level_category` | `1S` | `1`, `1S`, `1M` SI units and multiples; `2` UK, US and other equivalents; `3.x` informative |
| `symbol` | `g` | Symbol |
| `conversion_factor` | `10⁻³ kg` | Factor as published |
| `factor` | `0.001` | The factor as a number, where it is a plain multiple |
| `factor_unit` | `kg` | SI unit of `factor` |
| `status` | | Empty active, `X` deleted, `D` deprecated |

### unit-quantities.csv

`sector_number`, `sector`, `quantity` and `code`: one row per unit and quantity
in Annex I. A unit can appear under several quantities (`C62` one is listed
under dozens of dimensionless quantities). Five energy-per-volume units (`KWN`,
`KWS`, `MNJ`, `Q41`, `Q42`) are listed in Annex I without a quantity, so
`quantity` is empty for them.

### unit-sets.csv

`set`, `code`, `name`, `symbol`, `level_category`, `factor_to_base` and
`is_base`, as described above.

## Notes

- **Factors as numbers.** `factor` is computed from the published text: the
  mantissa with its decimal comma and digit groups (`0,453 592 37`), times the
  power of ten (`10⁻³`), followed by one unit. Factors that are expressions,
  such as `(5/9) x K` for degree Fahrenheit or `kg x m`, are left empty
  (`factor` is empty for 466 of the 1,500 codes that have a published factor).
  Numbers below 10⁻⁹ are written in exponent notation (`1e-18`). The factors
  are as precise as Rec 20 prints them (US gallon 3.785412 litres).
- **Source quirks.** Some recent entries write powers and exponents with plain
  digits and a decimal point (`10-18 m3`, `1.667 x 10-2 /s`); they were read as
  10⁻¹⁸ m³ and 0.01667 /s. One factor, `1.667 × 104 W/s` (`Q35`), is ambiguous
  and left empty. Non-breaking spaces were replaced by spaces, and the code
  `MNJ` has a stray `¦` in its status column, which is treated as active.
- **Packaging units.** Rec 20 has deleted its own packaging codes (`BX`, `CT`)
  and refers to Recommendation 21: a packaging code such as `AE` becomes the
  unit code `XAE`. Those `X..` codes are not in this file.
- **Revision.** Revision 17 (2021) is the latest revision published as a
  spreadsheet at the time of retrieval.

## Sources

- [UN/CEFACT Recommendation No. 20, Revision 17, Annexes I to III](https://unece.org/trade/documents/revision-17-annexes-i-iii)
  (`rec20_Rev17e-2021.xlsx`, 298.37 KB), UNECE.
- unece.org blocks scripted downloads, so the file was retrieved on 2026-11-09
  from the copy kept in [mskvarc/cefact-units](https://github.com/mskvarc/cefact-units/blob/HEAD/sources/rec20-rev17.xlsx)
  (305,526 bytes, the size UNECE lists). That project states that it is derived
  from Rec 20 and not affiliated with UNECE.

The workbook was converted with a script and checked for: 2,136 unique codes in
Annexes II and III; every Annex I code present in Annexes II and III; the base
unit of each set present with factor 1; and the factors of common units against
their definitions (gram 0.001 kg, pound 0.45359237 kg, litre 0.001 m³, kilowatt
hour 3.6 MJ).
