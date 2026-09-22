# 🎓 ErasmusGO

**Türk üniversite öğrencilerinin Erasmus başvuru ve hazırlık sürecini tek platformda toplayan web platformu.**

> Sakarya Üniversitesi Yönetim Bilişim Sistemleri bölümü, *Sistem Analizi ve Tasarımı* dersi kapsamında 4 kişilik bir ekip tarafından geliştirilmiştir. Platform ders süresince canlı ortamda yayınlanmış, dönem sonunda sunucular kapatılmıştır. Bu repo projenin analiz, tasarım ve arayüz çalışmalarını belgelemektedir.

![Ana Sayfa](docs/06-arayuz-tasarimi/ana-sayfa.png)

---

## 📌 Problem

Erasmus'a gitmek isteyen öğrenciler başvuru adımlarını, üniversite seçeneklerini, gerekli belgeleri, yaşam maliyetlerini ve dil hazırlığını farklı kaynaklardan (statik PDF rehberler, sosyal medya grupları, üniversite siteleri) toplamak zorunda kalıyor. Bilgiler dağınık, çoğu zaman güncel değil ve Türkçe kaynak sınırlı.

## 💡 Çözüm

ErasmusGO, başvuru öncesi araştırmadan yurt dışına çıkışa kadar tüm hazırlık sürecini tek bir dijital platformda yönetmeyi hedefler.

| Alan | Tasarlanan Özellikler |
|---|---|
| **Hesap & Erişim** | E-posta doğrulamalı kayıt, Google/Apple ile giriş, profil yönetimi |
| **Kullanıcı Rolleri** | Erasmus'a gitmemiş öğrenci, deneyimli öğrenci ve akademisyen rolleri |
| **Başvuru & Bilgi** | Adım adım başvuru rehberi, ülke/üniversite karşılaştırma, belge takibi |
| **Bildirimler** | Son tarihlere 7 gün ve 1 gün kala hatırlatıcı |
| **Topluluk** | Liyakat sistemli forum, deneyim paylaşımı, aynı ülkeye gidecek öğrencilerle grup kurma |
| **Dil & Akademik** | Dil hazırlık modülü, staj ve ders planlama, yaşam maliyeti hesaplama |
| **Güvenlik** | KVKK uyumu, şifre hashleme, başarısız girişlerde hesap kilitleme |

---

## 🔍 Analiz Süreci

Gereksinimler üç kaynaktan derlendi: **kullanıcı ihtiyaç anketi**, **üç platformla kıyaslama (benchmarking)** ve **ekip içi beyin fırtınası**. Sonuçta 13 fonksiyonel ve 6 fonksiyonel olmayan kategori altında 90'ı aşkın gereksinim tanımlandı.

### Kullanıcı İhtiyaç Anketi (33 yanıt)

Katılımcıların 25'i Erasmus'a gitmek isteyen, 7'si Erasmus'a gidip dönmüş öğrenci, 1'i akademisyen/koordinatör. Planlanan özelliklerin önem puanları özelliklerin önceliklendirilmesinde kullanıldı:

![Anket Sonuçları](docs/01-analiz/anket-sonuclari.png)

### Rakip Analizi

ErasmusGO; **ESN Türkiye**, **Erasmus+ resmi platformu** ve **Erasmusu.com** ile karşılaştırıldı. ESN Türkiye kıyaslamasından özet (27 kriter):

| Kriter | ErasmusGO | ESN Türkiye |
|---|:---:|:---:|
| Kullanıcı hesabı ve profil | ✅ | ❌ |
| Başvuru rehberi | ✅ | ⚠️ Statik PDF |
| Üniversite karşılaştırma | ✅ | ❌ |
| Belge ve evrak takibi | ✅ | ❌ |
| Bildirim / hatırlatıcı | ✅ | ❌ |
| Forum ve topluluk | ✅ | ⚠️ Sosyal medya üzerinden |
| Dil hazırlık modülü | ✅ | ❌ |
| Yaşam maliyeti hesaplama | ✅ | ❌ |
| Türkçe içerik | ✅ | ⚠️ Kısmi |
| Fiziksel etkinlikler | ❌ | ✅ |

**Sonuç:** ESN Türkiye, Türkiye'ye gelen uluslararası öğrencilerin sosyal uyumunu fiziksel etkinliklerle destekleyen gönüllü bir ağ. ErasmusGO ise yurt dışına gidecek Türk öğrencilerin **başvuru öncesi hazırlık ve karar verme sürecine** odaklanıyor. Yani iki platform rakip değil, birbirini tamamlıyor.

📄 [Gereksinim Beyanı](docs/01-analiz/gereksinim-beyani.pdf) · [Rakip Analizi (tam tablolar)](docs/01-analiz/rakip-analizi.pdf)

---

## 🗂️ Sistem Tasarımı

### Bağlam Diyagramı
![Bağlam Diyagramı](docs/02-veri-akis-diyagramlari/baglam-diyagrami.png)

### Ebeveyn Diyagramı (Seviye 0)
Diyagram geniş olduğu için tam boyutta açmak için görsele tıklayın.

[![Ebeveyn Diyagramı](docs/02-veri-akis-diyagramlari/ebeveyn-diyagrami.png)](docs/02-veri-akis-diyagramlari/ebeveyn-diyagrami.png)

### Çocuk Diyagramlar (Seviye 1)

| Süreç | Hazırlayan |
|---|---|
| [Profil Yönetimi](docs/02-veri-akis-diyagramlari/cocuk-diyagramlar/profil-yonetimi.png) | Ensar Türk |
| [Forum ve Topluluk](docs/02-veri-akis-diyagramlari/cocuk-diyagramlar/forum-ve-topluluk.png) | Ege Mert Kaya |
| [Grup Oluşturma](docs/02-veri-akis-diyagramlari/cocuk-diyagramlar/grup-olusturma.png) | Canan Bayram |
| [Üniversite Karşılaştırma](docs/02-veri-akis-diyagramlari/cocuk-diyagramlar/universite-karsilastirma.png) | Muhammet Talha Baler |

**Profil Yönetimi (Süreç 2):** Profil görüntüleme, güncelleme, şifre güncelleme, profil doğrulama ve kaydetme alt süreçleri.

![Profil Yönetimi Çocuk Diyagramı](docs/02-veri-akis-diyagramlari/cocuk-diyagramlar/profil-yonetimi.png)

### Mantık Modelleri
Karar ağaçları ve yapısal dil ile süreç mantığının modellenmesi.

| Karar Ağacı 8.1 | Karar Ağacı 11.1.1 (Ülke/Üniversiteye Göre Grup Kurma) |
|---|---|
| ![Karar Ağacı 8.1](docs/03-mantik-modelleri/karar-agaci-8.1.png) | ![Karar Ağacı 11.1.1](docs/03-mantik-modelleri/karar-agaci-11.1.1.png) |

📄 [Mantık Modelleme](docs/03-mantik-modelleri/mantik-modelleme-8.1.pdf) · [Yapısal Dil](docs/03-mantik-modelleri/yapisal-dil-11.1.1.pdf)

### Veri Sözlükleri
Her çocuk diyagramdaki veri akışları ve veri depoları için ayrı veri sözlüğü hazırlandı: [`docs/04-veri-sozlukleri`](docs/04-veri-sozlukleri)

### Varlık İlişki Diyagramları
Veritabanı kavramsal, mantıksal ve fiziksel olmak üzere üç aşamada modellendi.

![Kavramsal ER](docs/05-varlik-iliski-diyagramlari/kavramsal-er.png)

[Mantıksal ER](docs/05-varlik-iliski-diyagramlari/mantiksal-er.png) · [Fiziksel ER](docs/05-varlik-iliski-diyagramlari/fiziksel-er.png)

---

## 🖼️ Arayüz

| Ülke Karşılaştırma | Grup Sohbet Odaları |
|---|---|
| ![Ülke Karşılaştırma](docs/06-arayuz-tasarimi/cikti-ekrani.png) | ![Odalar](docs/06-arayuz-tasarimi/girdi-ekrani.png) |

---

## 🙋 Katkılarım (Ensar Türk)

- **Fikir geliştirme:** Problemin tanımlanması ve platform konseptinin oluşturulmasında aktif rol aldım.
- **Rakip analizi:** ESN Türkiye ile 27 kriter üzerinden kıyaslama analizini yürüttüm.
- **Sistem tasarımı:** Profil Yönetimi çocuk diyagramını ve veri sözlüğünü hazırladım.
- **Arayüz tasarımı:** Kullanıcı arayüzünün tasarımında görev aldım.
- **Yayına alma:** Platformu canlı ortama aldım (deploy).

## 👥 Ekip

Muhammet Talha Baler · Ege Mert Kaya · Ensar Türk · Canan Bayram

---

## 📁 Repo Yapısı

```
ErasmusGO/
├── docs/
│   ├── proje-beyani.pdf              # Projenin tam raporu
│   ├── 01-analiz/                    # Gereksinim beyanı, rakip analizi, anket sonuçları
│   ├── 02-veri-akis-diyagramlari/    # Bağlam, ebeveyn ve çocuk diyagramlar
│   ├── 03-mantik-modelleri/          # Karar ağaçları, yapısal dil
│   ├── 04-veri-sozlukleri/           # Veri sözlükleri (Excel)
│   ├── 05-varlik-iliski-diyagramlari/# Kavramsal, mantıksal, fiziksel ER
│   └── 06-arayuz-tasarimi/           # Arayüz ekran görüntüleri
└── kaynak-dosyalar/drawio/           # Diyagramların düzenlenebilir draw.io dosyaları
```

📄 Projenin tam raporu: [Proje Beyanı](docs/proje-beyani.pdf)
