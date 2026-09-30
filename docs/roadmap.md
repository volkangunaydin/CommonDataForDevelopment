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
| 🔜 | Currencies (code, numeric, minor units) | ISO 4217 |
| ⬜ | Country subdivisions | ISO 3166-2 |
| ⬜ | Languages and locales | ISO 639, Unicode CLDR |
| ⬜ | Time zones | IANA tz database |
| ⬜ | Units of measure | UN/ECE Recommendation 20 |
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
| 🔜 | address | Districts | Ministry of Interior, TÜİK |
| ⬜ | address | Neighbourhoods and postal codes | PTT |
| 🔜 | banking | Banks (name, national bank code, BIC) | TCMB, BDDK, TBB |
| ⬜ | banking | Bank branches | TBB |
| ⬜ | banking | IBAN structure and validation | TCMB |
| 🔜 | tax | Tax offices | GİB |
| ⬜ | tax | VAT rates | GİB |
| ⬜ | tax | Tax identification number rules (VKN, TCKN) | GİB, NVİ |
| ⬜ | business | Economic activity codes (NACE) | TÜİK, GİB |
| ⬜ | business | Uniform chart of accounts | Ministry of Treasury and Finance |
| ⬜ | calendar | Public holidays | Official Gazette |

### Other countries

The same domains (`address`, `banking`, `tax`, `business`, `calendar`) apply to
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
| 🔜 | TR | UBL-TR code lists (profiles, invoice types, tax codes, withholding and exemption codes) | GİB e-Belge technical guides |
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
