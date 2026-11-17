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
| Ülkeler | [`data/countries/<CC>/`](data/countries/) | Alanlara göre gruplanmış ülkeye özel veriler: `address`, `banking`, `currency`, `customs`, `tax`, `business`, `calendar` |
| Konular | [`data/topics/`](data/topics/) | Ülkeler üstü konular: [UBL](data/topics/ubl/), [e-fatura](data/topics/e-invoicing/) (e-Fatura, Peppol, EN 16931, …) |

`<CC>`, büyük harfle ISO 3166-1 alpha-2 ülke kodudur (`TR`, `DE`, `US`).

### Mevcut veri setleri

| Veri seti | Dizin | Satır |
| --- | --- | --- |
| Ülkeler (ISO 3166-1) | [`data/world/countries`](data/world/countries/) | 250 |
| Para birimleri (ISO 4217) | [`data/world/currencies`](data/world/currencies/) | 178 + 169 tarihsel |
| Ölçü birimleri (UN/ECE Rec 20), birim setleri ve katsayıları | [`data/world/units-of-measure`](data/world/units-of-measure/) | 2.136 + setlerde 153 |
| Türkiye illeri | [`data/countries/TR/address/provinces`](data/countries/TR/address/provinces/) | 81 |
| Türkiye ilçeleri | [`data/countries/TR/address/districts`](data/countries/TR/address/districts/) | 973 |
| Türkiye mahalleleri ve posta kodları | [`data/countries/TR/address/neighbourhoods`](data/countries/TR/address/neighbourhoods/) | 72.780 |
| Ülkeler (Türkçe adlarla) | [`data/countries/TR/address/country`](data/countries/TR/address/country/) | 250 |
| Türkiye vergi daireleri | [`data/countries/TR/tax/tax-offices`](data/countries/TR/tax/tax-offices/) | 860 + 233 şube |
| KDV oranları, (I) ve (II) sayılı liste sıraları | [`data/countries/TR/tax/vat-rates`](data/countries/TR/tax/vat-rates/) | 5 oran + 79 liste sırası |
| Türkiye bankaları | [`data/countries/TR/banking/banks`](data/countries/TR/banking/banks/) | 70 |
| Türkiye kart BIN aralıkları | [`data/countries/TR/banking/card-bins`](data/countries/TR/banking/card-bins/) | 1.540 |
| Türkçe adlarıyla para birimleri | [`data/countries/TR/currency/currencies`](data/countries/TR/currency/currencies/) | 193 |
| Gümrük tarife istatistik pozisyonları (GTİP 2026) | [`data/countries/TR/customs/gtip`](data/countries/TR/customs/gtip/) | 15.753 GTİP + 16.814 üst düzey |
| UBL-TR para birimi kodları (e-Fatura) | [`data/topics/e-invoicing/TR/currency-codes`](data/topics/e-invoicing/TR/currency-codes/) | 193 |
| UBL-TR vergi istisna kodları (e-Fatura) | [`data/topics/e-invoicing/TR/tax-exemption-codes`](data/topics/e-invoicing/TR/tax-exemption-codes/) | 112 |
| UBL-TR KDV tevkifat kodları (e-Fatura) | [`data/topics/e-invoicing/TR/withholding-codes`](data/topics/e-invoicing/TR/withholding-codes/) | 52 |
| UBL-TR ölçü birimi kodları (e-Fatura) | [`data/topics/e-invoicing/TR/unit-codes`](data/topics/e-invoicing/TR/unit-codes/) | 39 |
| UBL-TR senaryo / ProfileID kodları (e-Fatura) | [`data/topics/e-invoicing/TR/profile-ids`](data/topics/e-invoicing/TR/profile-ids/) | 16 |
| UBL-TR fatura tip kodları (e-Fatura) | [`data/topics/e-invoicing/TR/invoice-type-codes`](data/topics/e-invoicing/TR/invoice-type-codes/) | 20 |
| UBL-TR vergi tip kodları (e-Fatura) | [`data/topics/e-invoicing/TR/tax-type-codes`](data/topics/e-invoicing/TR/tax-type-codes/) | 31 |
| UBL-TR paket/kap cins kodları (e-Fatura) | [`data/topics/e-invoicing/TR/packaging-type-codes`](data/topics/e-invoicing/TR/packaging-type-codes/) | 27 |
| UBL-TR ödeme şekli kodları (e-Fatura) | [`data/topics/e-invoicing/TR/payment-means-codes`](data/topics/e-invoicing/TR/payment-means-codes/) | 75 |
| UBL-TR uygulama yanıt kodları (e-Fatura) | [`data/topics/e-invoicing/TR/response-codes`](data/topics/e-invoicing/TR/response-codes/) | 5 |
| UBL-TR taşıma gönderim şekli kodları (e-Fatura) | [`data/topics/e-invoicing/TR/transport-mode-codes`](data/topics/e-invoicing/TR/transport-mode-codes/) | 10 |
| UBL-TR INCOTERMS teslim şekli kodları (e-Fatura) | [`data/topics/e-invoicing/TR/incoterms-codes`](data/topics/e-invoicing/TR/incoterms-codes/) | 15 |
| UBL-TR PartyIdentification schemeID değerleri (e-Fatura) | [`data/topics/e-invoicing/TR/party-identification-schemes`](data/topics/e-invoicing/TR/party-identification-schemes/) | 30 |
| UBL-TR AdditionalItemIdentification şemaları (e-Fatura) | [`data/topics/e-invoicing/TR/additional-item-identification-schemes`](data/topics/e-invoicing/TR/additional-item-identification-schemes/) | 6 |
| UBL-TR ihraç kayıtlı party identification şemaları (e-Fatura) | [`data/topics/e-invoicing/TR/ihrac-kayitli-party-identification-schemes`](data/topics/e-invoicing/TR/ihrac-kayitli-party-identification-schemes/) | 2 |
| UBL-TR Yatırım Teşvik kalem sınıflandırma kodları (e-Fatura) | [`data/topics/e-invoicing/TR/yatirim-tesvik-item-classification-codes`](data/topics/e-invoicing/TR/yatirim-tesvik-item-classification-codes/) | 4 |
| UBL-TR irsaliye tip kodları (e-İrsaliye) | [`data/topics/e-invoicing/TR/despatch-advice-type-codes`](data/topics/e-invoicing/TR/despatch-advice-type-codes/) | 2 |
| Vergi / kimlik no biçim kuralları (VKN, TCKN) | [`data/countries/TR/tax/tax-id-rules`](data/countries/TR/tax/tax-id-rules/) | 2 |
| NACE Rev. 2.1 faaliyet kodları | [`data/countries/TR/business/nace`](data/countries/TR/business/nace/) | 3.190 |
| Tekdüzen hesap planı | [`data/countries/TR/business/uniform-chart-of-accounts`](data/countries/TR/business/uniform-chart-of-accounts/) | 352 |
| Türkiye resmi tatilleri | [`data/countries/TR/calendar/public-holidays`](data/countries/TR/calendar/public-holidays/) | 9 kural + 9 tarih (2026) |
| IBAN yapısı ve doğrulama (TR) | [`data/countries/TR/banking/iban`](data/countries/TR/banking/iban/) | 1 + 5 alan |
| Elektronik belge türleri özeti (e-Belge) | [`data/topics/e-invoicing/TR/document-types`](data/topics/e-invoicing/TR/document-types/) | 14 |

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
