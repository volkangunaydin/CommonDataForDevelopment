# Common Data for Development

**English** | [Türkçe](README.tr.md)

Open, versioned reference data that software and AI applications need again and
again: countries, currencies, banks, addresses, tax rules, e-invoicing code
lists and more, collected in one place, in one consistent format, with the
source of every dataset recorded.

> **Status:** early stage. The structure and conventions are in place; datasets
> are being added. See the [roadmap](docs/roadmap.md) for what is planned.

## Why

Almost every business application needs the same reference data, and every team
ends up collecting it again from PDFs, government sites and half-maintained
gists. AI applications have the same need with an extra twist: a model asked for
a bank code or a tax office list will happily produce a plausible but wrong one
unless it is given real data to work from.

This repository aims to be that real data:

- **Worldwide scope** with country-level detail where it matters.
- **Plain files** (CSV and JSON, UTF-8) that work in any language and tool.
- **Self-describing**: every dataset ships with a schema and its sources.
- **AI-ready**: a machine-readable [catalog](catalog.json) and predictable paths
  so agents and RAG pipelines can find and load data without guessing.

## What is inside

| Area | Path | Contents |
| --- | --- | --- |
| World | [`data/world/`](data/world/) | Datasets that cover all countries: country codes, currencies, languages, time zones, units, IBAN formats |
| Countries | [`data/countries/<CC>/`](data/countries/) | Country-specific data grouped by domain: `address`, `banking`, `tax`, `business`, `calendar` |
| Topics | [`data/topics/`](data/topics/) | Cross-cutting subjects: [UBL](data/topics/ubl/), [e-invoicing](data/topics/e-invoicing/) (e-Fatura, Peppol, EN 16931, …) |

`<CC>` is the ISO 3166-1 alpha-2 country code in upper case (`TR`, `DE`, `US`).

### Available datasets

| Dataset | Path | Rows |
| --- | --- | --- |
| Provinces of Türkiye | [`data/countries/TR/address/provinces`](data/countries/TR/address/provinces/) | 81 |

The full list is always in [`catalog.json`](catalog.json).

## Using the data

Every dataset is a folder containing the data files, a `datapackage.json`
([Frictionless Data Package](https://datapackage.org/)) describing fields and
sources, and a short `README.md`.

Fetch a file directly:

```bash
curl -O https://raw.githubusercontent.com/volkangunaydin/CommonDataForDevelopment/main/data/countries/TR/address/provinces/provinces.csv
```

Or discover datasets programmatically:

```python
import csv, io, json, urllib.request

BASE = "https://raw.githubusercontent.com/volkangunaydin/CommonDataForDevelopment/main/"

catalog = json.load(urllib.request.urlopen(BASE + "catalog.json"))
dataset = next(d for d in catalog["datasets"] if d["id"] == "tr-address-provinces")

package = json.load(urllib.request.urlopen(f"{BASE}{dataset['path']}/datapackage.json"))
resource = package["resources"][0]

with urllib.request.urlopen(f"{BASE}{dataset['path']}/{resource['path']}") as f:
    rows = list(csv.DictReader(io.TextIOWrapper(f, encoding="utf-8")))
```

For production use, pin to a tag or commit instead of `main`.

### For AI applications and agents

Start from [`catalog.json`](catalog.json), then read the dataset's
`datapackage.json` for field meanings before using the rows. See
[AGENTS.md](AGENTS.md) for guidance on both consuming and contributing data with
AI tools.

## Conventions in brief

- UTF-8, LF line endings, no BOM.
- CSV for tabular data, JSON for nested data.
- English `snake_case` field names; local-language values are kept as they are.
- International codes wherever they exist: ISO 3166 (countries), ISO 4217
  (currencies), ISO 639 (languages), ISO 8601 (dates).
- Codes are strings. `01` is not `1`.

The full rules are in [docs/data-standards.md](docs/data-standards.md).

## Contributing

Contributions are welcome, especially data for countries not yet covered. The
one firm rule: **every row must be traceable to an authoritative source.** Read
[CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request.

## License

- Code and tooling: [MIT](LICENSE)
- Data: [CC BY 4.0](LICENSE-DATA.md), unless a dataset's `datapackage.json`
  states otherwise

The data is provided as is, without warranty. It is reference data, not legal,
tax or financial advice; verify against the official source before relying on it
for regulated processes.
