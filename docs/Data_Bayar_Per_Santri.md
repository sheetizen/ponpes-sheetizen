# Dokumentasi Sheet: Data Bayar Per Santri

## 1. Tujuan Sheet

Sheet `Data Bayar Per Santri` berfungsi sebagai **laporan terpusat yang merangkum riwayat dan status pembayaran dari setiap santri secara otomatis**. Tujuan utamanya adalah untuk menyediakan pandangan yang jelas dan terkini mengenai kewajiban finansial santri, total pembayaran yang telah dilakukan, sisa tunggakan, dan status pembayaran secara keseluruhan atau per jenis tagihan.

**PENTING: Sheet ini dirancang untuk sepenuhnya OTOMATIS. TIDAK ADA INPUT DATA MANUAL yang dilakukan di sheet ini, kecuali nama Santri**  Semua data yang ditampilkan di sini dihasilkan melalui formula Spreadsheet (seperti `QUERY`, `SUMIFS`, `VLOOKUP`/`XLOOKUP`, `IF`, dll.) yang mengambil dan mengolah data dari sheet-sheet sumber lainnya, terutama `Input Pembayaran`, `Database Santri`, dan `Jumlah Harus Dibayar`.

Di sheet ini Anda adalah pembaca laporan, seperti bagian administrasi, bendahara, atau pimpinan ponpes, untuk keperluan pemantauan, penagihan, dan pengambilan keputusan.

## 2. Struktur Kolom dan Asal Data (Semua Kolom Terisi Otomatis)

Kolom-kolom berikut adalah perkiraan yang umum ada dalam sheet laporan seperti ini. Nama kolom dan detail kalkulasi spesifik mungkin berbeda di Spreadsheet Anda, namun prinsipnya adalah data ditarik dan dihitung secara otomatis.

| Nama Kolom (Perkiraan)     | Tipe Data (Hasil) | Kemungkinan Asal Data & Cara Perhitungan (Otomatis)                                                                                                                              | Contoh Isi (Hasil)            | Keterangan                                                                                                                               |
|----------------------------|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| `Nama_Lengkap_Santri`      | Teks              | Diambil dari `Database Santri` (`Nama_Lengkap`) menggunakan `ID_Santri` sebagai lookup key (misal, dengan `VLOOKUP` atau `XLOOKUP`).                                                  | `Muhammad Al Fatih`           | Nama lengkap santri untuk memudahkan identifikasi.                                                                                       |
| `Kelas`                    | Teks              | Diambil dari `Database Santri` (`Kelas`) menggunakan `Nama Santri` sebagai lookup key.                                                                                                 | `VII A`                       | Kelas santri saat ini. Berguna untuk filtering atau analisis per kelas.                                                                  |
| `Wali/Ortu`                    | Teks              | Diambil dari `Database Santri` (`Nama ortu`) menggunakan `Nama Santri` sebagai lookup key.                                                                                                 | `AAYOGRAPH`                       | Wali santri saat ini. Berguna untuk filtering atau analisis data.                                                                  |
| `Jenis_Tagihan_Deskripsi`  | Teks              | Diambil dari `Jumlah Harus Dibayar` (`Deskripsi_Tagihan`). Muncul jika laporan ini merinci status per jenis tagihan, bukan hanya total keseluruhan per santri.                      | `SPP Bulan Juli 2025`         | Deskripsi spesifik tagihan yang menjadi kewajiban santri.                                                                                |
| `Periode_Tagihan`          | Teks              | Bisa diambil dari `Jumlah Harus Dibayar` (`Periode_Tagihan` atau kombinasi `Bulan_Berlaku` & `Tahun_Ajaran_Berlaku`) jika laporan dirinci per periode.                                 | `Juli 2025`                   | Periode tagihan yang relevan.                                                                                                            |
| `Total_Sudah_Dibayar`      | Angka             | Hasil agregasi (`SUMIFS` atau `QUERY`) dari `Input Pembayaran` (`Jumlah_Bayar`), dijumlahkan berdasarkan `ID_Santri` (dan `Jenis_Tagihan_Deskripsi`/`Periode_Tagihan` jika dirinci).  | `500000`                      | Akumulasi total pembayaran yang telah diterima dari santri untuk tagihan/periode tersebut.                                                |
| `Harus Bayar`      | Angka             | Hasil agregasi (`SUMIFS` atau `QUERY`) dari `Data Harus Dibayar` (`Jumlah_Bayar`)  | `500000`                      | Akumulasi total pembayaran yang telah diterima dari santri untuk tagihan/periode tersebut.                                                |
| `Sisa Tagihan`           | Angka             | Hasil kalkulasi: `Nominal_Kewajiban` - `Total_Sudah_Dibayar`.                                                                                                                        | `0`                           | Selisih antara yang harus dibayar dengan yang sudah dibayar. Nilai positif berarti tunggakan, nol berarti lunas, negatif berarti kelebihan bayar. |

**Struktur Laporan:**
Sheet ini bisa memiliki beberapa format tampilan:
1.  **Ringkasan per Santri**: Sheet ini menunjukkan data per santri untuk melihat  total kewajiban, total bayar, dan total sisa tunggakan secara keseluruhan (tidak dirinci per jenis tagihan).
2.  **Detail per Tagihan per Santri**: Beberapa baris per santri, di mana setiap baris menunjukkan status satu jenis tagihan spesifik (misalnya, SPP Juli, Uang Pangkal, Ekskul).

## 3. Cara Menggunakan Sheet Ini (Sebagai Pembaca Laporan)

Sebagai pengguna yang melihat laporan di sheet ini:
1.  **Buka Sheet**: Akses sheet `Data Bayar Per Santri`.
2.  **Amati Data**: Lihat informasi yang disajikan.
3.  **Masukkan Nama Lengkap Santri**

**PENTING: JANGAN MENGEDIT APAPUN SECARA LANGSUNG DI SHEET INI.** Karena sheet ini otomatis, setiap perubahan manual yang Anda lakukan akan hilang atau menyebabkan error ketika formula di dalamnya menghitung ulang data. Perubahan data harus dilakukan pada sheet sumbernya.

## 4. Keterkaitan dengan Sheet Lain (Sumber Data)

Sheet `Data Bayar Per Santri` sangat bergantung pada sheet-sheet berikut sebagai sumber datanya:

* **`Input Pembayaran` (KRUSIAL)**:
    * Menyediakan data `ID_Santri`, `Jumlah_Bayar`, `Tanggal_Bayar`, dan `ID_Tagihan_Dibayar` yang menjadi dasar utama semua kalkulasi pembayaran.
* **`Database Santri` (KRUSIAL)**:
    * Menyediakan data `ID_Santri`, `Nama_Lengkap_Santri`, `Kelas`, dan atribut santri lainnya yang ditampilkan sebagai informasi deskriptif.
* **`Jumlah Harus Dibayar` (KRUSIAL)**:
    * Menyediakan data `ID_Tagihan`, `Deskripsi_Tagihan`, `Nominal_Tagihan`, `Periode_Tagihan` yang menjadi dasar untuk menentukan kewajiban setiap santri. Logika di sheet `Data Bayar Per Santri` akan mencocokkan santri dengan tagihan yang berlaku untuknya.

Kualitas dan akurasi data di sheet `Data Bayar Per Santri` sepenuhnya bergantung pada kualitas dan akurasi data yang diinput pada sheet-sheet sumber di atas.

---

[Kembali ke Daftar Isi Utama](../README.md)

[Sebelumnya - Database Santri](../docs/Database_Santri.md) | 
[Selanjutnya - Input Pengeluaran](../docs/Input_Pengeluaran.md)
