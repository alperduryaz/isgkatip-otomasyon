# İSG Katip Otomasyon Araçları

İSG Katip sisteminde tekrarlayan işlemleri otomatikleştiren web tabanlı araçlar.

## 🚀 Mevcut Araçlar

### 1. Periyodik Kontrol Toplu Ataması
Periyodik kontrol sözleşmelerinin toplu olarak girilmesini sağlar.

📁 **Klasör:** [`periyodik-kontrol/`](./periyodik-kontrol/)

**Özellikler:**
- ✅ Personel yönetimi (LocalStorage)
- ✅ TC dropdown ile hızlı seçim
- ✅ Görev bazlı toplu atama (Mekanik/Elektrik)
- ✅ Ekipman sayılarını toplu yapıştırma
- ✅ Mükerrerlik kontrolü (SGK+TC)
- ✅ Excel-tarzı fill-down
- ✅ Elektrik personeli için otomatik Tesisat filtresi

**Kullanım:**
1. `form.html` dosyasını tarayıcıda aç
2. Personelleri ekle
3. Veriyi hazırla
4. Kopyala
5. İSG Katip'te `bookmarklet.txt` kodunu kullan

---

## 📖 Kurulum

### Form Kullanımı (Offline)
1. `form.html` dosyasını bilgisayarınıza indirin
2. Çift tıklayarak tarayıcıda açın
3. Bookmark olarak kaydedin (isteğe bağlı)

### Bookmarklet Kurulumu
1. `bookmarklet.txt` dosyasını açın
2. Tüm kodu kopyalayın
3. Tarayıcınızda yeni bir bookmark oluşturun
4. URL kısmına kopyaladığınız kodu yapıştırın
5. İSG Katip'te bookmark'a tıklayın

---

## 🛠️ Teknik Detaylar

- **Teknoloji:** Vanilla JavaScript, HTML5, CSS3
- **Depolama:** LocalStorage (tarayıcı bazlı)
- **Uyumluluk:** Chrome, Edge, Firefox
- **Boyut Limiti:** Form ~60KB, Bookmarklet ~16KB

---

## 📝 Lisans

MIT License - Detaylar için [LICENSE](./LICENSE) dosyasına bakın.

---

## 🤝 Katkıda Bulunma

Gelecekte daha fazla otomasyon aracı eklenecektir:
- OSGB sözleşme yönetimi
- Diğer toplu işlemler

---

## ⚠️ Sorumluluk Reddi

Bu araçlar, İSG Katip sisteminde veri girişini hızlandırmak için geliştirilmiştir. Kullanıcılar, girilen verilerin doğruluğundan sorumludur. Araçlar "olduğu gibi" sunulmaktadır.

---

## 📧 İletişim

Sorularınız için GitHub Issues kullanabilirsiniz.

---
**Son Güncelleme:** 2024-12-24
