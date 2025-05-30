# Dokumentasi Sheet: Data Bayar Per Santri

## 1. Tujuan Sheet

Sheet `Data Bayar Per Santri` bertujuan untuk **merangkum dan menampilkan riwayat serta status pembayaran dari masing-masing santri**. Sheet ini idealnya **bukan untuk input manual**, melainkan merupakan hasil olahan data (misalnya menggunakan `PIVOT TABLE`, `QUERY`, atau formula `SUMIFS`, `COUNTIFS`, dll.) yang sumbernya berasal dari sheet `Input Pembayaran` dan `Database Santri`.

Tujuannya adalah untuk memudahkan pemantauan tunggakan, rekapitulasi pembayaran, dan memberikan informasi cepat mengenai status keuangan per santri.

## 2. Struktur Kolom yang Mungkin Ada (Hasil Olahan)

Berikut adalah perkiraan kolom yang mungkin ada di sheet ini. Ingat, ini adalah **kolom hasil kalkulasi atau query, bukan untuk diisi manual.**

| Nama Kolom                      | Tipe Data    | Sumber Data Utama (Perkiraan)                                       | Contoh Isi                             | Keterangan                                                                                                  |
|---------------------------------|--------------|---------------------------------------------------------------------|----------------------------------------|-------------------------------------------------------------------------------------------------------------|
| `ID_Santri`                     | Teks/Angka   | `Database Santri`.`ID_Santri` (sebagai unique key/grouping)           | `PYS25001`                             | Identifier unik santri.                                                                                     |
| `Nama_Lengkap_Santri`           | Teks         | `Database Santri`.`Nama_Lengkap`                                      | `Muhammad Al Fatih`                    | Nama lengkap santri, ditarik berdasarkan `ID_Santri`.                                                       |
| `Kelas_Santri`                  | Teks         | `Database Santri`.`Kelas`                                             | `VII A`                                | Kelas santri saat ini, ditarik berdasarkan `ID_Santri`.                                                     |
| `Jenis_Tagihan_Spesifik`        | Teks         | `Jumlah Harus Dibayar`.`Deskripsi_Tagihan` (jika laporan per jenis tagihan) | `SPP Bulan Juli 2024`                  | Jika laporan dirinci per jenis tagihan yang seharusnya dibayar santri.                                      |
| `Total_Kewajiban_Santri`        | Angka        | Kalkulasi dari `Jumlah Harus Dibayar` (disesuaikan per santri/kelas)   | `500000` (untuk 1 jenis tagihan)       | Total nominal yang seharusnya dibayarkan santri (bisa per jenis tagihan atau total keseluruhan).              |
| `Total_Sudah_Dibayar_Santri`    | Angka        | Agregasi (`SUM`) dari `Input Pembayaran`.`Jumlah_Bayar` per `ID_Santri` | `500000`                               | Total akumulasi pembayaran yang telah dilakukan oleh santri (bisa per jenis tagihan atau total).              |
| `Sisa_Tunggakan_Santri`         | Angka        | `Total_Kewajiban_Santri` - `Total_Sudah_Dibayar_Santri`                 | `0`                                    | Selisih antara kewajiban dan pembayaran. Jika negatif, berarti ada kelebihan bayar.                         |
| `Status_Pembayaran_Santri`      | Teks         | Logika IF berdasarkan `Sisa_Tunggakan_Santri`                         | `Lunas`, `Belum Lunas`, `Cicilan`      | Status pembayaran santri secara keseluruhan atau per jenis tagihan.                                         |
| `Tanggal_Pembayaran_Terakhir`   | Tanggal      | Agregasi (`MAX`) dari `Input Pembayaran`.`Tanggal_Bayar` per `ID_Santri` | `28/05/2025`                           | Tanggal transaksi pembayaran terakhir dari santri tersebut.                                                 |
| `Jumlah_Transaksi_Pembayaran`   | Angka        | Agregasi (`COUNT`) dari `Input Pembayaran` per `ID_Santri`             | `1`                                    | Jumlah berapa kali santri melakukan pembayaran.                                                             |
| `Rincian_Tagihan_Belum_Lunas` | Teks         | Logika kompleks atau catatan manual (kurang ideal jika otomatis)      | `SPP Agustus, Iuran Buku`              | Daftar tagihan spesifik yang belum lunas (lebih kompleks untuk diotomatisasi penuh dalam satu sel).         |

**Catatan Penting:**
* **BUKAN INPUT MANUAL**: Tekankan bahwa sheet ini idealnya dihasilkan oleh formula atau fitur Spreadsheet (Pivot Table, Query). Pengguna hanya melihat hasilnya.
* **Sumber Data**: Pastikan formula merujuk dengan benar ke sheet `Input Pembayaran`, `Database Santri`, dan `Jumlah Harus Dibayar`.
* **Struktur Laporan**: Tampilan sheet ini bisa beragam. Bisa jadi satu baris per santri untuk total keseluruhan, atau beberapa baris per santri jika dirinci per jenis tagihan yang menjadi kewajibannya.
* **Refresh Data**: Jika menggunakan Pivot Table atau Query, pengguna mungkin perlu me-refresh data secara manual agar tampilan selalu update, kecuali jika Spreadsheet mendukung update otomatis.

## 3. Cara Menggunakan Sheet Ini (Sebagai Pembaca Laporan)

1.  Buka sheet `Data Bayar Per Santri`.
2.  Gunakan fitur filter atau sort di Spreadsheet untuk mencari santri tertentu atau mengurutkan berdasarkan tunggakan, nama, kelas, dll.
3.  Perhatikan kolom `Sisa_Tunggakan_Santri` dan `Status_Pembayaran_Santri` untuk mengetahui kondisi keuangan masing-masing santri.
4.  Jika ada keraguan pada data yang ditampilkan, lakukan verifikasi silang dengan data transaksi di `Input Pembayaran` dan data master di `Database Santri` serta `Jumlah Harus Dibayar`.
5.  **Jangan mengubah data secara manual di sheet ini** jika ia dirancang sebagai output otomatis. Perubahan harus dilakukan di sheet sumber (`Input Pembayaran` untuk transaksi, atau sheet master untuk data santri/tagihan).

## 4. Keterkaitan dengan Sheet Lain

* **`Input Pembayaran`**: Ini adalah **SUMBER DATA UTAMA** untuk semua nominal dan tanggal pembayaran.
* **`Database Santri`**: Menyediakan data identitas santri (`ID_Santri`, `Nama_Lengkap_Santri`, `Kelas_Santri`).
* **`Jumlah Harus Dibayar`**: Menyediakan data mengenai apa saja dan berapa besar tagihan yang menjadi dasar perhitungan `Total_Kewajiban_Santri`.
* **`Dashboard`**: Ringkasan dari sheet ini (misalnya, jumlah santri menunggak, total tunggakan) dapat ditampilkan di `Dashboard`.
* **`SETUP WA`**: Informasi status tunggakan dari sheet ini bisa menjadi pemicu untuk mengirim pengingat tagihan melalui WhatsApp.

---
[Kembali ke Daftar Isi Utama](../README.md)

[Sebelumnya - Database Santri](../docs/Database_Santri.md) | 
[Selanjutnya - Input Pengeluaran](../docs/Input_Pengeluaran.md)
