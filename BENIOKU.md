# Göz Klavyesi – Android uygulaması

Bu klasör, göz klavyesini tam ekran, internetsiz çalışan bir Android uygulamasına çeviren projedir.
Uygulamayı bilgisayarınıza hiçbir şey kurmadan GitHub üzerinde ücretsiz derleyebilirsiniz.

## 1. APK'yı oluşturun (yaklaşık 10 dakika)

1. github.com'da ücretsiz hesap açın. Sağ üstten **New repository** seçin, bir ad verin ve **Private** işaretleyin.
2. Açılan sayfada **uploading an existing file** bağlantısına tıklayın. Bu klasörün **içindekilerin tamamını** (`.github` klasörü dahil) sürükleyip bırakın ve **Commit changes** deyin.
   Mac'te `.github` klasörü gizlidir; Finder'da Cmd+Shift+. ile görünür yapın. Yine de yüklenmezse depoda
   **Add file > Create new file** deyin, adı `.github/workflows/build.yml` yazın ve bu klasördeki aynı dosyanın içeriğini yapıştırın.
3. Üstteki **Actions** sekmesine geçin. “Uygulamayı derle” işi kendiliğinden başlar (başlamazsa seçip **Run workflow** deyin).
4. İş yeşil tik aldığında üzerine tıklayın. Sayfanın altındaki **Artifacts** bölümünden `goz-klavyesi-test-apk` dosyasını indirin, zip'i açın.

## 2. Telefona / tablete kurun

1. `app-debug.apk` dosyasını cihaza gönderin (WhatsApp'ta kendinize, e-posta, Drive, USB).
2. Dosyaya dokunun. “Bilinmeyen kaynaklara izin ver” sorulursa izin verin.
3. Uygulamayı açın, kamera iznini verin.

İpucu: Hastanın uygulamadan yanlışlıkla çıkmaması için Android **Uygulama sabitleme** (Ayarlar > Güvenlik > Uygulama sabitleme) özelliğini açın.
Türkçe ses yoksa uygulamanın Ayarlar > Konuşma bölümünde **Türkçe ses paketini kur** düğmesini kullanın.

## 3. Google Play'e yüklemek isterseniz

1. **İmza anahtarı:** Actions > “İmza anahtarı oluştur (bir kez)” > **Run workflow**, bir şifre girin.
   Çıkan `imza-anahtari-SAKLAYIN` dosyasını indirin ve güvenli bir yerde saklayın (kaybolursa uygulama güncellenemez).
2. **Gizli bilgiler:** Depoda Settings > Secrets and variables > Actions > **New repository secret** ile üçünü ekleyin:
   - `KEYSTORE_BASE64` → `KEYSTORE_BASE64.txt` dosyasının içeriği
   - `KEYSTORE_PASSWORD` → girdiğiniz şifre
   - `KEY_ALIAS` → `upload`
3. “Uygulamayı derle” işini yeniden çalıştırın. `goz-klavyesi-play-store` içinden `app-release.aab` dosyasını alın.
4. play.google.com/console adresinde geliştirici hesabı açın (tek seferlik 25 dolar), yeni uygulama oluşturun ve `.aab` dosyasını yükleyin.
   `store/` klasöründe ikon, tanıtım görseli, mağaza metni ve gizlilik politikası hazırdır.
   Gizlilik politikasını herkese açık bir adreste yayımlamanız gerekir (ör. Google Sites).

Not: Sadece kendi hastanız için kullanacaksanız Play'de **Dahili test** kanalı yeterlidir: inceleme beklemeden
en fazla 100 kişinin e-posta adresine yükleme yapılır. 2023 sonrası açılan kişisel hesaplarda herkese açık yayın için
önce 12 test kullanıcısıyla 14 günlük kapalı test şartı vardır.

Lisans: Göz takibi için kullanılan WebGazer GPLv3 lisanslıdır. Uygulamayı Play'de yayımlarsanız kaynak kodunu
(bu depoyu) herkese açık yapmanız ve GPLv3 lisansıyla paylaşmanız gerekir.

## Güncelleme

`app/src/main/assets/index.html` dosyasını değiştirip GitHub'a yükleyin; Actions yeni APK'yı otomatik üretir.
Aynı cihaza yeni sürüm kurulunca cümleler ve ayarlar korunur.
