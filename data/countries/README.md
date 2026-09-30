# Countries

Country-specific datasets. Each country has a folder named with its upper-case
ISO 3166-1 alpha-2 code, and inside it one folder per domain.

Path pattern: `data/countries/<CC>/<domain>/<dataset>/`

## Domains

| Domain | Contents |
| --- | --- |
| `address` | Administrative divisions, postal codes, address formats |
| `banking` | Banks, branches, national bank codes, account number rules |
| `tax` | Tax offices, tax types and rates, tax ID rules |
| `business` | Activity codes, company types, chart of accounts |
| `calendar` | Public holidays, working-day rules |

## Countries

| Code | Country | Datasets |
| --- | --- | --- |
| [`TR`](TR/) | Türkiye | 1 |

## Adding a country

Create `data/countries/<CC>/README.md` listing the country's datasets, then add
datasets as described in [CONTRIBUTING.md](../../CONTRIBUTING.md).
