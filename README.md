# Türk Motifleri Memory — APK Kurulum Rehberi

## Dosyalar
- `index.html` — Oyunun tamamı (offline çalışır)
- `manifest.json` — PWA ayarları
- `sw.js` — Service Worker (cache/offline)
- `icons/` — Uygulama ikonları

---

## APK Yapma — Adım Adım

### YOL 1: PWABuilder (En Kolay — 10 dk)

1. **GitHub'a yükle:**
   - github.com adresine git → New Repository → `turk-memory` adını ver
   - Tüm dosyaları yükle (index.html, manifest.json, sw.js, icons klasörü)
   - Settings → Pages → Branch: main → Save
   - URL'in şöyle olacak: `https://KULLANICIN.github.io/turk-memory`

2. **PWABuilder'a git:**
   - https://www.pwabuilder.com adresine git
   - URL kutusuna GitHub Pages adresini yapıştır
   - "Start" butonuna bas

3. **APK indir:**
   - "Android" sekmesine tıkla
   - "Download Package" butonuna bas
   - İndirilen zip içinde `.apk` dosyası olacak

4. **Telefona yükle:**
   - APK dosyasını telefonuna kopyala
   - Ayarlar → Güvenlik → Bilinmeyen Kaynaklar → İzin Ver
   - APK'ya dokun → Yükle

---

### YOL 2: Android Studio (Daha Profesyonel)

1. Android Studio kur: https://developer.android.com/studio
2. New Project → Empty Activity
3. `app/src/main/assets/` klasörüne tüm dosyaları kopyala
4. `MainActivity.java` içinde WebView kur:

```java
WebView webView = new WebView(this);
webView.getSettings().setJavaScriptEnabled(true);
webView.getSettings().setDomStorageEnabled(true); // localStorage için!
webView.loadUrl("file:///android_asset/index.html");
setContentView(webView);
```

5. Build → Generate Signed APK → İmzala → Çıkar

---

### YOL 3: Capacitor (En Profesyonel)

```bash
npm install -g @capacitor/cli @capacitor/core @capacitor/android
npx cap init "Türk Memory" "com.turkmemory.app"
npx cap add android
# index.html'i www/ klasörüne koy
npx cap sync
npx cap open android
# Android Studio'da Build → APK
```

---

## Önemli Notlar

- Oyun **tamamen offline** çalışır — internet gerekmez
- **localStorage** ile ilerleme kaydedilir — uygulama silinmediği sürece kaybolmaz
- 250 level, tüm temalar, tüm SVG motifler tek dosyada

---

## Önerilen Uygulama Bilgileri

| Alan | Değer |
|------|-------|
| Uygulama Adı | Türk Motifleri Memory |
| Kısa Ad | Türk Memory |
| Paket Adı | com.turkmemory.app |
| Versiyon | 1.0.0 |
| Min Android | 5.0 (API 21) |
| Yönelim | Portrait |
