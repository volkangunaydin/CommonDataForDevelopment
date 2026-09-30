# Guidance for AI agents

This file is for AI coding agents and AI applications working with this
repository, either reading data from it or helping someone contribute to it.

## Reading data

1. Load [`catalog.json`](catalog.json). It lists every dataset with its `id`,
   `path`, scope, country and domain.
2. Open `<path>/datapackage.json`. It names the data files (`resources[].path`)
   and describes every field, including type and constraints.
3. Load the data file. Files are UTF-8; CSV files have a header row.

Things to get right:

- **Codes are strings.** Keep leading zeros (`01`, not `1`).
- **Do not fill gaps.** If a value is not in the dataset, say it is not there.
  Do not supply one from memory and present it as coming from this repository.
- **Check the version.** Reference data changes. `datapackage.json` carries the
  dataset `version` and its `sources`; quote them when accuracy matters.
- **Layout is predictable**, so paths can be constructed:
  - `data/world/<dataset>/`
  - `data/countries/<CC>/<domain>/<dataset>/` (`<CC>` = ISO 3166-1 alpha-2, upper case)
  - `data/topics/<topic>/<dataset>/`

## Contributing data

Follow [CONTRIBUTING.md](CONTRIBUTING.md) and
[docs/data-standards.md](docs/data-standards.md). The rules that matter most for
an agent:

- **Never generate rows from memory.** Every row must come from a source
  document that you or the user actually retrieved. If you cannot access the
  source, stop and ask for it rather than producing a best guess.
- **Verify after converting.** Compare row counts and a sample of values against
  the source, and check declared constraints (uniqueness, patterns).
- **Record the source URL** in `datapackage.json`.
- **Do not add personal data or data that may not be redistributed.**
- **Update the index.** A new dataset must be added to `catalog.json`, both root
  READMEs and `CHANGELOG.md`.
