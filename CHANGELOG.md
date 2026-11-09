# Changelog

Notable changes to the repository: datasets added, breaking changes to existing
datasets, and changes to the conventions. Each dataset also carries its own
version in its `datapackage.json`.

## Unreleased

### Added

- Repository structure, data standards, contribution guide and dataset template.
- `tr-address-provinces` 0.1.0: the 81 provinces of Türkiye.
- `tr-address-districts` 0.1.0: the 973 districts of Türkiye (İçişleri Bakanlığı names, GeoNames coordinates).
- `tr-address-districts` 0.2.0: new field `tuik_code`, the four-digit TÜİK district code (CL_IBBS 1.2, ADNKS 2025, retrieved 2026-11-05), for all 973 districts; new field `alternate_names` with the spellings used by GİB and GeoNames (13 districts).
- `tr-address-country` 0.1.0: 250 countries and territories with Turkish names (CLDR 49), ISO 3166-1 codes, calling codes, continent, currency and domain (GeoNames), and capitals in Turkish (Wikidata) with GeoNames coordinates (retrieved 2026-11-05).
- `tr-tax-tax-offices` 0.1.0: tax offices of Türkiye (860) and their branches (233), from the GİB list dated 2026-06-18.
- `tr-banking-banks` 0.1.0: the 70 participants of the TCMB payment systems with their EFT bank codes, BDDK titles and categories, and FAST participation (lists retrieved 2026-10-31).
- `tr-banking-card-bins` 0.1.0: the 1,540 domestic card BIN ranges served by the BKM BIN API on 2026-10-31, with issuer, scheme, product, level and brand.
- `world-currencies` 0.1.0: the 178 current ISO 4217 codes with numeric code, minor units and fund flag, the 277 entity assignments and the 169 historic entries (List One published 2026-09-17, List Three 2026-01-01).
- `tr-currency-currencies` 0.1.0: 193 currency codes (current ISO 4217 plus those accepted in e-invoices) with Turkish and English names and symbols from Unicode CLDR 49. New country domain `currency`.
- `tr-customs-gtip` 0.1.0: the 2026 GTİP nomenclature from the TÜİK classification server (retrieved 2026-11-09), 32,567 rows from section down to the 15,753 twelve-digit codes, with parent codes and TÜİK descriptions; the 35 statistics-only codes not in the tariff schedule (Karar Sayısı 10781) and their 48 artificial parents are flagged. New country domain `customs`.
- `e-invoicing-tr-currency-codes` 0.1.0: the 193 currency codes accepted by the GİB UBL-TR schematron (e-Fatura package retrieved 2026-11-05), 15 of them withdrawn from ISO 4217.
