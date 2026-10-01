# LemauGo.id

> **"LemauGo.id — Batik Asli, Pasar Lebih Luas, Untung Lebih Terukur."**

Prototipe web high-fidelity ekosistem digital untuk UMKM pengrajin **Batik Sungai Lemau**, Kabupaten Bengkulu Tengah. Dibangun sebagai **prototipe akademik** untuk kebutuhan lomba esai dan perancangan inovasi — bukan produk komersial yang sudah berjalan.

---

## Konsep Platform

LemauGo.id bukan sekadar marketplace. Platform ini memadukan:

1. **Etalase digital kolektif** berbasis kurasi Indikasi Geografis (IG).
2. **Katalog pengrajin terverifikasi** — halaman tersendiri yang mempertemukan konsumen dengan pengrajin.
3. **Profil pengrajin individual** — konsumen mengenal pengrajin di balik setiap karya.
4. **Kalkulator harga jual** yang benar-benar berfungsi di front-end.
5. **Pembukuan multikanal** — tunai, QRIS, dan marketplace dalam satu catatan.
6. **Ringkasan laba sederhana**: Uang Masuk, Uang Keluar, Sisa Keuntungan.
7. **Riwayat transaksi usaha** sebagai dokumen pendukung pembiayaan formal.
8. **Identitas kolektif** Batik Sungai Lemau.
9. **Modul belajar** pemasaran digital — tersedia di dashboard pengrajin.
10. **Login dua jenis pengguna** — Pengrajin (PIN) dan Konsumen (email/kata sandi).

## Cara Menjalankan

Prototipe ini berupa situs statis — **tanpa proses build dan tanpa backend**.

**Cara 1 (paling mudah):** buka `index.html` langsung di browser (klik dua kali).

**Cara 2 (disarankan, agar semua fitur URL berfungsi mulus):**

```bash
cd sungailemau-godigital
python -m http.server 8000
# lalu buka http://localhost:8000
```

Tidak ada dependensi yang perlu diinstal. Semua font dimuat dari Google Fonts (butuh koneksi internet untuk tipografi optimal; tanpa internet, situs tetap berfungsi dengan font fallback).

## Struktur Proyek

```
sungailemau-godigital/
├─ index.html                  ← Beranda publik
├─ jelajahi.html               ← Jelajahi Produk — katalog + filter/sort/pencarian
├─ produk.html?id=b001         ← Detail produk (galeri, verifikasi, QRIS demo)
├─ pengrajin.html              ← Katalog pengrajin (mode daftar bila tanpa ?id)
├─ pengrajin.html?id=p1        ← Profil pengrajin (mode detail dengan ?id)
├─ tentang.html                ← Sejarah Batik Sungai Lemau (6 bagian editorial)
├─ verifikasi-produk.html      ← Cara verifikasi produk
├─ masuk.html                  ← Masuk — dua tab: Pengrajin (PIN) & Konsumen
├─ edukasi.html                ← [Tidak tampil di navigasi publik — akses via dashboard]
├─ dashboard/
│  ├─ index.html               ← Ringkasan (6 kartu + 2 visualisasi)
│  ├─ produk.html              ← Produk Saya
│  ├─ tambah-produk.html       ← Tambah Produk (validasi + alur kurasi)
│  ├─ pesanan.html             ← Pesanan (8 pesanan simulasi)
│  ├─ pembukuan.html           ← Pembukuan Multikanal (berfungsi, localStorage)
│  ├─ kalkulator.html          ← Kalkulator Harga Jual (berfungsi penuh)
│  ├─ belajar.html             ← Modul Belajar (6 modul, progres tersimpan)
│  ├─ profil.html              ← Profil Usaha (tanpa kanal penjualan di form)
│  ├─ verifikasi.html          ← Status Verifikasi (alur 4 tahap)
│  └─ pengaturan.html          ← Pengaturan
└─ assets/
   ├─ css/
   │  ├─ tokens.css            ← DESIGN TOKENS (warna, tipografi, radius, spasi)
   │  ├─ base.css              ← Komponen dasar (tombol, badge, form, tabel, modal)
   │  ├─ public.css            ← Gaya area publik
   │  └─ dashboard.css         ← Gaya area pengrajin
   ├─ js/
   │  ├─ data.js               ← SEMUA DATA DUMMY (edit di sini)
   │  ├─ app.js                ← Komponen bersama (header, footer, kartu, ikon, logo)
   │  ├─ store.js              ← Penyimpanan lokal (localStorage)
   │  └─ dashboard.js          ← Kerangka dashboard + grafik SVG
   └─ img/                     ← Foto placeholder (ganti dengan foto asli, nama sama)
```

## Perubahan Navigasi (v2 — LemauGo.id)

| Perubahan | Sebelum | Sesudah |
|---|---|---|
| Nama platform | SungaiLemauGoDigital | **LemauGo.id** |
| Menu Pengrajin | Scroll ke `#pengrajin` di Beranda | Halaman katalog `pengrajin.html` |
| Menu Jelajahi | "Jelajahi Batik" | **"Jelajahi Produk"** |
| Menu Edukasi | Tampil di navigasi publik | Dihapus dari navigasi publik |
| Tombol Masuk | "Masuk Pengrajin" | **"Masuk"** (dua tab: Pengrajin & Konsumen) |
| Halaman Tentang | Tujuan platform & pilot | **Sejarah Batik Sungai Lemau** |
| Beranda | Memuat section "Tiga Kesenjangan" | Dihapus, layout lebih bersih |
| Profil Usaha (dashboard) | Ada field "Kanal Penjualan Aktif" | Dihapus dari form profil |

## File Utama yang Bisa Diedit

| Kebutuhan | File |
|---|---|
| Ganti nama pengrajin, produk, harga, transaksi, pesanan, modul | `assets/js/data.js` |
| Ganti warna, font, radius | `assets/css/tokens.css` |
| Ganti foto | `assets/img/` — timpa berkas dengan nama sama |
| Ubah teks beranda | `index.html` |
| Ubah sejarah Batik Sungai Lemau | `tentang.html` |

## Data Dummy

Seluruh data adalah **simulasi** dengan nama fiktif: 6 pengrajin, 16 produk, 20 transaksi, 8 pesanan, 6 modul belajar, dan 6 bulan data grafik — semuanya di `assets/js/data.js`. Nama motif (Gunung Bungkuk, Sungai Mengalir, Rafflesia, Liku Sembilan, dst.) adalah **contoh ilustratif**, bukan klaim data resmi.

Transaksi baru dari form pembukuan serta progres modul belajar disimpan di **localStorage** browser (kunci `slgd-demo-v1`) — hapus data situs untuk mengatur ulang demo.

## Catatan Etika & Legal

- Prototipe pengembangan untuk **kebutuhan akademik dan perancangan inovasi**.
- Nama lembaga (MPIG, Dekranasda, KPw Bank Indonesia Provinsi Bengkulu, perguruan tinggi, GenBI) ditampilkan sebagai **"mitra pendukung yang diusulkan" / "rancangan kolaborasi"** — belum merupakan kerja sama resmi.
- Fitur QRIS, marketplace, dan ekspor laporan bersifat **demonstrasi**, bukan transaksi riil.
- Autentikasi login bersifat **simulasi** dan belum terhubung ke sistem backend.
- Jangan menggunakan nama "Batik Sungai Lemau" di luar konteks budaya dan asal geografis yang sah.

## Catatan Teknologi

Versi prototipe ini dibangun sebagai **situs statis (HTML + CSS + JavaScript murni, tanpa framework)** agar dapat dibuka langsung tanpa instalasi apa pun. Arsitekturnya modular:

- `assets/js/data.js` → data produk, pengrajin, transaksi, modul
- `app.js` / `dashboard.js` → komponen bersama: header, footer, kartu, grafik
- `store.js` → localStorage (pembukuan & progres belajar)
- `tokens.css` → design tokens (warna, tipografi, spasi)

## Rekomendasi Screenshot untuk Esai

1. **Gambar 1 (utama):** `index.html` desktop lebar 1360–1440px
2. `dashboard/index.html` — bukti fitur pembukuan & ringkasan laba
3. `dashboard/kalkulator.html` — bukti kalkulator harga berfungsi
4. `jelajahi.html` — etalase kolektif terkurasi
5. `pengrajin.html` — katalog pengrajin terverifikasi
6. `tentang.html` — halaman Sejarah Batik Sungai Lemau
