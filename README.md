# 📚 Sistem Basis Data Perpustakaan & Analisis Peminjaman (SQLite & Python)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/[username-github]/[nama-repository]/blob/main/Tugas_BasisData_SQLite_411222050_MercyAngelia.ipynb)
![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![SQLite](https://img.shields.io/badge/SQLite-3-003B57.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458.svg)

Repository ini berisi implementasi sistem basis data relasional perpustakaan menggunakan **SQLite3** di lingkungan **Google Colab**, dilengkapi dengan eksplorasi data menggunakan **Pandas** serta visualisasi transaksi peminjaman menggunakan **Matplotlib** dan **Seaborn**.

---

## 👤 Identitas Mahasiswa
* **Nama:** Mercy Angelia
* **NIM:** 411222050
* **Program Studi:** Teknik Informatika (Semester 6)
* **Institusi:** Universitas Dian Nusantara

---

## 🗂️ Struktur Basis Data (Skema Relasional)

Basis data (`perpustakaan_undira.db`) dirancang dengan tiga tabel utama yang terhubung melalui relasi *Primary Key* dan *Foreign Key*:

1. **`buku`**
   * `id` (`INTEGER`, Primary Key, Autoincrement)
   * `judul` (`TEXT`, Not Null)
   * `penulis` (`TEXT`, Not Null)
   * `tahun` (`INTEGER`, Not Null)
2. **`anggota`**
   * `id` (`INTEGER`, Primary Key, Autoincrement)
   * `nama` (`TEXT`, Not Null)
   * `email` (`TEXT`, Unique, Not Null)
3. **`peminjaman`**
   * `id` (`INTEGER`, Primary Key, Autoincrement)
   * `id_anggota` (`INTEGER`, Foreign Key $\rightarrow$ `anggota.id`)
   * `id_buku` (`INTEGER`, Foreign Key $\rightarrow$ `buku.id`)
   * `tgl_pinjam` (`DATE`, Not Null)
   * `tgl_kembali` (`DATE`, Nullable — bernilai `NULL` apabila buku belum dikembalikan)

---

## 🚀 Ruang Lingkup & Tahapan Pengerjaan

### 1. Perancangan & Manipulasi Basis Data (SQLite)
* **Pembuatan Skema & Integritas Referensial:** Mengaktifkan `PRAGMA foreign_keys = ON` dan mendefinisikan struktur tabel `buku`, `anggota`, serta `peminjaman`.
* **Populasi Data (DML):** Menambahkan 5 data buku, 3 data anggota, dan 4 transaksi peminjaman (termasuk transaksi aktif dengan nilai `tgl_kembali = NULL`).
* **Query Relasional (`JOIN`):** Menggabungkan tabel `peminjaman`, `anggota`, dan `buku` untuk menyajikan daftar transaksi peminjaman yang lengkap.
* **Agregasi Data (`GROUP BY`):** Menghitung total buku yang dipinjam oleh masing-masing anggota menggunakan `COUNT()` dan `LEFT JOIN`.

### 2. Eksplorasi Data & Visualisasi (Python)
* **Integrasi Pandas:** Mengonversi hasil query SQL langsung menjadi `pandas.DataFrame` menggunakan `pd.read_sql_query()`.
* **Analisis & Feature Engineering:** Menghitung selisih waktu peminjaman (`durasi_hari`) untuk transaksi yang telah selesai serta mengidentifikasi status peminjaman aktif.
* **Visualisasi Grafik:**
  * Diagram batang total buku yang dipinjam per anggota.
  * Diagram batang distribusi durasi peminjaman per judul buku.

---

## 📁 Struktur Repository

```text
├── Tugas_BasisData_SQLite_411222050_MercyAngelia.ipynb   # Notebook Google Colab (Kode SQL, Pandas & Visualisasi)
└── README.md                                             # Dokumentasi proyek
