# Dokumentasi Sheet: Database Santri

## 1. Tujuan Sheet

Sheet `Database Santri` berfungsi sebagai **database utama** yang menyimpan semua informasi detail mengenai santri yang terdaftar di PONPES YOGS VERSE. Data di sheet ini menjadi rujukan utama untuk identitas dan status santri dalam sistem administrasi keuangan.

## 2. Struktur Kolom dan Panduan Pengisian

Berikut adalah detail untuk setiap kolom dalam sheet `Database Santri`. Pastikan untuk mengisi data sesuai dengan panduan agar integritas data terjaga.

| Nama Kolom         | Tipe Data          | Wajib Diisi? | Contoh Isi                     | Keterangan                                                                                                |
|--------------------|--------------------|--------------|--------------------------------|-----------------------------------------------------------------------------------------------------------|
| `NO`               | Angka              | **OTOMATIS** | `01`                     | Nomor berurutan secara otomatis supaya lebih rapi.  |
| `Nama Santri`     | Teks               | **YA** | `Muhammad Al Fatih`            | Nama lengkap santri sesuai akta/dokumen resmi.                                                            |
| `Kelas`            | Teks               | **YA** | `VII A`, `XII IPA`             | Kelas atau tingkatan santri saat ini (diambil dari  `SETUP `.                                                                     |
| `NIS`              | Angka              | **YA**       | `24250002`                   | Nomor Induk Siswa.                                                                    |
| `Jenis_Kelamin`    | Teks (Pilihan)     | **YA** | `Laki-laki` / `Perempuan`      | Jenis kelamin santri. Menggunakan Data Validation.                                                  |
| `Status_Santri`    | Teks (Pilihan)     | **YA** | `Aktif`, `Pindah`, `Lulus` | Status santri saat ini. Menggunakan Data Validation.                                       |
| `Alamat`           | Teks Panjang       | **YA** | `Jl. Merdeka No. 10, Kota Yogs, Provinsi Z, Kode Pos 12345` | Alamat lengkap tempat tinggal wali santri.                                                                |
| `Nama Ortu/Wali`        | Teks               | **YA** | `Abdullah Hasan`               | Nama lengkap orang tua atau wali santri.                                                                  |
| `No WA ORTU/Wali`       | Angka       | **YA** | `6281234567890`                 | Nomor WA wali yang aktif dan bisa dihubungi. Format: `628xxxxxxxxxx`. Penting untuk komunikasi/notifikasi kuitansi pembayaran. |

**Catatan Penting:**
* **`NAMA SANTRI`**: Kolom ini adalah *Primary Key*. Pastikan memasukkan nama santri dengan benar. `NAMA SANTRI` dari sheet ini akan digunakan di sheet `Input Pembayaran` dan `Data Bayar Per Santri` untuk menghubungkan data.
* **Format Tanggal**: Usahakan menggunakan format tanggal yang konsisten di seluruh spreadsheet (misalnya, `DD/MM/YYYY`).
* **Pilihan Terbatas (Data Validation)**: Untuk kolom seperti `Jenis_Kelamin`, `Status_Santri`, `Hubungan_Wali`, sangat disarankan untuk menggunakan fitur "Data Validation" di Spreadsheet untuk membuat daftar pilihan yang baku. Ini menjaga konsistensi data dan memudahkan input.
* **`No_HP_Wali`**: Pastikan formatnya benar dan valid untuk pengiriman notifikasi WhatsApp (jika fitur WA aktif).

## 3. Cara Mengisi Sheet Ini

1.  **Santri Baru**:
    * Tambahkan baris baru di bagian bawah data yang sudah ada.
    * Isi semua kolom yang bertanda "Wajib Diisi" (**YA**).

2.  **Update Data Santri**:
    * Cari baris data santri yang ingin diubah (bisa menggunakan fungsi Find/Search di Spreadsheet berdasarkan `NAMA SANTRI` atau `NIS`).
    * Ubah informasi pada kolom yang relevan.
    * **Peringatan**: Hindari mengubah `NAMA SANTRI` jika sudah ada transaksi terkait santri tersebut, karena dapat merusak integritas data di sheet lain. Jika terpaksa diubah, pastikan semua `NAMA SANTARI` yang merujuk di sheet lain juga diperbarui.

3.  **Menonaktifkan Santri**:
    * Ubah nilai di kolom `Status_Santri` menjadi "Pindah" atau "Lulus" (sesuai pilihan yang tersedia).
    * Jangan menghapus baris data santri yang sudah tidak aktif jika riwayat transaksinya masih ingin disimpan untuk keperluan audit atau pelaporan masa lalu.

## 4. Keterkaitan dengan Sheet Lain

* **`Input Pembayaran`**: Menggunakan `NAMA SANTRI` dari sheet ini untuk mencatat siapa yang melakukan pembayaran. `KELAS` bisa ditarik (menggunakan `VLOOKUP` atau `XLOOKUP`) untuk verifikasi.
* **`Data Bayar Per Santri`**: Menampilkan data santri (seperti `Nama_Lengkap`, `Kelas`, `Jumlah yang Sudah Dibayar`) yang diambil dari sheet ini berdasarkan `NAMA SANTRI`.
* **`NOTIFIKASI WA (BUKTI BAYAR/KUITANSI)`**: `NAMA ORTU/WALI`, `NAMA SANTRI`, `NOMOR WA ORTU/WALI` digunakan untuk personalisasi notifikasi WhatsApp.
* **`Jumlah Harus Dibayar`**: Mungkin ada logika yang mengaitkan `Kelas` santri dengan jenis tagihan tertentu.

---
---
[Kembali ke Daftar Isi Utama](../README.md)

[Sebelumnya - Jumlah Harus Dibayar](../docs/Jumlah_Harus_Dibayar.md) | 
[Selanjutnya - Input Pembayaran](../docs/Input_Pembayaran.md)
