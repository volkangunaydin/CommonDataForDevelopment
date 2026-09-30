# Common Data for Development

[English](README.md) | **Türkçe**

Yazılım ve yapay zekâ uygulamalarının tekrar tekrar ihtiyaç duyduğu referans
veriler için açık ve sürümlü bir kaynak: ülkeler, para birimleri, bankalar,
adresler, vergi kuralları, e-fatura kod listeleri ve daha fazlası. Hepsi tek
yerde, tek bir tutarlı biçimde ve her veri setinin kaynağı kayıtlı olarak.

> **Durum:** başlangıç aşamasında. Yapı ve kurallar hazır, veri setleri
> ekleniyor. Planlananlar için [yol haritasına](docs/roadmap.md) bakın.

## Neden

Hemen her iş uygulaması aynı referans verilere ihtiyaç duyar ve her ekip bu
verileri PDF'lerden, kamu sitelerinden ve bakımsız kalmış kod parçalarından
yeniden toplar. Yapay zekâ uygulamalarında ihtiyaç aynıdır, üstüne bir risk
eklenir: gerçek veri verilmediğinde model, banka kodu ya da vergi dairesi
listesi istendiğinde inandırıcı ama yanlış bir cevap üretir.

Bu depo o gerçek veri olmayı hedefler:

- **Dünya çapında kapsam**, gereken yerde ülke düzeyinde ayrıntı.
- **Düz dosyalar** (CSV ve JSON, UTF-8): her dilde ve her araçta çalışır.
- **Kendini tanımlayan yapı**: her veri seti şeması ve kaynaklarıyla gelir.
- **Yapay zekâya hazır**: makinece okunabilir [katalog](catalog.json) ve
  öngörülebilir dizin yapısı sayesinde ajanlar ve RAG hatları veriyi tahmin
  yürütmeden bulup yükleyebilir.

## İçerik

| Alan | Dizin | İçerik |
| --- | --- | --- |
| Dünya | [`data/world/`](data/world/) | Tüm ülkeleri kapsayan veri setleri: ülke kodları, para birimleri, diller, saat dilimleri, birimler, IBAN biçimleri |
| Ülkeler | [`data/countries/<CC>/`](data/countries/) | Alanlara göre gruplanmış ülkeye özel veriler: `address`, `banking`, `tax`, `business`, `calendar` |
| Konular | [`data/topics/`](data/topics/) | Ülkeler üstü konular: [UBL](data/topics/ubl/), [e-fatura](data/topics/e-invoicing/) (e-Fatura, Peppol, EN 16931, …) |

`<CC>`, büyük harfle ISO 3166-1 alpha-2 ülke kodudur (`TR`, `DE`, `US`).

### Mevcut veri setleri

| Veri seti | Dizin | Satır |
| --- | --- | --- |
| Türkiye illeri | [`data/countries/TR/address/provinces`](data/countries/TR/address/provinces/) | 81 |

Tam liste her zaman [`catalog.json`](catalog.json) dosyasındadır.

## Verinin kullanımı

Her veri seti bir klasördür. İçinde veri dosyaları, alanları ve kaynakları
tanımlayan bir `datapackage.json`
([Frictionless Data Package](https://datapackage.org/)) ve kısa bir `README.md`
bulunur.

Bir dosyayı doğrudan indirmek için:

```bash
curl -O https://raw.githubusercontent.com/volkangunaydin/CommonDataForDevelopment/main/data/countries/TR/address/provinces/provinces.csv
```

Veri setlerini programla keşfetmek için:

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

Canlı ortamda `main` yerine bir etikete (tag) ya da commit'e sabitleyin.

### Yapay zekâ uygulamaları ve ajanlar için

[`catalog.json`](catalog.json) ile başlayın, satırları kullanmadan önce alanların
anlamı için veri setinin `datapackage.json` dosyasını okuyun. Yapay zekâ
araçlarıyla veri kullanma ve veri ekleme kuralları [AGENTS.md](AGENTS.md)
dosyasındadır.

## Kısaca kurallar

- UTF-8, LF satır sonu, BOM yok.
- Tablo verisi için CSV, iç içe veri için JSON.
- Alan adları İngilizce ve `snake_case`; yerel dildeki değerler olduğu gibi
  korunur.
- Var olan her yerde uluslararası kodlar: ISO 3166 (ülke), ISO 4217 (para
  birimi), ISO 639 (dil), ISO 8601 (tarih).
- Kodlar metindir. `01`, `1` değildir.

Kuralların tamamı [docs/data-standards.md](docs/data-standards.md) dosyasındadır
(İngilizce).

## Katkı

Katkılara açığız, özellikle henüz kapsanmayan ülkelerin verileri için. Tek kesin
kural: **her satır yetkili bir kaynağa dayandırılabilmelidir.** Pull request
açmadan önce [CONTRIBUTING.md](CONTRIBUTING.md) dosyasını okuyun.

## Lisans

- Kod ve araçlar: [MIT](LICENSE)
- Veri: [CC BY 4.0](LICENSE-DATA.md) (veri setinin `datapackage.json` dosyasında
  aksi belirtilmedikçe)

Veriler olduğu gibi, garanti verilmeden sunulur. Bunlar referans veridir; hukuki,
vergisel ya da finansal tavsiye değildir. Mevzuata tabi süreçlerde kullanmadan
önce resmî kaynaktan doğrulayın.
