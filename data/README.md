# Data

```
data/
├── world/                        # datasets covering all countries
│   └── <dataset>/
├── countries/                    # country-specific datasets
│   └── <CC>/                     # ISO 3166-1 alpha-2, upper case
│       └── <domain>/             # address | banking | tax | business | calendar
│           └── <dataset>/
└── topics/                       # cross-country subjects
    └── <topic>/                  # ubl | e-invoicing
        └── <dataset>/
```

Each `<dataset>` folder contains its data files, a `datapackage.json` and a
`README.md`. See [data standards](../docs/data-standards.md) for the rules and
[`catalog.json`](../catalog.json) for the list of datasets.

## Where does a dataset go?

- It has one row per country, or applies to all countries → `world/`
- It describes one country → `countries/<CC>/<domain>/`
- It belongs to a standard or subject that spans countries → `topics/<topic>/`.
  Country-specific parts of a topic go in a country subfolder of the topic, for
  example `topics/e-invoicing/TR/`.
