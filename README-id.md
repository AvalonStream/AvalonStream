# Avalon

### Satu PC Windows 10/11 x64. Banyak desktop yang independen.

Avalon mengubah satu host Windows 10/11 x64 menjadi beberapa instance desktop yang dapat diakses secara independen. Setiap instance dapat memiliki sesi Windows, display virtual, input, audio, aplikasi, game, dan koneksi Moonlight sendiri.

**Satu host. Banyak instance.**

[English](README.md)

[Log pengembangan dan masukan](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / bug dan permintaan fitur](https://github.com/AvalonStream/AvalonStream/issues)

---

## Apa itu Avalon?

Avalon adalah platform streaming desktop multi-sesi untuk Windows 10/11 x64. Alih-alih mendedikasikan seluruh PC untuk satu desktop interaktif, Avalon memungkinkan beberapa instance Windows independen berjalan berdampingan pada host yang sama tanpa membutuhkan mesin virtual penuh untuk setiap pengguna.

---

## Kemampuan utama

- Beberapa instance Windows independen pada satu host
- Konteks streaming khusus untuk setiap instance
- Display virtual, resolusi, dan refresh rate per instance
- Jalur keyboard, mouse, dan audio sesi yang independen
- Avalon mempertahankan lifecycle sesi tanpa harus menjaga klien RDP eksternal tetap terhubung
- Pembuatan, pairing, status, dan diagnosis melalui Web
- Moonlight tetap menjadi klien di ponsel, tablet, TV, dan PC

---

## Cara kerja

Buat instance, pilih pengaturan display, lalu pair klien. Avalon menyiapkan sesi Windows, display virtual, konteks streaming, dan lifecycle; setelah itu hubungkan melalui Moonlight.

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

## Dirancang untuk Moonlight

Avalon mengubah sisi host, bukan mengganti klien yang sudah Anda kenal. Moonlight tetap dapat digunakan di Windows, Linux, macOS, Android, iOS/iPadOS, Android TV, dan perangkat lain yang didukung.

---

## Skenario penggunaan

- Gaming di rumah: orang berbeda menggunakan instance berbeda secara bersamaan
- Banyak akun dan workload multi-instance
- Beberapa workstation jarak jauh pada satu PC bertenaga tinggi
- Pengujian, otomatisasi, dan lingkungan kompatibilitas
- Homelab dan remote computing yang di-host sendiri

---

## Model isolasi

Avalon menyediakan isolasi tingkat sesi Windows, bukan isolasi mesin virtual penuh. Desktop, aplikasi, display, input, dan audio dipisahkan per instance, tetapi Windows host, kernel, CPU, GPU, dan hardware fisik tetap digunakan bersama. Avalon bukan batas keamanan setara VM.

---

## Platform dan performa

Avalon menargetkan Windows 10 dan Windows 11 64-bit. Resolusi, refresh rate, codec, HDR, dan jumlah instance simultan bergantung pada GPU, driver, encoder, jaringan, dan hardware klien.

---

## Status proyek

Avalon saat ini berada pada tahap Alpha. Antarmuka, kompatibilitas, dan komponen tingkat rendah masih berkembang, sehingga perubahan yang tidak kompatibel dan kasus khusus hardware masih mungkin terjadi.

---

## Pengembangan dan masukan

README ini adalah pengantar produk yang stabil. Pembaruan pengembangan real-time dan panduan pesan dipelihara secara terpisah dalam log pengembangan.

- [Log pengembangan dan masukan](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / bug dan permintaan fitur](https://github.com/AvalonStream/AvalonStream/issues)

**Satu host. Banyak instance.**
