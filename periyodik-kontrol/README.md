# Periyodik Kontrol Toplu Ataması

İSG Katip'te periyodik kontrol sözleşmelerinin toplu olarak girilmesini sağlayan araç.

## 📋 İçindekiler
- [Özellikler](#özellikler)
- [Kullanım](#kullanım)
- [Form Özellikleri](#form-özellikleri)
- [Bookmarklet Kullanımı](#bookmarklet-kullanımı)
- [Sık Sorulan Sorular](#sık-sorulan-sorular)

---

## ✨ Özellikler

### 🧑‍💼 Personel Yönetimi
- LocalStorage tabanlı personel veritabanı
- TC No, Ad Soyad, Görev (Elektrik/Mekanik)
- Export/Import (JSON)
- Arama ve filtreleme

### 📝 Akıllı Form
- TC dropdown ile hızlı personel seçimi
- Görev bazlı toplu atama (Mekanik → 5 kayıt, Elektrik → 3 kayıt)
- Toplu SGK yapıştırma (Excel'den kopyala)
- Excel-tarzı fill-down (▼ butonları)

### ⚡ Elektrik Personeli Filtresi
- Elektrik personeli seçilince sadece Tesisat aktif
- Diğer ekipman alanları pasif (değerler korunur)
- Çıktıda otomatik filtreleme (sadece Tesisat)

### ✅ Validasyon
- SGK No: 26 haneli rakam kontrolü
- TC No: 11 haneli rakam kontrolü
- Mükerrerlik kontrolü (SGK+TC kombinasyonu unique)
- Görev bazlı personel kontrolü

---

## 🚀 Kullanım

### 1️⃣ Form Hazırlama

**Adım 1: Personel Ekle**
```
[👥 Personeller] butonuna tıkla
→ TC: 12345678901
→ Ad Soyad: Ahmet Yılmaz
→ Görev: Elektrik
→ [➕ Ekle]
```

**Adım 2: Veri Gir**
```
SGK No: 24939080813168300343020000
TC: [Dropdown'dan seç]
  → Ahmet Yılmaz (tek kişi) VEYA
  → ⚡ Elektrik (3 personel - toplu)
Ekipmanlar: 1, 2, 3...
```

**Adım 3: Toplu İşlemler**
- **SGK Yapıştır:** 10+ SGK numarasını kopyala → SGK input'a yapıştır → Otomatik dağılır
- **Fill Down:** SGK/TC yanındaki ▼ → Alta kopyala
- **Ekipman Kopyala:** Satır sonundaki ▼ → Tüm ekipmanları kopyala

**Adım 4: Ekle ve Kopyala**
```
[Tümünü Ekle] → Çıktıya ekle
[📋 Tümünü Kopyala] → Panoya kopyala
```

---

### 2️⃣ İSG Katip'te Kullanım

**Adım 1: Bookmarklet Kur**
```
1. bookmarklet.txt dosyasını aç
2. Tüm kodu kopyala
3. Tarayıcıda yeni bookmark oluştur
4. URL: [Kopyalanan kodu yapıştır]
5. İsim: "Periyodik Kontrol"
```

**Adım 2: Çalıştır**
```
1. İSG Katip'te giriş yap
2. Bookmark'a tıkla
3. Modal açılır
4. Veriyi yapıştır
5. [Kontrol Et] → Validasyon
6. [Toplu Kayıt Gir] → Otomatik gönder
```

---

## 🎯 Form Özellikleri

### Personel Dropdown
```
┌────────────────────────────────────┐
│ 🔧 Mekanik (5 personel)            │ ← Seçince 5 kayıt
│ ⚡ Elektrik (3 personel)           │ ← Seçince 3 kayıt
├────────────────────────────────────┤
│ 12345678901 - Ahmet (Elektrik)     │ ← Seçince 1 kayıt
│ 23456789012 - Mehmet (Mekanik)     │
└────────────────────────────────────┘
```

**Arama:** Yazarak filtrele (TC, isim, görev)
**Klavye:** ↑↓ navigate, Enter seç, ESC kapat

### Toplu SGK Yapıştırma
```
Excel/Notepad'den kopyala:
24939080813168300343020000
24939080813168300343020001
24939080813168300343020002

SGK input'a yapıştır → Otomatik 3 satıra dağılır
```

**Özellikler:**
- ✅ Otomatik temizlik (boşluk, harf)
- ✅ 26 hane validasyonu
- ✅ Alt satır doluysa araya ekler

### Fill Down (▼)
```
Satır 1: SGK | TC | Ekipmanlar
         [▼] [▼] [▼]

Alt satır boş → Direkt kopyala
Alt satır dolu → "Araya ekle / Üzerine yaz" sor
```

### Elektrik Filtresi
```
Elektrik seçilince:
[BK] [KE] [TS] [TZ] [RF] [İM] [LP] [YM] [KK] [AE]
 ⬛   ⬛   ✅   ⬛   ⬛   ⬛   ⬛   ⬛   ⬛   ⬛
 gri  gri aktif gri  gri  gri  gri  gri  gri  gri

Çıktıda:
322;SGK;TC;0;0;10;0;0;0;0;0;0;0
           ↑
      Sadece Tesisat
```

---

## 📤 Bookmarklet Kullanımı

### Veri Formatı
```
Tür;SGKNo;TCNo;BK;KE;TS;TZ;RF;İM;LP;YM;KK;AE

Örnek:
322;24939080813168300343020000;12345678901;1;2;3;4;5;6;7;8;9;10
```

### Validasyon Kuralları
- **Tür:** Sayı (varsayılan: 322)
- **SGK No:** 26 haneli rakam
- **TC No:** 11 haneli rakam
- **Ekipmanlar:** 0-9999 arası sayılar

### Toplu İşlem
```
Modal'a 10+ satır yapıştır
→ [Kontrol Et] → Hataları göster
→ [Toplu Kayıt Gir] → API'ye gönder
→ Her kayıt 2 saniye arayla işlenir
→ Sonuç: "✅ 8 başarılı, ❌ 2 hata"
```

---

## ❓ Sık Sorulan Sorular

### Personeller kayboldu!
**Cevap:** LocalStorage tarayıcı bazlıdır. Aynı dosyayı farklı isimle indirirseniz (`form-1.html`, `form-2.html`) farklı domainler olur. Çözüm: Export/Import kullanın.

### Elektrik personeline diğer ekipmanları nasıl atarım?
**Cevap:** Atamazsınız! Elektrik personeline sadece Tesisat atanabilir. Mekanik seçerseniz tüm ekipmanlar aktif olur.

### Mükerrer kayıt nedir?
**Cevap:** Aynı SGK + TC kombinasyonu. Örnek: Aynı işyerine aynı kişiyi 2 kez atama yapılamaz.

### Form temizleniyor mu?
**Cevap:** Hayır! [Tümünü Ekle] basınca form kalır, düzeltip tekrar ekleyebilirsiniz. [🗑️ Formu Temizle] butonu ile manuel temizleyin.

### Bookmarklet çalışmıyor!
**Cevap:** 
1. İSG Katip'te giriş yaptınız mı?
2. Token var mı? (Console: `sessionStorage.getItem('token')`)
3. Bookmarklet kodu tam kopyalandı mı?

---

## 🔧 Teknik Detaylar

### Dosya Boyutları
- `form.html`: ~60KB
- `bookmarklet.txt`: ~16KB

### LocalStorage Keys
```javascript
'isgPersoneller' → Personel listesi (JSON array)
'isgKatipPeriyodikKontrolData' → Çıktı verisi (text)
```

### Tarayıcı Uyumluluğu
- ✅ Chrome 90+
- ✅ Edge 90+
- ✅ Firefox 88+
- ⚠️ Safari (LocalStorage farklı çalışabilir)

### API Endpoints
```
POST /be/bsn-inter/submit
POST /be/quote/updateFlowInstance
POST /be/bsninter/conf/participant/hasRole
```

---

## 📊 Örnek Kullanım Senaryoları

### Senaryo 1: Tek İşyeri - Karma Personel
```
1. SGK: 24939... (İşyeri A)
2. Mekanik seç → 5 kayıt (Yunus, Şeyho, ...)
3. Ahmet seç → 1 kayıt
4. Elektrik seç → 3 kayıt (Ali, Veli, ...)
→ Toplam: 9 kayıt, 1 işyerine
```

### Senaryo 2: Çok İşyeri - Aynı Personel
```
SGK listesi kopyala:
24939...0000
24939...0001
24939...0002

SGK input'a yapıştır
→ 3 satır
→ Her satıra Ahmet seç
→ 3 kayıt, 3 farklı işyerine
```

### Senaryo 3: Elektrik - Sadece Tesisat
```
1. Elektrik seç
2. TS = 10 gir
3. Diğer ekipmanlar pasif (gri)
4. [Tümünü Ekle]
→ Çıktı: 322;SGK;TC;0;0;10;0;0;0;0;0;0;0
```

---

## 🐛 Bilinen Sorunlar

1. **Firefox'ta dropdown bazen kapanmıyor** → ESC tuşu ile kapatın
2. **Çok fazla satır (100+) yavaş çalışır** → 50'şer parça halinde işleyin
3. **LocalStorage 5MB sınırı** → 500+ personel sorun yaratabilir

---

## 📝 Değişiklik Geçmişi

### v2.6 - 2024-12-24
- ✅ Elektrik personeli filtresi
- ✅ Ekipman satırı fill-down butonu
- ✅ Akıllı ekipman kopyalama (boş/dolu kontrol)
- ✅ Form temizleme kaldırıldı (düzenleme kolaylığı)
- ✅ Mükerrerlik kontrolü

### v2.5 - 2024-12-23
- ✅ Personel yönetimi (CRUD)
- ✅ TC dropdown
- ✅ Görev bazlı toplu atama
- ✅ Toplu SGK yapıştırma
- ✅ Export/Import

---

## 📧 Destek

Sorun bildirmek veya öneride bulunmak için GitHub Issues kullanın.

---

**Geliştirici:** Alper Duryaz  
**Lisans:** MIT  
**Son Güncelleme:** 2024-12-24
