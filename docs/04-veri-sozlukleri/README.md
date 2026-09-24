# Veri Sözlükleri

Her çocuk diyagramdaki veri akışları ve veri depoları için ayrı bir veri sözlüğü hazırlandı. Her dosya standart bir yapı izler:

1. **Akış Bilgisi** — akışın kaynağı, adı ve hedefi (örn. `Öğrenci → Grup Kurma Talebi → Süreç 11.1`)
2. **Veri Yapıları** — akışın yapısal gösterim (`=`, `+`, `[ ]`, `{ }`, `( )`) ile tanımı
3. **Detaylı Veri Sözlüğü** — her veri elemanı için tip, format, açıklama ve örnek değer

| Dosya | İlgili Süreç | Kapsam |
|---|---|---|
| [`profil-yonetimi-veri-sozlugu.xlsx`](profil-yonetimi-veri-sozlugu.xlsx) | Süreç 2.2 — Profil Güncelleme | Kullanıcı ID, ad soyad, e-posta, üniversite, bölüm, sınıf, dil seviyesi, ülke tercihi, profil fotoğrafı |
| [`forum-ve-topluluk-veri-sozlugu.xlsx`](forum-ve-topluluk-veri-sozlugu.xlsx) | Süreç 8.1 — Forum Yazısı Oluşturma | Gönderi ID, kullanıcı bilgisi, başlık/içerik, etiket, görsel URL + `D7 Forum Gönderileri` veri deposu |
| [`grup-olusturma-veri-sozlugu.xlsx`](grup-olusturma-veri-sozlugu.xlsx) | Süreç 11.1 — Ülke/Üniversiteye Göre Grup Kurma | Grup kurma talebi: kullanıcı ID, ülke/üniversite tercihi, grup adı, talep tarihi |
| [`universite-karsilastirma-veri-sozlugu.xlsx`](universite-karsilastirma-veri-sozlugu.xlsx) | Süreç 5.1 — Üniversite Arama ve Filtreleme | Arama kriterleri: ülke, şehir, bölüm, dil, minimum sıralama, burs durumu + `Veri Deposu` sayfası |

İlgili DFD çocuk diyagramları için bkz. [`docs/02-veri-akis-diyagramlari/cocuk-diyagramlar`](../02-veri-akis-diyagramlari/cocuk-diyagramlar).
