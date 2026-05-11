# 📱 BES Agresif Takip - Android Widget Dashboard

Flutter ile yazılmış, Android home screen'e widget olarak eklenebilen BES (Bireysel Emeklilik Sistemi) portföy takip uygulaması.

## 🎯 Özellikler

✅ **Flutter Uygulaması**
- Portföy dashboard arayüzü
- 4 fon gerçek zamanlı takibi
- Ağırlıklı getiri hesabı
- Dark mode tasarım
- 15 dakikada bir otomatik güncelleme

✅ **Android Widget**
- Home screen'e sabitlenen widget
- Günlük ortalama getiriyi gösterir
- Otomatik güncelleme
- Tıklanabilir arayüz

## 📦 Yapısı

```
BESFONTAKIP/
├── lib/
│   ├── main.dart                 ← Uygulama giriş noktası
│   ├── screens/
│   │   └── home_screen.dart      ← Dashboard ekranı
│   ├── models/
│   │   └── fund_model.dart       ← Fon veri modeli
│   ├── services/
│   │   └── api_service.dart      ← API ve mock veriler
│   └── widgets/
│       └── fund_card.dart        ← Fon kartı widget'ı
├── android/
│   └── app/src/main/
│       ├── kotlin/
│       │   ├── MainActivity.kt
│       │   ├── ServetWidgetProvider.kt   ← Widget sağlayıcısı
│       │   └── WidgetUpdateService.kt    ← Widget update servisi
│       └── res/
│           ├── layout/
│           │   └── widget_layout.xml     ← Widget arayüzü
│           ├── drawable/
│           │   └── widget_background.xml
│           └── xml/
│               └── widget_info.xml       ← Widget konfigürasyonu
├── pubspec.yaml                 ← Flutter bağımlılıkları
└── README.md
```

## 🚀 Kurulum

### Ön Gereksinimler
- Flutter SDK ≥ 3.0.0
- Android SDK
- Kotlin 1.7+

### Adımlar

1. **Repository'i klonla**
```bash
git clone https://github.com/EvrenGP/BESFONTAKIP.git
cd BESFONTAKIP
```

2. **Bağımlılıkları yükle**
```bash
flutter pub get
```

3. **Uygulamayı çalıştır**
```bash
flutter run
```

4. **Android cihazında widget ekle**
   - Ana ekranda **uzun basıp tut**
   - "Widget Ekle" seçeneğini aç
   - "Servet Dashboard" bul
   - Widget'ı ana ekranda istediğin yere yerleştir
   - Widget otomatik olarak 15 dakikada bir güncellenecek

## 📊 Fonlar ve Ağırlıklar

| Kod | Fon Adı | Ağırlık |
|-----|---------|--------|
| NHN | Zurich 2. Değişken | 35% |
| CHH | QNB 1. Hisse | 25% |
| ALU | Allianz Agresif | 25% |
| CFA | QNB Altın | 15% |

## 🔄 API Entegrasyonu

Şu anda mock veriler kullanılıyor. Kendi API'nı entegre etmek için:

1. `lib/services/api_service.dart` dosyasını aç
2. `fetchFunds()` metodundaki API çağrısını uncomment et
3. Kendi API endpoint'ini kullan:

```dart
static Future<List<Fund>> fetchFunds() async {
  final response = await http.get(
    Uri.parse('https://your-api.com/funds'),
  );
  // ... response'ı parse et
}
```

## 🎨 Widget Güncelleme

Widget'ın görünümünü değiştirmek için:

- **Layout**: `android/app/src/main/res/layout/widget_layout.xml`
- **Stil**: `android/app/src/main/res/drawable/widget_background.xml`
- **Renk ve Yazı**: `lib/widgets/fund_card.dart`

## 🔔 Güncelleme Sıklığı

- **Uygulama**: Her sayfa açıldığında veya "SİSTEMİ GÜNCELLE" butonuna basıldığında
- **Widget**: 15 dakikada bir otomatik güncelleme (değiştirilebilir)

`android/app/src/main/res/xml/widget_info.xml` dosyasında `updatePeriodMillis` değerini değiştir:
- 900000 = 15 dakika
- 1800000 = 30 dakika
- 3600000 = 1 saat

## 📱 Cihaz Gereksinimleri

- **Minimum Android versiyonu**: Android 5.0 (API 21)
- **Flutter SDK**: 3.0.0 ve üzeri
- **Kotlin**: 1.7+

## 🤝 Katkıda Bulun

Öneriler ve bug raporları için GitHub Issues açabilirsin.

## 📄 Lisans

MIT License

## 👤 Geliştirici

**EvrenGP**

---

**Not**: Veriler 15 dakika gecikmesiyle görüntülenir. Hedef emeklilik yaşı: 56.
