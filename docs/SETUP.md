# Dokumentasi Sheet: SETUP

## 1. Tujuan Sheet

Sheet `SETUP` bertujuan untuk menyimpan semua parameter konfigurasi umum dan informasi dasar mengenai Pondok Pesantren (PONPES) yang bersifat fundamental untuk operasional sistem administrasi keuangan ini. Data di sini cenderung statis atau jarang diubah.

## 2. Struktur Kolom dan Panduan Pengisian

Berikut adalah perkiraan detail untuk setiap kolom dalam sheet `SETUP`. Pastikan untuk mengisi data sesuai dengan panduan.

| Nama Kolom         | Tipe Data          | Wajib Diisi? | Contoh Isi                                     | Keterangan                                                                                                |
|--------------------|--------------------|--------------|------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| `Nama_Pengaturan`  | Teks               | **YA** | `Nama Ponpes`                                  | Label atau deskripsi dari item pengaturan.                                                                |
| `Nilai_Pengaturan` | Teks/Angka/Tanggal | **YA** | `PONPES YOGS VERSE`                            | Nilai aktual dari item pengaturan tersebut.                                                               |
| `Keterangan`       | Teks               | Tidak        | `Nama resmi institusi sesuai akta pendirian`   | Penjelasan tambahan mengenai item pengaturan jika diperlukan.                                             |

**Contoh Baris Data Pengaturan:**

| Nama_Pengaturan                 | Nilai_Pengaturan                         | Keterangan                                       |
|---------------------------------|------------------------------------------|--------------------------------------------------|
| `Nama Ponpes`                   | `PONPES YOGS VERSE`                      | Nama resmi institusi.                            |
| `Alamat Lengkap Ponpes`         | `Jl. Pendidikan No. 1, Kota Yogs, Provinsi Z` | Alamat lengkap ponpes.                           |
| `Nomor Telepon Ponpes`          | `(021) 1234567`                          | Nomor telepon kantor ponpes.                     |
| `Email Ponpes`                  | `info@ponpesyogsverse.sch.id`            | Alamat email resmi ponpes.                       |
| `Website Ponpes`                | `www.ponpesyogsverse.sch.id`             | Alamat website resmi ponpes.                     |
| `Nama Kepala Ponpes`            | `K.H. Ahmad Yasin`                       | Nama pimpinan tertinggi ponpes.                  |
| `Nama Bendahara`                | `Ustadzah Fatimah Azzahra`               | Nama bendahara atau penanggung jawab keuangan.   |
| `Tahun Ajaran Aktif`            | `2024/2025`                              | Tahun ajaran yang sedang berjalan.               |
| `Rekening Bank Ponpes (Utama)`  | `Bank Syariah Yogs - 1234567890 a.n. PONPES YOGS VERSE` | Informasi rekening utama untuk penerimaan.   |
| `Logo Ponpes (Path/URL)`        | `/images/logo.png` atau URL gambar         | Lokasi file logo untuk kuitansi/laporan (jika ada). |

**Catatan Penting:**
* Setiap baris mewakili satu item konfigurasi.
* Isi semua `Nama_Pengaturan` yang relevan dan `Nilai_Pengaturan` yang sesuai.
* Keakuratan data di sheet ini penting karena bisa jadi dirujuk oleh formula atau skrip di sheet lain untuk menampilkan informasi (misalnya di kop kuitansi).

## 3. Cara Mengisi Sheet Ini

1.  Identifikasi semua parameter konfigurasi yang dibutuhkan oleh sistem administrasi PONPES YOGS VERSE.
2.  Untuk setiap parameter, buat satu baris baru.
3.  Isi kolom `Nama_Pengaturan` dengan label yang jelas (misalnya, "Nama Ponpes").
4.  Isi kolom `Nilai_Pengaturan` dengan data yang sesuai (misalnya, "PONPES YOGS VERSE").
5.  Tambahkan `Keterangan` jika diperlukan untuk memperjelas maksud dari pengaturan tersebut.
6.  Sheet ini biasanya diisi sekali di awal penggunaan sistem dan hanya diubah jika ada perubahan fundamental pada data institusi.

## 4. Keterkaitan dengan Sheet Lain

* **`Template_Kuitansi`**: Informasi seperti `Nama Ponpes`, `Alamat Lengkap Ponpes` mungkin akan ditarik dari sini untuk ditampilkan di kuitansi.
* **`Dashboard`**: Beberapa informasi umum mungkin ditampilkan di dashboard.
* Sheet lain yang memerlukan informasi institusi secara umum.

---
[Kembali ke Daftar Isi Utama](../README.md)
  
