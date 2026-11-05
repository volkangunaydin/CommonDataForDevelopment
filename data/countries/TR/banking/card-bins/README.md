# Card BIN ranges of Türkiye

Domestic card BIN ranges (the leading digits of a payment card number that
identify the issuer) as published by the Interbank Card Center of Türkiye
(Bankalararası Kart Merkezi, BKM) through its BIN API. Each range names the
issuing bank or payment institution, the card scheme, the product type and
level, the card programme brand and the card number length. Typically used to
show the bank and card family at checkout, to pick the right virtual POS and
installment table, and to validate card numbers.

| File | Rows | Description |
| --- | --- | --- |
| [`card-bins.csv`](card-bins.csv) | 1,540 | One row per BIN range |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `bin_range_min` | `53020069` | First BIN of the range, 7 or 8 digits |
| `bin_range_max` | `53020069` | Last BIN of the range, same length |
| `issuer_code` | `0010` | EFT code of the issuer, see [tr-banking-banks](../banks/) |
| `issuer_name` | `T.C.ZİRAAT BANKASI A.Ş.` | Issuer name as given by BKM |
| `scheme` | `mastercard` | `mastercard`, `visa`, `troy`, `amex`, `unionpay`, `diners`, `jcb`, `private_label` |
| `product` | `debit` | `credit`, `debit`, `prepaid` |
| `level` | `debit` | `classic`, `gold`, `business`, `debit`, `maestro`, `electron`, `platinum`, `domestic` |
| `card_type_code` | `BAG` | BKM three-letter card type code |
| `brand_name` | `Bankkart` | Card programme brand, empty when none |
| `brand_code` | `003` | BKM code of the brand, empty when none |
| `card_number_length` | `16` | Length of the card number |

Rows by scheme: 593 Mastercard, 452 TROY, 405 Visa, 43 Amex, 41 UnionPay,
6 private label. Issuers: 40 banks and 30 payment or electronic money
institutions.

## How to match a card number

1. Take the first 8 digits of the card number and compare them with the 8-digit
   ranges; take the first 7 digits and compare them with the 7-digit ranges.
2. A card matches a row when the digits fall between `bin_range_min` and
   `bin_range_max` inclusive (compare as numbers of equal length).
3. The ranges are published by BKM as they are. One pair overlaps: the Garanti
   UnionPay range `90010500`–`91119999` (19-digit cards) and the Halkbank Amex
   BIN `9001203` (16-digit cards). Prefer the narrower range, and use
   `card_number_length` to disambiguate.

Six-digit BINs are no longer sufficient: the schemes moved to 8-digit BINs in
2022 and BKM publishes 8-digit ranges, so one old 6-digit BIN can now belong to
several issuers.

## Notes

- **Scope.** All ranges served by the BKM BIN API, which covers cards issued in
  Türkiye under domestic and international schemes. Cards issued abroad are not
  included.
- **Issuer names** are BKM's own spelling and abbreviate some titles
  (`T.GARANTİ BANKASI A.Ş.`). Join on `issuer_code` with
  [tr-banking-banks](../banks/) for the official title. Payment and electronic
  money institutions (codes `0825` to `0935`) and Golden Global Yatırım Bankası
  (`0150`, removed from the TCMB systems on 2026-09-18) are not in that dataset.
- **Card type.** BKM publishes one text such as `MasterCard - Kredi Kartı -
  Classic` plus a three-letter code; `scheme`, `product` and `level` are that
  text split and translated to fixed English tokens, and `card_type_code` is the
  code unchanged. BKM also serves boolean flags (`isVisa`, `isGold`, ...) and a
  `validateForCheckDigit` field; the flags are redundant with the card type and
  the check digit field was `false` for every row, so they are not included.
- **Changes daily.** BKM adds and removes ranges as issuers launch and retire
  products. This file is a snapshot of 2026-10-31; refresh it from the API
  before relying on it for live traffic.
- **Access.** The BKM BIN API is free of charge and needs no contract; since
  2024-12-16 it is open to any organisation, not only BKM members. Credentials
  (client id and secret) are requested from BKM by e-mail (binapi@bkm.com.tr),
  and each organisation may query it five times a day.

## Sources

- **BKM BIN API Servisi**, Bankalararası Kart Merkezi A.Ş. The data in this
  dataset is the API response of 2026-10-31, converted field by field (see
  Notes). [BKM BIN API Servisi tanıtım dokümanı, Ocak 2026](https://github.com/hazarkarabay/guncel-kart-bin-listesi/blob/master/BKM%20BIN%20API%20Servisi.pdf)
  describes the service, its history and access terms.
- **Retrieved via** [guncel-kart-bin-listesi, release 2026-10-31](https://github.com/hazarkarabay/guncel-kart-bin-listesi/releases/tag/2026-10-31),
  an independent project that calls the BKM BIN API daily and publishes the
  unmodified response as `binlist.json`. The project states that it is not
  affiliated with BKM. Direct retrieval from the API, with this repository's own
  credentials, is planned for the next refresh.

The export was converted with a script and checked for: row count (1,540 in and
out), uniqueness of the (`bin_range_min`, `bin_range_max`) pair, one consistent
`brand_code` per brand name, and every `issuer_code` of a bank matching a code in
`tr-banking-banks` (40 of 70 issuers; the other 30 are payment institutions).
