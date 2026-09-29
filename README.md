# ⚡ Tokopedia Review Auto-Reply

Chrome Extension (Manifest V3) untuk mempercepat pekerjaan seller membalas
ulasan pembeli di **Tokopedia Seller Center**. Dari yang biasanya scroll,
cari tombol, ketik ulang template berkali-kali, cukup 2 klik per ulasan
(atau 0 klik di mode otomatis penuh).

## ✨ Fitur

- 🔍 **Deteksi otomatis** tombol BALAS pada ulasan yang belum dibalas
- 📜 **Auto-scroll** ke ulasan berikutnya, termasuk saat daftar dimuat bertahap
- ✍️ **Isi template otomatis** ke kolom balasan (kompatibel dengan input gaya React)
- 🎯 **Sorotan visual** (kuning berkedip) pada tombol BALAS/KIRIM berikutnya
- 🤖 **Dua mode:**
  - *Semi-otomatis* — Anda klik KIRIM sendiri (paling aman)
  - *Otomatis penuh* — script mengklik BALAS & KIRIM
- 🔢 **Batas balasan per sesi** untuk mengontrol jumlah balasan
- 🧪 **Tombol TEST** untuk mencoba satu ulasan sebelum menjalankan massal
- 🪟 **Panel kontrol** yang bisa digeser & diperkecil, posisi dan pengaturan
  tersimpan otomatis
- 📊 **Statistik & log real-time** (diproses / berhasil / gagal) + info debug
- 🖼️ Mendukung halaman dengan **iframe same-origin**

## 🛠️ Teknologi

JavaScript (Vanilla) · Chrome Extension Manifest V3 · Content Scripts ·
DOM API · MutationObserver · CSS

## 📦 Instalasi

1. Clone / download repo ini:
```bash
   git clone https://github.com/USERNAME/tokopedia-review-autoreply.git
```
2. Buka `chrome://extensions`
3. Aktifkan **Developer mode** (pojok kanan atas)
4. Klik **Load unpacked**, lalu pilih folder repo ini
5. Buka halaman **Ulasan/Rating** di Tokopedia Seller Center (refresh jika perlu)

## 🚀 Cara Pakai

1. Panel kontrol muncul di kanan bawah halaman.
2. Ubah **Pesan balasan** sesuai kebutuhan.
3. Isi **Maks. balasan per sesi**.
4. (Opsional) Centang **Klik BALAS & KIRIM otomatis** untuk mode penuh.
5. Klik **TEST** untuk mencoba satu ulasan.
6. Jika lancar, klik **JALANKAN**. Klik **STOP** kapan saja untuk berhenti.

> Di mode semi-otomatis, klik tombol KIRIM yang disorot kuning. Script lalu
> otomatis pindah ke ulasan berikutnya.

## 🧩 Cara Kerja Singkat

1. Content script disuntikkan ke halaman Seller Center.
2. Script memindai DOM (termasuk iframe same-origin) untuk mencari tombol
   BALAS yang terlihat dan berukuran wajar (filter ukuran mencegah salah
   mendeteksi elemen pembungkus).
3. Teks template diisi lewat native value setter + event `input`/`change`
   agar terbaca framework front-end.
4. Tombol KIRIM disorot (atau diklik otomatis), lalu loop berlanjut sampai
   target tercapai atau daftar habis.

## 📁 Struktur Proyek
├── manifest.json # Konfigurasi extension (MV3)
├── content.js # Logika utama & panel kontrol
├── styles.css # Styling panel & efek highlight
└── README.md

## ⚠️ Catatan & Batasan

- Tokopedia dapat mengabaikan klik buatan script (bukan klik asli). Jika mode
  otomatis penuh tidak bereaksi, matikan centangnya dan gunakan mode semi.
- Jika ulasan dimuat lewat iframe cross-origin, browser tidak mengizinkan
  akses; balasan harus dilakukan manual.
- Struktur halaman Tokopedia bisa berubah sewaktu-waktu sehingga deteksi
  tombol mungkin perlu disesuaikan.
- Jangan menutup tab selama sesi berjalan.

## 📜 Disclaimer

Proyek ini dibuat untuk tujuan edukasi dan portofolio. Ini **bukan** produk
resmi Tokopedia dan tidak berafiliasi dengannya. Gunakan dengan bijak,
patuhi Syarat & Ketentuan platform, dan hindari balasan yang spammy.
Penggunaan menjadi tanggung jawab pengguna.

## 📄 Lisensi

MIT License
