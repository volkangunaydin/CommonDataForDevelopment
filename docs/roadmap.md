# Roadmap

Planned datasets, grouped the same way as the `data/` folder. This is a working
list, not a commitment; priorities follow what contributors need. Open an issue
to propose an addition or to claim an item.

Candidate sources are listed so contributors know where to start. Check each
source's terms of use before redistributing its data.

Status: ✅ available · 🔜 next · ⬜ planned

## World

| Status | Dataset | Candidate source |
| --- | --- | --- |
| 🔜 | Countries (alpha-2, alpha-3, numeric, names) | ISO 3166-1 |
| ✅ | [Currencies](../data/world/currencies/) (code, numeric, minor units, historic) | ISO 4217 |
| ⬜ | Country subdivisions | ISO 3166-2 |
| ⬜ | Languages and locales | ISO 639, Unicode CLDR |
| ⬜ | Time zones | IANA tz database |
| ✅ | [Units of measure](../data/world/units-of-measure/) with unit sets and conversion factors | UN/ECE Recommendation 20 |
| ⬜ | International calling codes | ITU-T E.164 |
| ⬜ | IBAN structure per country | IBAN Registry (ISO 13616) |
| ⬜ | Tax ID formats and check-digit rules per country | National tax authorities |
| ⬜ | Postal code formats per country | Universal Postal Union |

## Countries

Türkiye is the first country being built out and serves as the model for others.

### TR – Türkiye

| Status | Domain | Dataset | Candidate source |
| --- | --- | --- | --- |
| ✅ | address | [Provinces](../data/countries/TR/address/provinces/) | ISO 3166-2:TR |
| ✅ | address | [Districts](../data/countries/TR/address/districts/) | Ministry of Interior, TÜİK, GeoNames |
| ✅ | address | [Countries with Turkish names](../data/countries/TR/address/country/) | Unicode CLDR, GeoNames, Wikidata |
| ⬜ | address | Neighbourhoods and postal codes | PTT |
| ✅ | banking | [Banks](../data/countries/TR/banking/banks/) (name, national bank code; BIC pending) | TCMB, BDDK |
| ✅ | banking | [Card BIN ranges](../data/countries/TR/banking/card-bins/) | BKM BIN API |
| ⬜ | banking | Bank branches | TBB |
| ⬜ | banking | IBAN structure and validation | TCMB |
| ✅ | currency | [Currencies with Turkish names](../data/countries/TR/currency/currencies/) | Unicode CLDR, ISO 4217, GİB |
| ✅ | customs | [Customs tariff codes (GTİP)](../data/countries/TR/customs/gtip/) | TÜİK, Ministry of Trade |
| ⬜ | customs | Duty rates and units of measure per GTİP | Ministry of Trade (tariff schedule, İthalat Rejimi Kararı) |
| ✅ | tax | Tax offices | GİB |
| ✅ | tax | [VAT rates](../data/countries/TR/tax/vat-rates/) with list I and II items | GİB |
| ⬜ | tax | Tax identification number rules (VKN, TCKN) | GİB, NVİ |
| ⬜ | business | Economic activity codes (NACE) | TÜİK, GİB |
| ⬜ | business | Uniform chart of accounts | Ministry of Treasury and Finance |
| ⬜ | calendar | Public holidays | Official Gazette |

### Other countries

The same domains (`address`, `banking`, `currency`, `customs`, `tax`, `business`, `calendar`) apply to
every country. Contributions for any country are welcome; start with its
administrative divisions and banks, which most applications need first.

## Topics

### UBL

| Status | Dataset | Candidate source |
| --- | --- | --- |
| ⬜ | Document types | OASIS UBL 2.1 |
| ⬜ | Common code lists (document type, tax category, payment means) | OASIS UBL, UN/CEFACT |

### E-invoicing

| Status | Region | Dataset | Candidate source |
| --- | --- | --- | --- |
| ✅ | TR | [UBL-TR currency codes](../data/topics/e-invoicing/TR/currency-codes/) | GİB e-Fatura package (schematron) |
| ✅ | TR | [UBL-TR tax exemption codes](../data/topics/e-invoicing/TR/tax-exemption-codes/) | GİB UBL-TR Kod Listeleri |
| ✅ | TR | [UBL-TR VAT withholding codes](../data/topics/e-invoicing/TR/withholding-codes/) | GİB UBL-TR Kod Listeleri |
| ✅ | TR | [UBL-TR unit of measure codes](../data/topics/e-invoicing/TR/unit-codes/) | GİB UBL-TR Kod Listeleri |
| 🔜 | TR | UBL-TR code lists (profiles, invoice types, tax type codes, packaging codes) | GİB UBL-TR Kod Listeleri |
| ⬜ | TR | Document types overview (e-Fatura, e-Arşiv, e-İrsaliye, …) | GİB |
| ⬜ | EU | EN 16931 code lists | European Commission |
| ⬜ | EU | Peppol BIS Billing code lists and participant identifier schemes | OpenPeppol |
| ⬜ | World | E-invoicing systems by country (format, mandate, authority) | National tax authorities |

## Tooling

| Status | Item |
| --- | --- |
| 🔜 | Validation script: every `datapackage.json` is valid and every data file matches its schema |
| 🔜 | CI check on pull requests |
| ⬜ | Generated `catalog.json` instead of hand-maintained |
| ⬜ | Release artifacts in additional formats (JSON, SQL, Parquet) |
| ⬜ | Tagged releases |
