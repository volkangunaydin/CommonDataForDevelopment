# VAT rates of Türkiye

The value added tax (katma değer vergisi, KDV) rates of Türkiye and the two
lists that decide which goods and services take a reduced rate. The rates are
set by Decree 2007/13033 under article 28 of the VAT Law (3065); this dataset
follows the consolidated text published by the Revenue Administration (Gelir
İdaresi Başkanlığı, GİB). Typically used to set up VAT codes in invoicing and
ERP software and to look up the rate of a product or service.

| File | Rows | Description |
| --- | --- | --- |
| [`vat-rates.csv`](vat-rates.csv) | 5 | The three rates with validity dates, including the rates before 2023-07-10 |
| [`vat-rate-list-items.csv`](vat-rate-list-items.csv) | 79 | One row per item of list I (41) and list II (38) |
| [`vat-rate-list-tariff-lines.csv`](vat-rate-list-tariff-lines.csv) | 155 | Customs tariff lines named in the tables of four items |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Rates

| Rate type | Rate | Since | Before |
| --- | --- | --- | --- |
| `general` (everything not in a list) | 20% | 2023-07-10 | 18% |
| `list_i` | 1% | 2007-12-31 | – |
| `list_ii` | 10% | 2023-07-10 | 8% |

The rates changed on 2023-07-10 by Presidential Decree 7346. `vat-rates.csv`
covers the rates under Decree 2007/13033 only; it starts on 2007-12-31, the day
after the Decree was published, and does not cover earlier decrees.

## Fields

### vat-rates.csv

| Field | Example | Description |
| --- | --- | --- |
| `rate_type` | `general` | `general`, `list_i` or `list_ii` |
| `rate_percent` | `20` | Rate in percent |
| `valid_from` | `2023-07-10` | First day of the rate |
| `valid_to` | | Last day; empty while in force |
| `applies_to` | `Taxable supplies not in list I or II` | Scope in English |
| `legal_basis` | `Decree 2007/13033 art. 1(1)(a) as amended by Presidential Decree 7346` | Provision |

### vat-rate-list-items.csv

| Field | Example | Description |
| --- | --- | --- |
| `list` | `II` | `I` (1%) or `II` (10%) |
| `section` | `B` | `A` (food) or `B` (other) in list I; empty in list II |
| `item` | `14` | Item number (sıra) |
| `rate_percent` | `10` | Rate of the list |
| `status` | `in_force` | `in_force` or `repealed` |
| `text` | `Cenaze hizmetleri.` | Full Turkish text of the item |

### vat-rate-list-tariff-lines.csv

| Field | Example | Description |
| --- | --- | --- |
| `list`, `section`, `item` | `II`, ``, `33` | The item the line belongs to |
| `gtip_printed` | `9403.30` | Tariff position as printed |
| `gtip` | `940330` | Digits only |
| `description` | `Bürolarda kullanılan türden ahşap mobilyalar` | Description as printed |
| `in_gtip_2026` | `true` | Whether the code exists in the 2026 GTİP |

## How to find the rate of a supply

1. Look for the goods or service in list I, then in list II. If it is in neither,
   the general rate applies.
2. Read the whole item text: several items carry their own exceptions. For
   example, newspapers (list I B-8) and books (list II item 14) take the general
   rate when sold electronically; some used car sales under list I B-9 take the
   general rate; and medicines in list II item 18 take 10% even when they are
   also in list I.
3. Read article 1 of the Decree for rules that cut across the lists: ÖTV-liable
   food in list I A takes the list II rate (art. 1(3)), and financial leasing
   takes the rate of the leased goods, except for list I B items 16 and 17
   (art. 1(2)). These rules are in the source text but not in the rows of this
   dataset.
4. A rate depends on the date of the taxable event (KDV Kanunu art. 10), so use
   `valid_from` and `valid_to` for invoices dated before 2023-07-10.

## Notes

- **Customs positions are not current.** The items of list I A and the tables
  name positions of the customs tariff editions in force when each item was
  written (2006/11437, 2007/13007, 2010/1180, 1951, 5045 and others). 28 of the
  155 tariff lines no longer exist as codes in the 2026 GTİP
  (`in_gtip_2026 = false`), mostly agricultural machinery and tractors in list
  II item 28 that have since been renumbered. GİB's footnotes 50 to 52 in the
  source give correlation tables to the 2019 tariff; they are not part of this
  dataset.
- **List I section A** opens with the sentence that its items refer to the tariff
  of Decree 2006/11437; that sentence is not repeated in each row.
- **The tariff table of list I B-17** lists machinery that takes 1% only when
  delivered to a financial leasing company and leased on to the taxpayers the
  item describes. The 1% does not extend to other sales of these machines, and
  the table rows do not carry this condition themselves.
- **Text as published.** The item texts keep GİB's amendment notes and its
  footnote numbers in parentheses, such as `(34)`, which refer to the footnotes
  (dipnotlar) at the end of the source. The footnotes, which give earlier
  wordings, are not part of this dataset. Five items are repealed and keep only
  the repeal note.
- **Temporary rates.** The provisional articles of the Decree (geçici madde 1 to
  10) set temporary rates for periods that have all ended (the last on
  2023-12-31) and are not included.
- **Snapshot.** GİB's text includes amendments up to Presidential Decree 9126
  (in force 2024-11-15). Check the source for later decrees before relying on
  it.

## Source

- [Güncel KDV Oranları, GİB](https://cdn.gib.gov.tr/api/gibportal-file/file/getFileResources?objectKey=arsiv%2Fyardim-kaynaklar%2Fyararli-bilgiler%2Fkdv-oranlari.pdf):
  consolidated text of Decree 2007/13033 with lists I and II and footnotes,
  retrieved 2026-11-09. The rates before 2023-07-10 are from footnotes 102
  (`% 18`) and 103 (`% 8`) of the same text.

The rows were extracted from the PDF text by a script, not retyped, and checked
for: item numbers running without gaps (list I A 1–20, B 1–21, list II 1–38);
every tariff line belonging to an item with a table; and every tariff code
having 4, 6 or 12 digits.
