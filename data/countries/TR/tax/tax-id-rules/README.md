
# Tax and identity number format rules of Türkiye (VKN, TCKN)

Format constraints for **TCKN** (Republic of Türkiye identity number) and
**VKN** (tax identification number). Intended for input masks and first-pass
validation in business software.

| File | Rows | Description |
| --- | --- | --- |
| [`tax-id-rules.csv`](tax-id-rules.csv) | 2 | One row per identifier type |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Important

- **No check-digit formula is shipped here.** NVİ states that TCKN's last two
  digits are check digits calculated from the first nine and that the algorithm
  is shared with public institutions, but it does not publish the formula on its
  website. GİB does not publish a public VKN check-digit algorithm. Per this
  repository's source rule, unpublished algorithms are not invented or copied
  from third-party blogs.
- Format validity ≠ existence. A number that matches `pattern` may still be
  unused; live confirmation requires NVİ / GİB services.
- Keep codes as strings (`0001234567`), never as integers.

## Sources

- [NVİ, T.C. Kimlik No İşlemleri](https://www.nvi.gov.tr/istanbul/tc-kimlik-no-islemleri), retrieved 2026-11-16.
- [e-Fatura Paketi](https://ebelge.gib.gov.tr/dosyalar/kilavuzlar/e-FaturaPaketi%20(29).zip) schematron VKN/TCKN length checks, retrieved 2026-11-16.
