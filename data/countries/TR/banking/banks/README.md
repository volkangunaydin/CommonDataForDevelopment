# Banks of Türkiye

Banks and other participants of the payment systems run by the Central Bank of
the Republic of Türkiye (TCMB), with the four-digit national bank code (the
"EFT code") that identifies them in transfers and IBANs. Names and categories
come from the register of the banking regulator (BDDK). Typically used to
populate bank pick lists and to resolve the bank from an IBAN.

| File | Rows | Description |
| --- | --- | --- |
| [`banks.csv`](banks.csv) | 70 | One row per TCMB payment system participant |
| [`datapackage.json`](datapackage.json) | – | Metadata and field schema |

## Fields

| Field | Example | Description |
| --- | --- | --- |
| `code` | `0046` | Four-digit TCMB participant code, unique |
| `name` | `AKBANK T.A.Ş.` | Official title (BDDK register) |
| `type` | `deposit_bank` | `deposit_bank`, `participation_bank`, `development_investment_bank`, `tmsf_bank`, `central_bank`, `other_participant` |
| `digital_bank` | `false` | BDDK marks the bank as *Dijital Banka* |
| `fast_participant` | `true` | Listed in the TCMB FAST participant list |
| `website` | `http://www.akbank.com` | Web address from BDDK, may be empty |

Rows by type: 35 deposit banks, 11 participation banks, 20 development and
investment banks, 1 bank under TMSF, the central bank and 2 other participants
(Merkezi Kayıt Kuruluşu, PTT).

## Notes

- **Codes are strings** and keep their leading zero. In a Turkish IBAN the bank
  identifier is the five digits after the two check digits, and it is this code
  with one more leading zero (`0046` appears as `00046`).
- **Scope.** The rows are the 70 participants of the TCMB payment systems
  (EFT/EMKT). This includes three participants that are not banks: TCMB itself
  (`0001`), Merkezi Kayıt Kuruluşu (`0806`) and PTT (`0807`). Payment and
  electronic money institutions that take part only in FAST (codes `0825` to
  `0911`) are not included.
- **Names** are the official titles from the BDDK register, in upper case as
  published. The TCMB list abbreviates some of them (`T. İŞ BANKASI A.Ş.` for
  `TÜRKİYE İŞ BANKASI A.Ş.`); the BDDK title is used here. Where the two lists
  differ because of a recent rename, the TCMB footnotes agree with BDDK
  (`0137` Rabobank to Hepsi Bank, `0096` Turkish Bank to Freedom Bank, `0111`
  QNB Finansbank to QNB Bank).
- **Join.** Rows were joined on the EFT code that BDDK publishes for each bank.
  Five BDDK entries had no code (Freedom Bank, Hepsi Bank, Tera Yatırım Bankası,
  Adil Katılım Bankası, Hayat Finans Katılım Bankası); they were matched to the
  TCMB row of the same name.
- **İktisat Katılım Bankası (`0216`)** joined the TCMB systems on 2026-08-07 and
  was not yet in the BDDK web list when retrieved, so its name comes from TCMB
  and its type from its title; it has no website here.
- **Golden Global Yatırım Bankası** is still in the BDDK list but was removed from
  the TCMB systems on 2026-09-18 and has no code there, so it is not included.
- No BIC (SWIFT) codes yet; the regulator lists do not carry them and the BIC
  directory itself is proprietary.
- Snapshot of the lists as retrieved on 2026-10-31. Check the sources for banks
  admitted, renamed or removed since.

## Sources

- [TCMB Ödeme Sistemleri Katılımcıları (2026)](https://www.tcmb.gov.tr/wps/wcm/connect/9fa62a85-5b6d-46c5-9b01-eb461d43723d/TCMB+%C3%96deme+Sistemleri+Kat%C4%B1l%C4%B1mc%C4%B1lar%C4%B1+(072025).pdf?MOD=AJPERES) – codes and participant list
- [FAST Sistemi Katılımcı Listesi (2026)](https://www.tcmb.gov.tr/wps/wcm/connect/954e041c-582d-4d1a-bd35-ff78e7c277b8/FAST+S%C4%B0STEM%C4%B0+KATILIMCILARI.pdf?MOD=AJPERES) – `fast_participant`
- [BDDK – Bankalar (Yetkili Kuruluşlar)](https://www.bddk.org.tr/Kurulus/Liste/77) – official titles, categories, digital bank flag, websites

The PDFs were converted to text and parsed; the BDDK page was parsed from its
HTML, which carries the EFT code of each bank. The result was checked against the
counts in the sources (70 TCMB participants; 35 + 21 + 10 + 1 BDDK banks, of which
66 have a TCMB code) and for uniqueness of codes.
