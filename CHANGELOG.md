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
- `tr-tax-vat-rates` 0.1.0: VAT rates under Decree 2007/13033 (20%, 1%, 10%, and 18% and 8% before 2023-07-10), the 79 items of lists I and II and the 155 customs tariff lines in their tables, from GİB's consolidated text (amendments up to Presidential Decree 9126, retrieved 2026-11-09).
- `world-units-of-measure` 0.1.0: the 2,136 codes of UN/CEFACT Recommendation 20 Revision 17 with conversion factors as published and as numbers, the 1,635 unit and quantity pairs of Annex I, and 153 units in six unit sets (count, mass, volume, length, area, energy) with factors to the base unit.
- `e-invoicing-tr-tax-exemption-codes` 0.1.0: the 112 TaxExemptionReasonCode values of UBL-TR Kod Listeleri V1.43 (July 2026): VAT partial and full exemptions, ÖTV and accommodation tax exemptions, special base and export-registered codes, checked against the schematron.
- `e-invoicing-tr-withholding-codes` 0.1.0: the 52 VAT withholding codes (601–627 partial, 801–825 full) with rates from UBL-TR Kod Listeleri V1.43 and the percentages the schematron accepts.
- `e-invoicing-tr-unit-codes` 0.1.0: the 39 units of measure with Turkish names from UBL-TR Kod Listeleri V1.43, linked to Rec 20 and to the unit sets of `world-units-of-measure`.
- `e-invoicing-tr-currency-codes` 0.1.0: the 193 currency codes accepted by the GİB UBL-TR schematron (e-Fatura package retrieved 2026-11-05), 15 of them withdrawn from ISO 4217.
- `e-invoicing-tr-profile-ids` 0.1.0: the 16 ProfileID / scenario codes from UBL-TR Kod Listeleri V1.43, with which schematron ProfileID lists accept each value (retrieved 2026-11-16).
- `e-invoicing-tr-invoice-type-codes` 0.1.0: the 20 InvoiceTypeCode values (18 named in the guide, plus HKSSATIS and HKSKOMISYONCU from the schematron), with Yatırım Teşvik e-Arşiv flags.
- `e-invoicing-tr-tax-type-codes` 0.1.0: the 31 TaxTypeCode values under TaxTotal (29 named in the Vergi Kodları Listesi, plus 0059 and 9015 from the schematron only).
- `e-invoicing-tr-packaging-type-codes` 0.1.0: the 27 PackagingTypeCode values with Turkish names from Kod Listeleri V1.43, all accepted by the schematron.
- `e-invoicing-tr-payment-means-codes` 0.1.0: the 75 PaymentMeansCode values accepted by the UBL-TR schematron, with English names from UN/EDIFACT 4461 D.06A (retrieved 2026-11-16).
- `e-invoicing-tr-response-codes` 0.1.0: the 5 ResponseCode values (KABUL, RED, IADE from the guide; S_APR and GUMRUKONAY from the schematron).
- `e-invoicing-tr-transport-mode-codes` 0.1.0: TransportModeCode values 0–9 (1–8 named in Kod Listeleri §1.10).
- `e-invoicing-tr-incoterms-codes` 0.1.0: the 15 INCOTERMS codes with Turkish and English names from Kod Listeleri §1.14.
- `e-invoicing-tr-party-identification-schemes` 0.1.0: 30 PartyIdentification schemeID values, including the guide/schematron GCB_TESCILNO vs GTB_GCB_TESCILNO difference.
- `e-invoicing-tr-additional-item-identification-schemes` 0.1.0: the 6 AdditionalItemIdentification scheme values from Kod Listeleri §2.3.
- `e-invoicing-tr-ihrac-kayitli-party-identification-schemes` 0.1.0: the 2 DİİB line-code schemeIDs for IHRACKAYITLI invoices (code 702).
- `e-invoicing-tr-yatirim-tesvik-item-classification-codes` 0.1.0: the 4 Yatırım Teşvik item classification codes (01–04) from Kod Listeleri §2.5.
- `e-invoicing-tr-despatch-advice-type-codes` 0.1.0: DespatchAdviceTypeCode values SEVK and MATBUDAN from the schematron (no names in Kod Listeleri V1.43).
- `tr-tax-tax-id-rules` 0.1.0: TCKN (11 digits, last two are check digits per NVİ) and VKN (10 digits in UBL-TR) format rules; unpublished check-digit algorithms intentionally omitted.
- `tr-business-nace` 0.1.0: NACE Rev. 2.1 national classification from TÜİK surumId 1676 (3,190 rows: 23 sections … 2,142 subclasses), retrieved 2026-11-16. New country domain `business`.
- `tr-business-uniform-chart-of-accounts` 0.1.0: Tekdüzen Hesap Planı from 1 Sıra No'lu MSUGT section B (GİB consolidated PDF): 9 classes, 58 groups, 285 ledger accounts.
- `world-countries` 0.1.0: ISO 3166-1 alpha-2/alpha-3/numeric codes with English and French short names (GeoNames + CLDR), 250 rows including user-assigned XK.
- `tr-address-neighbourhoods` 0.1.0: 72,780 neighbourhood–postal-code rows from the PTT Posta Kodu Sorgulama API (81 provinces, 973 districts), retrieved 2026-11-16.
- `tr-calendar-public-holidays` 0.1.0: Law 2429 holiday rules (as amended) and 2026 dates (Diyanet for religious feasts). New country domain `calendar`.
- `tr-banking-iban` 0.1.0: TR IBAN structure and field layout from TCMB Communique 2008/6 and SWIFT IBAN Registry Release 102.
- `e-invoicing-tr-document-types` 0.1.0: overview of 13 e-Belge types from VUK Communique 509 plus e-Defter.
