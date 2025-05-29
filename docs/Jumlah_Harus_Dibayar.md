# Dokumentasi Sheet: Jumlah Harus Dibayar

## 1. Tujuan Sheet

Sheet `Jumlah Harus Dibayar` berfungsi sebagai **master data untuk semua jenis tagihan atau iuran** yang berlaku di PONPES by Sheetizen. Sheet ini merinci deskripsi, nominal, dan periode setiap jenis pembayaran yang menjadi kewajiban santri. Ini menjadi dasar untuk menentukan berapa besar tagihan yang harus dibayar oleh santri.

## 2. Struktur Kolom dan Panduan Pengisian

Berikut adalah detail untuk setiap kolom dalam sheet `Jumlah Harus Dibayar`.

| Nama Kolom                | Tipe Data         | Wajib Diisi? | Contoh Isi                                | Keterangan                                                                                                                                  |
|---------------------------|-------------------|--------------|-------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| `Nama Bulan Masehi`              | Teks       | **YA** | `Januari`, `Februari`, ..., `Desember`
| Bulan dalam Masehi. |
| `Nama Bulan Hijriah`       | Teks              | **YA** | `Muharram`, `Safar`, ..., `Dzulhijjah` | Bulan dalam Hijriah.                                                                                               |
| `Kategori_Tagihan`        | Teks (Pilihan)    | **YA** | `SPP`, `Uang Pangkal`, `Iuran Kegiatan`, `Denda`, `Lain-lain` | Pengelompokan jenis tagihan. Sebaiknya gunakan Data Validation.                                                                          |
| `Nominal_Tagihan`         | Angka             | **YA** | `500000`                                  | Jumlah nominal yang harus dibayar untuk tagihan ini (dalam Rupiah, tanpa titik atau koma).                                                    |
| `Periode_Tagihan`         | Teks (Pilihan)    | **YA** | `Bulanan`, `Tahunan`, `Sekali Bayar`, `Per Semester` | Siklus atau frekuensi tagihan. Sebaiknya gunakan Data Validation.                                                                          |
| `Berlaku_Untuk_Kelas`     | Teks              | Tidak        | `Semua`, `VII`, `VIII, IX`, `Khusus Tahfidz` | Menentukan apakah tagihan ini spesifik untuk kelas/program tertentu. Bisa "Semua" atau daftar kelas dipisah koma.                             |
| `Tahun_Ajaran_Berlaku`    | Teks              | Tidak        | `2024/2025`                               | Tahun ajaran di mana tagihan ini berlaku. Bisa dikosongkan jika berlaku umum.                                                              |
| `Bulan_Berlaku`           | Teks (Pilihan)    | Tidak        | `Januari`, `Februari`, ..., `Desember`    | Untuk tagihan bulanan, menentukan bulan spesifik. Bisa dikosongkan jika tidak relevan (misal untuk Uang Pangkal).                            |
| `Tanggal_Jatuh_Tempo_Rule` | Teks              | Tidak        | `Tanggal 10 setiap bulan`, `Akhir bulan pendaftaran` | Aturan umum untuk penentuan tanggal jatuh tempo. Bisa juga tanggal spesifik jika tagihan one-time.                                        |
| `Akun_Pendapatan_Terkait` | Teks              | Tidak        | `4-1001 SPP`, `4-1002 Uang Pangkal`         | Kode akun akuntansi terkait jika sistem ini terintegrasi dengan pencatatan akuntansi (opsional).                                            |

**Catatan Penting:**
* **`ID_Tagihan`**: Kolom ini adalah *Primary Key*. Pastikan setiap jenis tagihan memiliki `ID_Tagihan` yang unik.
* **Konsistensi**: `Kategori_Tagihan` dan `Periode_Tagihan` sebaiknya menggunakan pilihan terbatas (Data Validation) untuk konsistensi.
* **`Berlaku_Untuk_Kelas`**: Jika tagihan berlaku untuk beberapa kelas, bisa ditulis dipisah koma (misal: `VII, VIII, IX`). Jika berlaku untuk semua, tulis `Semua`.
* **`Nominal_Tagihan`**: Masukkan hanya angka, tanpa "Rp" atau pemisah ribuan. Format tampilan bisa diatur di Spreadsheet.

## 3. Cara Mengisi Sheet Ini

1.  Identifikasi semua jenis iuran atau tagihan yang ada di PONPES YOGS VERSE (misalnya, SPP, uang pangkal, iuran ekskul, iuran kitab, dll.).
2.  Untuk setiap jenis tagihan:
    * Tambahkan baris baru.
    * Isi `ID_Tagihan` dengan kode yang unik dan mudah diingat.
    * Isi `Deskripsi_Tagihan` dengan penjelasan yang jelas.
    * Pilih `Kategori_Tagihan` dan `Periode_Tagihan` yang sesuai.
    * Masukkan `Nominal_Tagihan` yang benar.
    * Isi kolom `Berlaku_Untuk_Kelas`, `Tahun_Ajaran_Berlaku`, `Bulan_Berlaku`, dan `Tanggal_Jatuh_Tempo_Rule` jika relevan untuk tagihan tersebut.
3.  Sheet ini diisi atau diperbarui setiap kali ada jenis tagihan baru, perubahan nominal, atau perubahan kebijakan tagihan. Biasanya di-review setiap awal tahun ajaran.

## 4. Keterkaitan dengan Sheet Lain

* **`Input Pembayaran`**: `ID_Tagihan` dari sheet ini dapat digunakan di `Input Pembayaran` untuk merinci pembayaran tersebut untuk tagihan apa. `Deskripsi_Tagihan` dan `Nominal_Tagihan` dapat ditarik otomatis (via `VLOOKUP`/`XLOOKUP`) ke `Input Pembayaran` berdasarkan `ID_Tagihan` yang dipilih.
* **`Data Bayar Per Santri`**: Informasi dari sheet ini (khususnya `Deskripsi_Tagihan` dan `Nominal_Tagihan`) penting untuk menghitung total kewajiban santri dan status pembayarannya.
* **`Dashboard`**: Agregasi pendapatan per `Kategori_Tagihan` dapat ditampilkan di Dashboard.
* **`SETUP WA`**: `Deskripsi_Tagihan` dan `Nominal_Tagihan` bisa digunakan dalam template pengingat tagihan.

---[Kembali ke Daftar Isi Utama](../README.md)

[Sebelumnya - Setup](../docs/SETUP_WA.md) | 
[Selanjutnya - Jumlah Harus Dibayar](../docs/Database_Santri.md)
