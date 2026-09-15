<div align="center">

# Avalon

### Tek bir Windows 10/11 x64 PC. Birden fazla bağımsız masaüstü.

Tek bir Windows 10/11 x64 bilgisayarı, her biri kendi ekranına, girişine, sesine, uygulamalarına ve uzak akış bağlantısına sahip birden fazla bağımsız masaüstü örneğine dönüştürün.

**Tek host. Birden fazla örnek.**

[English](README.md) · [简体中文](README-zh-CN.md)

</div>

---

## Avalon nedir?

Avalon, Windows 10/11 x64 için çok oturumlu masaüstü akış platformudur.

Bir PC’yi tek bir etkileşimli masaüstüyle sınırlamak yerine, aynı makinenin aynı anda birden fazla bağımsız Windows örneğini barındırmasına olanak tanır.

Her örnek kendine ait şu bileşenlere sahip olabilir:

- Windows masaüstü oturumu
- sanal ekran
- çözünürlük ve yenileme hızı
- giriş akışı
- ses akışı
- uygulamalar ve oyunlar
- Moonlight üzerinden uzak bağlantı

Böylece güçlü bir PC, her kullanıcı için tam bir sanal makine çalıştırmadan birkaç uzaktan erişilebilir bilgisayar gibi kullanılabilir.

---

## Pratikte nasıl görünür?

Bir Windows 10/11 x64 PC üzerinde üç Avalon örneği çalıştığını düşünün:

```text
                Windows 10/11 x64 Host
                       │
                ┌──────┴──────┐
                │    Avalon    │
                └──────┬──────┘
                       │
         ┌─────────────┼─────────────┐
         │             │             │
         ▼             ▼             ▼
    Instance 01    Instance 02    Instance 03
         │             │             │
         ▼             ▼             ▼
     Moonlight      Moonlight      Moonlight
        TV            Tablet         Laptop
```

Her istemci kendi Windows masaüstüne bağlanır.

Örnekler aynı masaüstünü, fare imlecini, ses çıkışını veya uygulama oturumunu paylaşmadan yan yana çalışır.

---

## Neden Avalon?

Geleneksel uzak masaüstü araçları genellikle tek bir kullanıcının tek bir masaüstünü kontrol ettiği modele göre tasarlanır.

Sanal makineler güçlü izolasyon sunar ancak ek işletim sistemleri, daha fazla bellek ve depolama kullanımı, daha karmaşık GPU yapılandırması ve daha yüksek yönetim maliyeti getirir.

Avalon farklı bir yaklaşım izler.

Windows oturumlarını, sanal ekranları, bağımsız akış süreçlerini ve merkezi yaşam döngüsü yönetimini bir araya getirerek birden fazla etkileşimli masaüstünün tek bir Windows 10/11 x64 host üzerinde birlikte çalışmasını sağlar.

Karmaşıklık Avalon’un içinde kalır. Kullanıcı açısından akış basittir:

```text
Bir örnek oluştur
        ↓
Ekran ve eşleştirmeyi yapılandır
        ↓
Moonlight'ı aç
        ↓
Bağlan
```

---

## Temel yetenekler

### Birden fazla bağımsız örnek

Aynı host üzerinde aynı anda birden fazla Windows masaüstü oturumu çalıştırın.

Her örnek kendi etkileşimli masaüstü ortamı gibi davranır.

### Bağımsız akış

Her örneğin kendi akış bağlamı vardır ve Moonlight istemcisi ile bağımsız olarak bağlanılabilir.

Bir TV bir örneğe bağlıyken, bir tablet veya başka bir bilgisayar aynı anda başka bir örneğe bağlanabilir.

### Bağımsız ekran

Her örnek çözünürlük ve yenileme hızı dahil kendi sanal ekran yapılandırmasını kullanabilir.

Avalon ekran ortamını yönetir; her örnek için fiziksel monitör gerekmez.

### Bağımsız giriş

Klavye ve fare girişleri tüm örnekler arasında paylaşılmak yerine hedef Windows oturumuna yönlendirilir.

Giriş katmanı geliştikçe Avalon, örnek başına daha eksiksiz cihaz izolasyonuna doğru ilerleyecek şekilde tasarlanmıştır.

### Bağımsız ses

Her örnek kendi Windows oturumu ses yolunu kullanır; böylece farklı kullanıcılar farklı uygulama veya oyun seslerini örnekler arasında basitçe karıştırmadan dinleyebilir.

### Oturum yaşam döngüsü yönetimi

Avalon oturumları kendisi oluşturur ve sürdürür.

Bir örneği canlı tutmak için harici bir RDP istemcisini sürekli bağlı tutmak gerekmez.

### Web yönetimi

Tüm örnekler tek bir Web arayüzünden yönetilir.

Tipik işlemler:

- örnek oluşturma ve silme
- örnek başlatma ve durdurma
- çözünürlük ve yenileme hızı yapılandırma
- Moonlight istemcilerini eşleştirme
- bağlantı durumunu kontrol etme
- tanılama bilgilerini görüntüleme
- host düzeyi ayarları yönetme

Günlük kullanım için komut satırı gerekmez.

---

## Moonlight için tasarlandı

Avalon, alışık olduğunuz Moonlight akış deneyimini korur.

Moonlight’ı şu cihazlarda kullanmaya devam edebilirsiniz:

- Windows
- Linux
- macOS
- Android
- iOS / iPadOS
- Android TV
- Moonlight destekli Smart TV ve akış cihazları

Avalon host tarafındaki organizasyonu değiştirir; tamamen yeni bir akış istemcisi öğrenmenizi gerektirmez.

---

## Kullanım senaryoları

### Evde oyun

Tek bir oyun PC’sini aynı evdeki farklı kişiler için birden fazla bağımsız oyun ortamına dönüştürün.

Bir kişi salondaki TV’de oynarken başka biri el konsolu veya dizüstü bilgisayardan farklı bir örneğe bağlanabilir.

### Çoklu hesap ve çoklu örnek

Aynı makinede farklı uygulama, hesap veya oyun oturumlarını ayrı Windows ortamlarında çalıştırın.

### Uzak iş istasyonu

Güçlü bir masaüstü bilgisayarı bağımsız erişilebilen birden fazla uzak çalışma alanı olarak kullanın.

### Test ve geliştirme

Yazılım testi, otomasyon, uyumluluk doğrulama veya izole kullanıcı ortamları için birden fazla Windows oturumu tutun.

### Homelab ve self-hosting

Yüksek performanslı bir Windows makinesini merkezi yönetilen çok kullanıcılı uzak bilgi işlem hostu olarak kullanın.

---

## Avalon nasıl çalışır?

Avalon içeride sistemin birkaç katmanını koordine eder:

```text
Web Management
      │
      ▼
Avalon Control Service
      │
      ▼
Windows Sessions
Virtual Displays
Streaming Processes
Input / Audio Routing
      │
      ▼
Moonlight Clients
```

Normal kullanıcıların bu uygulama ayrıntılarını bilmesi gerekmez.

Bir örnek oluşturursunuz; Avalon oturumu, ekranı, akış ortamını ve yaşam döngüsünü hazırlar; ardından bağlanırsınız.

---

## İzolasyon modeli

Avalon **Windows oturumu düzeyinde izolasyon** sağlar.

Her örneğin kendine ait Windows oturumu, masaüstü, uygulamaları, ekranı, giriş yolu ve ses yolu vardır.

Ancak Avalon örnekleri **tam sanal makineler değildir**.

Şunları paylaşmaya devam ederler:

- aynı Windows host kurulumu
- aynı çekirdek
- aynı fiziksel CPU
- aynı fiziksel GPU
- hostun aynı donanım kaynakları

Bu nedenle Avalon, VM düzeyinde bir güvenlik sınırı olarak değerlendirilmemelidir.

Amaç tam donanım sanallaştırması değil, verimli çok kullanıcılı ve çok masaüstülü akıştır.

---

## Mevcut durum

Avalon şu anda **Alpha** aşamasındadır.

Mimari, yönetim arayüzü, uyumluluk katmanı ve cihaz yığını gelişmeye devam etmektedir.

Bu aşamada şunlar görülebilir:

- uyumsuzluk yaratabilecek değişiklikler
- eksik donanım uyumluluğu
- arayüz değişiklikleri
- sürücü ve oturumla ilgili uç durumlar
- kararlı sürümden önce davranışı değişebilecek özellikler

Avalon henüz kritik üretim altyapısı olarak kullanılmak üzere tasarlanmamıştır.

Testler, günlükler, yeniden üretilebilir hata raporları ve gerçek kullanım geri bildirimleri bu aşamada özellikle değerlidir.

---

## Platform

Mevcut hedef:

```text
Windows 10 x64 / Windows 11 x64
```

Avalon özellikle Windows masaüstü, oturum ve grafik modeline göre tasarlanmıştır.

Diğer host işletim sistemleri şu anda projenin ana hedeflerinden biri değildir.

---

## Performans

Gerçek akış performansı birçok etkene bağlıdır:

- GPU
- kodlayıcı desteği
- grafik sürücüsü
- çözünürlük
- yenileme hızı
- codec
- ağ kalitesi
- istemci kod çözme kapasitesi
- aynı anda çalışan örnek sayısı

Avalon her sistemde belirli bir çözünürlük, yenileme hızı, HDR modu veya sabit sayıda eşzamanlı örnek garanti etmez.

Test kapsamı genişledikçe uyumluluk belgeleri de ayrıntılandırılacaktır.

---

## Proje felsefesi

Avalon basit bir fikir etrafında şekillenir:

> Güçlü bir PC sürekli olarak tek bir ekran, tek bir masaüstü ve tek bir kullanıcıyla sınırlı olmak zorunda değildir.

Host tek bir makine olabilir. Üzerinde çalışan deneyimlerin tek olması gerekmez.

---

## Geliştirme

Bu README, Avalon için kararlı ürün tanıtımı olarak tutulur.

Gerçek zamanlı geliştirme durumu ve proje mesajları için [devlog.md](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) dosyasına bakın.

Hata bildirimleri, sorular ve özellik talepleri için [GitHub Issues](https://github.com/AvalonStream/AvalonStream/issues) kullanın.

---

<div align="center">

### Avalon

**Tek host. Birden fazla örnek.**

</div>
