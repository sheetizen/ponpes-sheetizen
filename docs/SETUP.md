# Dokumentasi Sheet: SETUP

## 1. Tujuan Sheet

Sheet `SETUP` bertujuan untuk menyimpan semua parameter konfigurasi umum dan informasi dasar mengenai Pondok Pesantren (PONPES) yang bersifat fundamental untuk operasional sistem administrasi keuangan ini. Data di sini cenderung statis atau jarang diubah.

## 2. Struktur Kolom dan Panduan Pengisian

Berikut adalah perkiraan detail untuk setiap kolom dalam sheet `SETUP`. Pastikan untuk mengisi data sesuai dengan panduan.

| Nama Kolom         | Tipe Data          | Wajib Diisi? | Contoh Isi                                     | Keterangan                                                                                                |
|--------------------|--------------------|--------------|------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| `Nama_Pengaturan`  | Teks               | **YA** | `Nama Ponpes`                                  | Label atau deskripsi dari item pengaturan.                                                                |
| `Nilai_Pengaturan` | Teks/Angka/Tanggal | **YA** | `PONPES by SHEETIZEN`                            | Nilai aktual dari item pengaturan tersebut.                                                               |
| `Keterangan`       | Teks               | Tidak        | `Nama resmi institusi sesuai akta pendirian`   | Penjelasan tambahan mengenai item pengaturan jika diperlukan.                                             |

**Contoh Baris Data Pengaturan:**

| Nama_Pengaturan                 | Nilai_Pengaturan                         | Keterangan                                       |
|---------------------------------|------------------------------------------|--------------------------------------------------|
| `Nama Ponpes`                   | `PONPES YOGS VERSE`                      | Nama resmi institusi.                            |
| `Alamat Lengkap Ponpes`         | `Jl. Pendidikan No. 1, Kota Yogs, Provinsi Z` | Alamat lengkap ponpes.                           |
| `Email Ponpes`                  | `info@sheetizen.web.id`            | Alamat email resmi ponpes.                       |
| `Nama Kepala Ponpes`            | `K.H. Ahmad Yasin`                       | Nama pimpinan tertinggi ponpes.                  |
| `Nomor WA atau Telepon`         | `628998138103`                          | Nomor telepon kantor ponpes.                     |
| `Tahun Ajaran Aktif`            | `2024/2025`                              | Tahun ajaran yang sedang berjalan.               |
| `Logo Ponpes (Path/URL)`        | `insert -> image -> di dalam sel`         | Lokasi file logo untuk kuitansi/laporan (jika ada). |
| `Lokasi`                        | `Bandung`                          | Lokasi ponpes.                     |
| `Tanggal Hari ini`          | `Otomatis Terisi`                          | Otomatis terisi dalam bentuk Hijriah.                     |


**Catatan Penting:**
* Setiap baris mewakili satu item konfigurasi.
* Isi semua `Nama_Pengaturan` yang relevan dan `Nilai_Pengaturan` yang sesuai.
* Keakuratan data di sheet ini penting karena bisa jadi dirujuk oleh formula atau skrip di sheet lain untuk menampilkan informasi (misalnya di kop kuitansi).

## 3. Cara Mengisi Sheet Ini

1.  Identifikasi semua parameter konfigurasi yang dibutuhkan oleh sistem administrasi PONPES by Sheetizen.
2.  Untuk setiap parameter, buat satu baris baru.
3.  Isi kolom `Nama_Pengaturan` dengan label yang jelas (misalnya, "Nama Ponpes").
4.  Isi kolom `Nilai_Pengaturan` dengan data yang sesuai (misalnya, "PONPES YOGS VERSE").
5.  Tambahkan `Keterangan` jika diperlukan untuk memperjelas maksud dari pengaturan tersebut.
6.  Sheet ini biasanya diisi sekali di awal penggunaan sistem dan hanya diubah jika ada perubahan fundamental pada data institusi.

## 4. Mengisi SETUP (Pengaturan Spreadsheet)

Selain informasi umum tentang ponpes, setting juga untuk 
1.  `PEMBAYARAN atau TAGIHAN` = detail tagihan tiap kelas.
2.  `DATABASE KELAS` = data kelas yang ada di ponpes.
3.  `METODE BAYAR` = masukkan metode bayar yang ada di ponpes - terkait dengan saldo aset.
4.  `PENGELUARAN`	= detail kategori pengeluaran.

**Catatan Penting:**
* Isi kolom yang berwarna abu-abu.
* Kolom berwana putih akan terisi otomatis.

## 5. Keterkaitan dengan Sheet Lain

* **`Template_Kuitansi`**: Informasi seperti `Nama Ponpes`, `Alamat Lengkap Ponpes` akan diambil dari sini untuk ditampilkan di kuitansi.
* **`Input Pembayaran`**: `TAGIHAN` sebagai kategori pemasukan, `METODE BAYAR` sebagai metode pembayaran.
* **`Input Pengeluaran`**: `PENGELUARAN` sebagai kateogri pengeluaran. 
* **`Dashboard`**: Beberapa informasi umum seperti `KATEGORI PEMASUKAN`, `KATEGORI PENGELUARAN`, `ASET` akan ditampilkan di dashboard.
* **`Database Santri`**: Data kelas tiap santri akan diambil dari `DATABASE KELAS`

---
[Kembali ke Daftar Isi Utama](../README.md)
