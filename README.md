# 📋 Aplikasi Supervisi Akademik Guru Sekolah Menengah Pertama

> Aplikasi web supervisi akademik guru berbasis instrumen resmi Kemdikbud — dibangun sebagai single-file HTML, berjalan 100% di browser tanpa server.

🔗 **[Coba Langsung →](https://usernamekamu.github.io/supervisi-akademik-app)**

![Preview](https://img.shields.io/badge/Status-Active-brightgreen) ![HTML](https://img.shields.io/badge/HTML-Single%20File-orange) ![License](https://img.shields.io/badge/License-MIT-blue)

---

## 📸 Screenshot

> *(tambahkan screenshot di sini setelah deploy — klik kanan di browser → Save image → upload ke repo)*

---

## ✨ Fitur

- **4 Instrumen Penilaian** sesuai instrumen resmi PS-01/2021:
  - G1 — Administrasi Perencanaan Pembelajaran (12 aspek)
  - G2 — Penilaian Proses & Hasil Belajar (25 aspek)
  - G3 — Penyusunan RPP (16 aspek)
  - G4 — Supervisi Pelaksanaan KBM (44 aspek)
- **Kalkulasi nilai otomatis** dengan rumus `(jumlah skor / skor maks) × 100`
- **Predikat & Tindak Lanjut** otomatis berdasarkan rentang nilai
- **Dashboard & Rekap** seluruh guru binaan
- **Cetak / Export PDF** per instrumen maupun per guru
- **Export & Import JSON** untuk backup data
- **Offline-first** — tidak butuh internet setelah dibuka
- **Zero dependency** — murni HTML + CSS + JavaScript vanilla

---

## 🛠️ Teknologi

| Teknologi | Keterangan |
|---|---|
| HTML5 | Struktur dan layout |
| CSS3 | Styling, animasi, responsive |
| JavaScript (Vanilla) | Logika aplikasi, kalkulasi nilai |
| localStorage | Penyimpanan data di browser |

Tidak ada framework, tidak ada library eksternal, tidak ada backend — **satu file HTML saja**.

---

## 🚀 Cara Pakai

### Opsi 1 — Langsung di Browser
Buka link: **[https://usernamekamu.github.io/supervisi-akademik-app](https://usernamekamu.github.io/supervisi-akademik-app)**

### Opsi 2 — Download & Jalankan Lokal
```bash
# Clone repo
git clone https://github.com/usernamekamu/supervisi-akademik-app.git

# Buka file di browser
open index.html  # Mac
# atau klik dua kali file index.html di Windows
```

---

## 📖 Cara Penggunaan Aplikasi

1. **Isi Identitas Kepala Sekolah** di menu ⚙️ Pengaturan
2. **Tambah Data Guru** di menu 👥 Data Guru
3. **Isi Instrumen G1–G4** — pilih guru, centang Ada/Tidak Ada per aspek
4. **Klik "Simpan Penilaian"** — nilai dihitung otomatis
5. **Lihat Rekap** di menu 📈 Rekap Nilai
6. **Cetak laporan** PDF langsung dari browser

> 💡 **Tips:** Gunakan fitur **Export JSON** secara rutin sebagai backup, karena data tersimpan di localStorage browser.

---

## 🏗️ Arsitektur

```
index.html
├── <style>          → Semua CSS (layout, komponen, responsive)
├── <body>           → Struktur HTML (sidebar, halaman, modal)
└── <script>
    ├── DEF          → Definisi instrumen (soal, skor maks)
    ├── DB           → State aplikasi (guru, penilaian, settings)
    ├── localStorage → Persistensi data (ldDB, svDB)
    ├── Kalkulasi    → getVal, getJml, getNilai, gavg
    └── UI           → go, loadI, rguru, rdash, rrekap, ctkG
```

**Alur data:**
```
Klik Ada/Tidak → onCh() → update DB di RAM
Klik Simpan   → simpan() → svDB() → localStorage (permanen)
Buka ulang    → ldDB() → baca localStorage → tampilkan data
```

---

## 📐 Dasar Instrumen

Instrumen penilaian dalam aplikasi ini dibangun berdasarkan **Instrumen Supervisi Akademik PS-01/2021**, yang merupakan lampiran dari **Panduan Kerja Pengawas Sekolah Pendidikan Dasar dan Menengah** (Cetakan Pertama, April 2017), diterbitkan oleh Direktorat Pembinaan Tenaga Kependidikan, Direktorat Jenderal Guru dan Tenaga Kependidikan, Kementerian Pendidikan dan Kebudayaan.

| Instrumen | Nama | Aspek | Skor Maks | Sistem |
|---|---|---|---|---|
| G1 | Administrasi Perencanaan Pembelajaran | 12 | 12 | Ada = 1 / Tidak Ada = 0 |
| G2 | Penilaian Proses & Hasil Belajar | 25 | 25 | Ada = 1 / Tidak Ada = 0 |
| G3 | Penyusunan RPP | 16 | 16 | Ada = 1 / Tidak Ada = 0 |
| G4 | Supervisi Pelaksanaan KBM | 44 | 44 | Ada = 1 / Tidak Tampak = 0 |

**Rumus Nilai:** `(Jumlah Skor / Skor Maksimal) × 100`

**Predikat:**
| Rentang Nilai | Predikat |
|---|---|
| 91 – 100 | Amat Baik |
| 76 – 90 | Baik |
| 61 – 75 | Cukup |
| 0 – 60 | Kurang Baik |

---

## ⚖️ Landasan Hukum

Instrumen supervisi akademik yang digunakan dalam aplikasi ini memiliki landasan hukum berjenjang:

| No | Peraturan | Tentang |
|---|---|---|
| 1 | UU No. 20 Tahun 2003 | Sistem Pendidikan Nasional |
| 2 | UU No. 14 Tahun 2005 | Guru dan Dosen |
| 3 | PP No. 19 Tahun 2005 | Standar Nasional Pendidikan |
| 4 | Permendiknas No. 12 Tahun 2007 | Standar Kompetensi Pengawas Sekolah/Madrasah |
| 5 | PermenpanRB No. 21 Tahun 2010 | Jabatan Fungsional Pengawas Sekolah dan Angka Kreditnya |
| 6 | PermenpanRB No. 14 Tahun 2016 | Perubahan atas PermenpanRB No. 21 Tahun 2010 |
| 7 | **Panduan Kerja Pengawas Sekolah** | Direktorat GTK, Kemdikbud, Cetakan Pertama April 2017 |

> 📖 Sumber utama instrumen: **Panduan Kerja Pengawas Sekolah Pendidikan Dasar dan Menengah**, Direktorat Pembinaan Tenaga Kependidikan Pendidikan Dasar dan Menengah, Direktorat Jenderal Guru dan Tenaga Kependidikan, Kemdikbud, 2017.
> Dapat diakses di: [repositori.kemdikbud.go.id](https://repositori.kemdikbud.go.id/11282/)

---

## 🙋 Tentang Proyek Ini

Proyek ini dibuat untuk membantu kepala sekolah dalam mendokumentasikan dan menghitung hasil supervisi akademik guru binaan secara digital — menggantikan proses manual berbasis Excel.

---

## 📄 Lisensi

MIT License — bebas digunakan dan dimodifikasi.
