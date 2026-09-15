# Avalon

### Tek bir Windows 10/11 x64 PC. Birden çok bağımsız masaüstü.

Avalon, tek bir Windows 10/11 x64 ana bilgisayarı bağımsız olarak erişilebilen birden çok masaüstü örneğine dönüştürür. Her örnek kendi Windows oturumuna, sanal ekranına, girişine, sesine, uygulamalarına, oyunlarına ve Moonlight bağlantısına sahip olabilir.

**Tek ana bilgisayar. Birden çok örnek.**

[English](README.md)

[Geliştirme günlüğü ve geri bildirim](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / hata ve özellik istekleri](https://github.com/AvalonStream/AvalonStream/issues)

---

## Avalon nedir?

Avalon, Windows 10/11 x64 için çok oturumlu bir masaüstü yayın platformudur. Tüm bilgisayarı tek bir etkileşimli masaüstüne ayırmak yerine, her kullanıcı için tam bir sanal makine gerektirmeden aynı ana bilgisayarda birden çok bağımsız Windows örneği çalıştırır.

---

## Temel yetenekler

- Tek ana bilgisayarda birden çok bağımsız Windows örneği
- Her örnek için ayrı yayın bağlamı
- Örnek başına sanal ekran, çözünürlük ve yenileme hızı
- Bağımsız klavye, fare ve oturum sesi yolları
- Avalon, harici RDP istemcisini açık tutmadan oturum yaşam döngüsünü sürdürür
- Web üzerinden oluşturma, eşleştirme, durum ve tanılama
- Telefon, tablet, TV ve PC tarafında Moonlight kullanılmaya devam eder

---

## Nasıl çalışır?

Bir örnek oluşturun, ekran ayarlarını seçin ve istemciyi eşleştirin. Avalon Windows oturumunu, sanal ekranı, yayın bağlamını ve yaşam döngüsünü hazırlar; ardından Moonlight ile bağlanırsınız.

```text
Windows 10/11 x64 Host
        │
      Avalon
        │
 ┌──────┼──────┐
 ▼      ▼      ▼
Instance 01  Instance 02  Instance 03
 │      │      │
 ▼      ▼      ▼
Moonlight  Moonlight  Moonlight
```

---

## Moonlight için tasarlandı

Avalon bildiğiniz istemciyi değiştirmek yerine ana bilgisayar tarafını düzenler. Moonlight Windows, Linux, macOS, Android, iOS/iPadOS, Android TV ve desteklenen diğer cihazlarda kullanılmaya devam eder.

---

## Tipik kullanım alanları

- Evde oyun: farklı kişiler aynı anda farklı örnekleri kullanır
- Çoklu hesap ve çoklu örnek iş yükleri
- Tek güçlü PC üzerinde birden çok uzak iş istasyonu
- Test, otomasyon ve uyumluluk ortamları
- Homelab ve kendi barındırdığınız uzak bilgi işlem

---

## Yalıtım modeli

Avalon tam sanal makine yalıtımı değil, Windows oturum düzeyinde yalıtım sağlar. Masaüstü, uygulamalar, ekran, giriş ve ses yolları ayrıdır; ancak ana Windows sistemi, çekirdek, CPU, GPU ve fiziksel donanım ortaktır. VM düzeyinde bir güvenlik sınırı olarak değerlendirilmemelidir.

---

## Platform ve performans

Avalon 64 bit Windows 10 ve Windows 11’i hedefler. Çözünürlük, yenileme hızı, codec, HDR ve eşzamanlı örnek sayısı GPU, sürücüler, kodlayıcı, ağ ve istemci donanımına bağlıdır.

---

## Proje durumu

Avalon şu anda Alpha aşamasındadır. Arayüz, uyumluluk ve düşük seviyeli bileşenler gelişmeye devam ettiği için uyumsuz değişiklikler ve donanıma özgü uç durumlar görülebilir.

---

## Geliştirme ve geri bildirim

Bu README ürünün kararlı tanıtımıdır. Anlık geliştirme bilgileri ve mesaj yönergeleri ayrı geliştirme günlüğünde tutulur.

- [Geliştirme günlüğü ve geri bildirim](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / hata ve özellik istekleri](https://github.com/AvalonStream/AvalonStream/issues)

**Tek ana bilgisayar. Birden çok örnek.**
