# Contributing

Thank you for helping build a shared source of reference data. This page covers
what belongs in the repository and how to add it.

## What belongs here

Reference data that many applications need and that changes slowly:

- Code lists and classifications (countries, currencies, tax codes, units)
- Registries published by authorities (banks, tax offices, administrative divisions)
- Formats and validation rules (IBAN structure, tax ID check digits, postal code patterns)
- Standards material for UBL and e-invoicing (code lists, profiles, document types)

## What does not belong here

- **Personal data** of any kind: names, phone numbers, addresses or IDs of real people.
- **Data you are not allowed to redistribute.** Some widely used registries are
  proprietary (for example the full SWIFT BIC directory, or postal address
  databases sold under licence). If the source does not allow redistribution, do
  not add it; link to it in the dataset README instead.
- **Fast-moving data** such as exchange rates or stock prices. Link to an API.
- **Invented or AI-generated rows.** See below.

## The source rule

Every row must be traceable to an authoritative source: a standards body, a
regulator, a government agency or the organisation that owns the registry.

- Record each source in `datapackage.json` under `sources`, with a URL.
- Prefer the primary source over aggregators, blogs and other repositories.
- Do not add data produced from a language model's memory. Models are useful for
  converting and cleaning source files, but the rows themselves must come from
  the source, and you must check the result against it.

A pull request without sources will not be merged.

## Adding a dataset

1. **Pick the location.**

   | The data covers | Put it in |
   | --- | --- |
   | All countries | `data/world/<dataset>/` |
   | One country | `data/countries/<CC>/<domain>/<dataset>/` |
   | A cross-country subject (UBL, e-invoicing) | `data/topics/<topic>/<dataset>/` |

   `<CC>` is the upper-case ISO 3166-1 alpha-2 code. `<domain>` is one of
   `address`, `banking`, `tax`, `business`, `calendar`. Propose a new domain in
   an issue first if none fits.

2. **Copy the template.** Start from [`templates/dataset/`](templates/dataset/).

3. **Add the data files** following [docs/data-standards.md](docs/data-standards.md).

4. **Fill in `datapackage.json`**: name, title, description, version, licence,
   sources and a schema with a description for every field.

5. **Write the dataset `README.md`**: what the data is, the fields, anything a
   user must know to use it correctly, and the sources.

6. **Register it** in [`catalog.json`](catalog.json) and in the dataset table in
   both [`README.md`](README.md) and [`README.tr.md`](README.tr.md).

7. **Note it** in [`CHANGELOG.md`](CHANGELOG.md).

## Updating a dataset

- Bump `version` in `datapackage.json` and in `catalog.json`
  ([versioning rules](docs/data-standards.md#versioning)).
- Never reuse a code for a different meaning. If an entry is retired, follow the
  [rules for retired entries](docs/data-standards.md#retired-entries).
- State in the pull request which source document or publication date the update
  is based on.

## Pull requests

- One dataset per pull request where possible.
- Describe where the data came from and how you converted it.
- Keep diffs reviewable: do not reorder rows or reformat files unless that is the
  purpose of the change.

## Languages

Documentation is written in English. The root README is also maintained in
Turkish; keep the two in sync when you change either.
