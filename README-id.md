<div align="center">

# Avalon

### Satu PC Windows 10/11 x64. Banyak desktop independen.

Ubah satu mesin Windows 10/11 x64 menjadi beberapa instance desktop yang dapat diakses secara independen, masing-masing dengan tampilan, input, audio, aplikasi, dan koneksi streaming jarak jauh sendiri.

**Satu host. Banyak instance.**

[English](README.md) · [简体中文](README-zh-CN.md)

</div>

---

## Apa itu Avalon?

Avalon adalah platform streaming desktop multi-sesi untuk Windows 10/11 x64.

Alih-alih membatasi satu PC hanya pada satu desktop interaktif, Avalon memungkinkan mesin yang sama menjalankan beberapa instance Windows independen secara bersamaan.

Setiap instance dapat memiliki komponen sendiri:

- sesi desktop Windows
- display virtual
- resolusi dan refresh rate
- aliran input
- aliran audio
- aplikasi dan game
- koneksi jarak jauh melalui Moonlight

Dengan demikian, satu PC yang kuat dapat berfungsi lebih seperti beberapa komputer yang dapat diakses dari jarak jauh, tanpa harus menjalankan mesin virtual penuh untuk setiap pengguna.

---

## Seperti apa bentuknya?

Bayangkan satu PC Windows 10/11 x64 menjalankan tiga instance Avalon:

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

Setiap klien terhubung ke desktop Windows miliknya sendiri.

Instance berjalan berdampingan tanpa berbagi desktop, kursor mouse, keluaran audio, atau sesi aplikasi yang sama.

---

## Mengapa Avalon?

Alat remote desktop tradisional biasanya dirancang untuk satu pengguna yang mengendalikan satu desktop.

Mesin virtual memberikan isolasi yang kuat, tetapi juga menambah sistem operasi tambahan, penggunaan memori, kebutuhan penyimpanan, kompleksitas GPU, dan biaya administrasi.

Avalon menggunakan pendekatan yang berbeda.

Avalon menggabungkan sesi Windows, display virtual, proses streaming independen, dan manajemen siklus hidup terpusat agar beberapa desktop interaktif dapat hidup berdampingan pada satu host Windows 10/11 x64.

Kompleksitas tetap berada di dalam Avalon. Bagi pengguna, alurnya sederhana:

```text
Buat instance
        ↓
Atur display dan pairing
        ↓
Buka Moonlight
        ↓
Hubungkan
```

---

## Kemampuan utama

### Banyak instance independen

Jalankan beberapa sesi desktop Windows secara bersamaan pada host yang sama.

Setiap instance bertindak sebagai lingkungan desktop interaktif tersendiri.

### Streaming independen

Setiap instance memiliki konteks streaming sendiri dan dapat dihubungkan secara terpisah menggunakan klien Moonlight.

TV dapat terhubung ke satu instance sementara tablet atau komputer lain terhubung ke instance berbeda pada saat yang sama.

### Display independen

Setiap instance dapat menggunakan konfigurasi display virtual sendiri, termasuk resolusi dan refresh rate.

Avalon mengelola lingkungan display tanpa memerlukan monitor fisik untuk setiap instance.

### Input independen

Input keyboard dan mouse diarahkan ke sesi Windows yang dituju, bukan dibagikan ke semua instance.

Seiring perkembangan stack input, Avalon dirancang menuju isolasi perangkat per-instance yang semakin lengkap.

### Audio independen

Setiap instance menggunakan jalur audio sesi Windows miliknya sendiri, sehingga pengguna yang berbeda dapat mendengarkan aplikasi atau game yang berbeda tanpa audio tercampur begitu saja antar-instance.

### Manajemen siklus hidup sesi

Avalon membuat dan mempertahankan sesi secara mandiri.

Klien RDP eksternal tidak perlu tetap terhubung hanya agar sebuah instance tetap hidup.

### Manajemen melalui Web

Semua instance dikelola melalui satu antarmuka Web.

Operasi umum mencakup:

- membuat dan menghapus instance
- memulai dan menghentikan instance
- mengatur resolusi dan refresh rate
- memasangkan klien Moonlight
- memeriksa status koneksi
- melihat informasi diagnostik
- mengelola pengaturan tingkat host

Penggunaan sehari-hari tidak memerlukan command line.

---

## Dirancang untuk Moonlight

Avalon mempertahankan pengalaman streaming Moonlight yang sudah familier.

Anda dapat terus menggunakan Moonlight pada perangkat seperti:

- Windows
- Linux
- macOS
- Android
- iOS / iPadOS
- Android TV
- Smart TV dan perangkat streaming yang didukung Moonlight

Avalon mengubah cara host diorganisasi, bukan memaksa pengguna mempelajari klien streaming yang sepenuhnya baru.

---

## Skenario penggunaan

### Gaming di rumah

Ubah satu PC gaming menjadi beberapa lingkungan game independen untuk orang yang berbeda dalam satu rumah.

Satu orang dapat bermain di TV ruang keluarga sementara orang lain terhubung ke instance lain dari handheld atau laptop.

### Banyak akun dan banyak instance

Jalankan aplikasi, akun, atau sesi game yang berbeda dalam lingkungan Windows terpisah pada mesin yang sama.

### Workstation jarak jauh

Gunakan satu desktop bertenaga sebagai beberapa ruang kerja jarak jauh yang dapat diakses secara independen.

### Pengujian dan pengembangan

Pertahankan beberapa sesi Windows untuk pengujian software, otomatisasi, pemeriksaan kompatibilitas, atau lingkungan pengguna yang terisolasi.

### Homelab dan self-hosting

Gunakan mesin Windows berperforma tinggi sebagai host komputasi jarak jauh multi-pengguna yang dikelola secara terpusat.

---

## Cara kerja Avalon

Avalon mengoordinasikan beberapa lapisan sistem secara internal:

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

Pengguna biasa tidak perlu memahami detail implementasi ini.

Anda membuat sebuah instance; Avalon menyiapkan sesi, display, lingkungan streaming, dan siklus hidup; setelah itu Anda tinggal terhubung.

---

## Model isolasi

Avalon menyediakan **isolasi pada tingkat sesi Windows**.

Setiap instance memiliki sesi Windows, desktop, aplikasi, display, jalur input, dan jalur audio sendiri.

Namun, instance Avalon **bukan mesin virtual penuh**.

Mereka tetap berbagi:

- instalasi Windows host yang sama
- kernel yang sama
- CPU fisik yang sama
- GPU fisik yang sama
- sumber daya perangkat keras host yang sama

Karena itu Avalon tidak boleh dianggap sebagai batas keamanan setara VM.

Tujuannya adalah streaming multi-pengguna dan multi-desktop yang efisien, bukan virtualisasi perangkat keras penuh.

---

## Status saat ini

Avalon saat ini berada pada tahap **Alpha**.

Arsitektur, antarmuka manajemen, lapisan kompatibilitas, dan stack perangkat masih terus berkembang.

Pada tahap ini, hal-hal berikut dapat terjadi:

- perubahan yang tidak kompatibel
- kompatibilitas perangkat keras yang belum lengkap
- perubahan UI
- kasus tepi terkait driver dan sesi
- perilaku fitur yang masih dapat berubah sebelum rilis stabil

Avalon belum ditujukan sebagai infrastruktur produksi yang kritis.

Pengujian, log, laporan bug yang dapat direproduksi, dan umpan balik penggunaan nyata sangat berharga pada tahap ini.

---

## Platform

Target saat ini:

```text
Windows 10 x64 / Windows 11 x64
```

Avalon dirancang secara khusus di sekitar model desktop, sesi, dan grafis Windows.

Dukungan untuk sistem operasi host lain saat ini bukan tujuan utama proyek.

---

## Performa

Performa streaming sebenarnya bergantung pada banyak faktor, termasuk:

- GPU
- dukungan encoder
- driver grafis
- resolusi
- refresh rate
- codec
- kualitas jaringan
- kemampuan decoding klien
- jumlah instance yang berjalan bersamaan

Avalon tidak menjamin resolusi tertentu, refresh rate tertentu, mode HDR, atau jumlah instance simultan yang tetap pada setiap sistem.

Dokumentasi kompatibilitas akan semakin rinci seiring perluasan cakupan pengujian.

---

## Filosofi proyek

Avalon dibangun dari gagasan sederhana:

> PC yang kuat tidak seharusnya selalu dibatasi pada satu layar, satu desktop, dan satu pengguna.

Host-nya mungkin hanya satu mesin. Pengalaman yang berjalan di atasnya tidak harus hanya satu.

---

## Pengembangan

README ini dipertahankan sebagai pengantar produk Avalon yang stabil.

Untuk perkembangan real-time dan pesan proyek, lihat [devlog.md](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md).

Untuk laporan bug, pertanyaan, dan permintaan fitur, gunakan [GitHub Issues](https://github.com/AvalonStream/AvalonStream/issues).

---

<div align="center">

### Avalon

**Satu host. Banyak instance.**

</div>
