# E-invoicing

Reference data for electronic invoicing and related electronic documents
(despatch advice, receipts, ledgers) as mandated or standardised by tax
authorities and standards bodies.

Path pattern:

- `data/topics/e-invoicing/<dataset>/` for data spanning countries
- `data/topics/e-invoicing/<CC>/<dataset>/` for one country's system
- `data/topics/e-invoicing/EU/<dataset>/` for European standards (EN 16931, Peppol)

## Scope

- Code lists required to produce valid documents: profiles, invoice types, tax
  codes, exemption and withholding reason codes
- Document types in each system and what they are used for
- An overview of e-invoicing systems by country: format, authority, mandate

Out of scope: schemas, schematron files and official guides themselves. Datasets
link to the authority's distribution rather than copying it.

## Planned

| Region | System |
| --- | --- |
| `TR` | e-Fatura, e-Arşiv Fatura, e-İrsaliye and related e-Belge documents (UBL-TR), published by GİB |
| `EU` | EN 16931 and Peppol BIS Billing |

## Available

| Region | Dataset | Contents |
| --- | --- | --- |
| `TR` | [`currency-codes`](TR/currency-codes/) | Currency codes accepted by the GİB UBL-TR schematron |
| `TR` | [`tax-exemption-codes`](TR/tax-exemption-codes/) | Tax exemption reason codes (KDV, ÖTV, special base, export-registered) |
| `TR` | [`withholding-codes`](TR/withholding-codes/) | VAT withholding codes and rates |
| `TR` | [`unit-codes`](TR/unit-codes/) | Units of measure with Turkish names |
| `TR` | [`profile-ids`](TR/profile-ids/) | Scenario / ProfileID codes |
| `TR` | [`invoice-type-codes`](TR/invoice-type-codes/) | InvoiceTypeCode values |
| `TR` | [`tax-type-codes`](TR/tax-type-codes/) | TaxTypeCode values under TaxTotal |
| `TR` | [`packaging-type-codes`](TR/packaging-type-codes/) | PackagingTypeCode values with Turkish names |
| `TR` | [`payment-means-codes`](TR/payment-means-codes/) | PaymentMeansCode (UN/EDIFACT 4461 names) |
| `TR` | [`response-codes`](TR/response-codes/) | ApplicationResponse ResponseCode values |
| `TR` | [`transport-mode-codes`](TR/transport-mode-codes/) | TransportModeCode values |
| `TR` | [`incoterms-codes`](TR/incoterms-codes/) | INCOTERMS delivery term codes |
| `TR` | [`party-identification-schemes`](TR/party-identification-schemes/) | PartyIdentification schemeID values |
| `TR` | [`additional-item-identification-schemes`](TR/additional-item-identification-schemes/) | AdditionalItemIdentification schemes |
| `TR` | [`ihrac-kayitli-party-identification-schemes`](TR/ihrac-kayitli-party-identification-schemes/) | DİİB line-code schemes for IHRACKAYITLI |
| `TR` | [`yatirim-tesvik-item-classification-codes`](TR/yatirim-tesvik-item-classification-codes/) | Yatırım Teşvik item classification 01–04 |
| `TR` | [`despatch-advice-type-codes`](TR/despatch-advice-type-codes/) | DespatchAdviceTypeCode (SEVK, MATBUDAN) |
| `TR` | [`document-types`](TR/document-types/) | e-Belge document types overview (+ e-Defter) |

See the [roadmap](../../../docs/roadmap.md#e-invoicing) for what is planned.
