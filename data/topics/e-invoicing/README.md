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

No datasets yet. See the [roadmap](../../../docs/roadmap.md#e-invoicing).
