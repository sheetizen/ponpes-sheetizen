# Dokumentasi Sheet: Template Kuitansi

## 1. Tujuan Sheet

Sheet `Template Kuitansi` **tidak digunakan untuk menyimpan data transaksi kuitansi individual**. Sebaliknya, sheet ini berfungsi sebagai **master definisi atau cetak biru (blueprint)** untuk struktur, format, dan elemen-elemen yang akan ditampilkan pada sebuah kuitansi pembayaran standar PONPES YOGS VERSE.

Tujuan utamanya adalah untuk:
1.  **Menstandarisasi tampilan visual** semua kuitansi yang dikeluarkan.
2.  Menjadi **acuan bagi skrip Google Apps Script** di Spreadsheet yang bertugas menghasilkan file kuitansi individual secara otomatis dalam format PDF atau untuk dicetak. Data untuk mengisi kuitansi akan diambil dari sheet `Input Pembayaran` dan `Database Santri`.
3.  Mendefinisikan **elemen-elemen statis** (seperti label "No. Kuitansi:", "Diterima Dari:") dan **placeholder untuk data dinamis** (seperti nama santri, jumlah bayar, tanggal) yang akan diisi pada kuitansi.

## 2. Struktur Kolom dan Panduan Pengisian (Definisi Elemen Template)

Kolom-kolom di sheet ini mendefinisikan setiap bagian dari kuitansi. 
Berikut adalah contoh struktur kuitansinya:

| ID_Elemen             | Deskripsi_Elemen           | Tipe_Elemen  | Nilai_Statis_Teks    | Sheet_Sumber_Dinamis | Kolom_Sumber_Dinamis     | Urutan_Tampil |
|-----------------------|----------------------------|--------------|----------------------|----------------------|--------------------------|---------------|
| `kop_nama`            | Nama Ponpes (Kop)          | Data Dinamis |                      | `SETUP`              | (Kondisi: `Nama_Pengaturan="Nama Ponpes"`) | 1             |
| `kop_alamat`          | Alamat Ponpes (Kop)        | Data Dinamis |                      | `SETUP`              | (Kondisi: `Nama_Pengaturan="Alamat Lengkap Ponpes"`) | 2             |
| `email dan WA`        | Email dan WA Ponpes (Kop)             | Data Dinamis  | zupper15@gmail.com  | `SETUP`                     |                          | 3             |
| `no_kuitansi_label`   | No. Kuitansi         | Teks Statis  | No. Kuitansi :       |                      |                          | 4             |
| `no_kuitansi_value`   | Nilai No. Kuitansi         | Data Dinamis |                      | `Input Pembayaran`   | `NOMOR KUITANSI Pembayaran`| 5             |
| `tgl_kuitansi_label`  | Label Tanggal              | Teks Statis  | Tanggal :            |                      |                          | 6             |
| `tgl_kuitansi_value`  | Nilai Tanggal Pembayaran   | Data Dinamis |                      | `Input Pembayaran`   | `Tanggal_Bayar`          | 7             |
| `diterima_dari_label` | Label Diterima Dari        | Teks Statis  | Telah Diterima Dari :|                      |                          | 8             |
| `diterima_dari_value` | Nama Wali/Ortu Santri      | Data Dinamis |                      | `Database Santri`    | `Nama_Wali/Ortu_Santri (Otomatis)` | 9             |
| `Nama Santri Label`   | Nama Santri                | Teks Statis  | Nama Santri :        |                      |                          | 10             |
| `Nama Santri`         | Nilai Nama Santri                | Data Dinamis |                      | `Input Pembayaran`   | `Nama_Santri (Otomatis)` | 11             |
| `kelas_label`         | Label Kelas               | Teks Statis  | Kelas :           |                      |                          | 12            |
| `kelas_value`        | Nilai Kelas (Angka atau Teks) | Data Dinamis |                      | `Database Santri`   | `Kelas`           | 13            |
| `metode_pembayaran_label`     | Label Metode            | Teks Statis  | Metode Pembayaran :          |                      |                          | 14            |
| `metode_value`     | Nilai Metode Pembayaran (Teks)     | Data Dinamis |                      | `Input Pembayaran`   | `Metode Pembayaran` | 15            |
| `jumlah_uang_label`         | Jumlah Uang     | Teks Statis  | Uang Sejumlah :   |                      |                          | 16            |
| `jumlah_uang_value`         | Jumlah Pembayaran       | Data Dinamis |                      | `Input Pembayaran`   | `Nominal Pembayaran`   | 17            |
| `terbilang_label`         | Terbilang     | Teks Statis  | Terbilang   |                      |                          | 18            |
| `terbilang_value`         | Terbilang       | Data Dinamis |                      | `Otomatis`   | `Dari Kolom Uang Sejumlah`   | 19            |

**Catatan Penting:**
* Sheet ini adalah **DEFINISI TEMPLATE**, bukan tempat mengisi data kuitansi satu per satu.

## 4. Keterkaitan dengan Sheet Lain

* **`Input Pembayaran` (KRUSIAL)**: Merupakan sumber data dinamis utama untuk mengisi detail spesifik transaksi pada kuitansi (misalnya, `Nomor_Kuitansi_Pembayaran`, `Tanggal_Bayar`, `Jumlah_Bayar`, `Deskripsi_Pembayaran`, dan nama santri yang ditarik ke sini).
* **`Database Santri`**: Dapat menjadi sumber data dinamis untuk informasi detail santri.
* **`SETUP`**: Dapat menjadi sumber data dinamis untuk informasi umum ponpes yang bersifat statis namun perlu ditampilkan di kuitansi (misalnya, `Nama Ponpes`, `Alamat Ponpes`, `Email dan WA` `Tanggal`).

* ---

[Kembali ke Daftar Isi Utama](../README.md)

[Sebelumnya - Dashboard](../docs/Dashboard.md)
