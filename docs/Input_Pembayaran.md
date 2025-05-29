# Dokumentasi Sheet: Input Pembayaran

## 1. Tujuan Sheet

Sheet `Input Pembayaran` adalah sheet transaksional utama yang digunakan untuk **mencatat setiap detail transaksi pembayaran yang diterima** dari santri atau wali santri. Setiap baris mewakili satu transaksi pembayaran. Data di sheet ini menjadi sumber utama untuk laporan penerimaan kas dan pelacakan status pembayaran santri.

## 2. Struktur Kolom dan Panduan Pengisian

Berikut adalah perkiraan detail untuk setiap kolom dalam sheet `Input Pembayaran`.

| Nama Kolom                    | Tipe Data         | Wajib Diisi? | Contoh Isi                                  | Keterangan                                                                                                                                           |
|-------------------------------|-------------------|--------------|---------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Nomor`                       | Angka (otomatis) | **OTOMATIS** | `01`                | Nomor Urut Input Pembayaran|
| `Tanggal (M)`                 | Tanggal          | **YA** | `28/05/2025` (format DD/MM/YYYY)            | Tanggal Masehi ketika pembayaran diterima/dicatat.                                                                                                          |
| `Tanggal (H)`                 | Tanggal           | **OTOMATIS** | `1 Dzulhijjah 1446H`            | Tanggal Hijriah ketika pembayaran diterima/dicatat.                                                                                                          |
| `Nama_Santri`                 | Teks              | **YA** | `Muhammad Al Fatih`                         | Nama santri, ketik satu huruf, akan otomatis muncul karena ditarik otomatis dari `Database Santri` menggunakan `DATA VALIDASI`.           |
| `Kelas`                       | Teks/Angka        | **OTOMATIS** | `7`                                  | Kelas santri, ditarik otomatis dari `Database Santri` menggunakan `VLOOKUP` atau `XLOOKUP` berdasarkan `Nama Santri` untuk verifikasi.  |
| `Keterangan`                  | Teks              | **YA** | `Pembayaran SPP Dzulhijjah 1446H` | Penjelasan untuk pembayaran apa. keterangan ini dicetak di `Kuitansi Pembayaran` dan `Notifikasi WA Pembayaran ke Wali/Ortu Santri` .            |
| `Kategori`                    | Teks (Pilihan)            | **YA** | `Syahriyah Makan` | Pembayaran yang sudah disetting di sheet `SETUP`            |
| `Nominal`                     | Angka             | **YA** | `500000`                                    | Nominal yang dibayarkan (dalam Rupiah, tanpa titik atau koma).                                                                                         |
| `Metode Bayar`                | Teks (Pilihan)    | **YA** | `Tunai`, `Transfer Bank A`, `QRIS`, `Virtual Account` | Cara pembayaran yang digunakan. Menggunakan Data Validation dari sheet `SETUP`.                                                                                  |
| `Nomor Kuitansi`              | Teks              | **OTOMATIS**        | `KWI/280525/001`                              | Nomor kuitansi otomatis generate dari tanggal dan transaksi ke berapa di hari itu.                                                                                             |
| `Status Cetak`                | Teks (Emoji)       | **OTOMATIS**        | `✅`                            | Emoji otomatis jika sudah dicetak versi PDF.                                                                                    |
| `Status WA`                   | Teks (Emoji)       | **OTOMATIS**        | `📧`                            | Emoji otomatis jika sudah kirim WA.                                                                                    |

**Catatan Penting:**
* **`ID_Transaksi_Pembayaran`**: Pastikan unik. Jika diisi manual, buatlah sistem penomoran yang konsisten (misalnya, `TRXP` + TahunBulanTanggal + NomorUrut).
* **`ID_Santri`**: Harus valid dan ada di sheet `Database Santri`. Gunakan Data Validation dengan sumber dari kolom `ID_Santri` di `Database Santri` untuk menghindari kesalahan input.
* **`ID_Tagihan_Dibayar`**: Sangat disarankan untuk diisi agar pembayaran dapat dialokasikan ke tagihan yang benar. Gunakan Data Validation dari `ID_Tagihan` di `Jumlah Harus Dibayar`.
* **`Jumlah_Bayar`**: Masukkan angka saja.
* **Kolom Otomatis**: `Nama_Santri` dan mungkin sebagian `Deskripsi_Pembayaran` dapat diisi otomatis dengan formula jika `ID_Santri` dan `ID_Tagihan_Dibayar` diinput dengan benar. Ini mengurangi kesalahan input manual.

## 3. Cara Mengisi Sheet Ini

1.  Setiap kali ada pembayaran yang diterima:
    * Tambahkan baris baru di sheet `Input Pembayaran`.
    * Isi `ID_Transaksi_Pembayaran` (jika manual) atau biarkan terisi (jika otomatis).
    * Masukkan `Tanggal_Bayar`.
    * Masukkan `ID_Santri` yang melakukan pembayaran. Pastikan `Nama_Santri` yang muncul (jika otomatis) sudah benar.
    * Pilih `ID_Tagihan_Dibayar` yang sesuai (jika ada). Pastikan `Deskripsi_Pembayaran` yang muncul (jika otomatis) atau yang Anda input manual sudah benar.
    * Masukkan `Jumlah_Bayar` yang diterima.
    * Pilih `Metode_Pembayaran`.
    * Isi kolom `Bank_Pengirim` dan `Nama_Pengirim` jika pembayaran via transfer untuk memudahkan rekonsiliasi.
    * Catat `Bukti_Bayar_Ref` jika ada.
    * Masukkan nama `Petugas_Penerima`.
    * Update `Status_Verifikasi_Pembayaran` jika diperlukan.
    * Tambahkan `Keterangan_Lain` jika ada info tambahan.
2.  Lakukan pengecekan ulang data yang diinput sebelum beralih ke transaksi berikutnya.

## 4. Keterkaitan dengan Sheet Lain

* **`Database Santri`**: Mengambil `ID_Santri` sebagai referensi utama. Data santri lain (nama, kelas) bisa ditampilkan dari sini.
* **`Jumlah Harus Dibayar`**: Mengambil `ID_Tagihan` sebagai referensi jenis tagihan. Detail tagihan (deskripsi, nominal standar) bisa ditampilkan dari sini.
* **`Data Bayar Per Santri`**: Sheet ini adalah **sumber data utama** untuk sheet `Data Bayar Per Santri`. Data pembayaran diagregasi per santri di sheet tersebut.
* **`Dashboard`**: Total penerimaan, penerimaan per metode bayar, dll., di `Dashboard` berasal dari agregasi data di sheet ini.
* **`SETUP WA`**: Data dari sini (`Nama_Santri`, `Deskripsi_Pembayaran`, `Jumlah_Bayar`, `Tanggal_Bayar`) digunakan untuk mengisi template notifikasi pembayaran via WhatsApp.
* **`Template_Kuitansi`**: Data dari sheet ini akan digunakan untuk mengisi detail pada kuitansi yang akan dicetak.

---
[Kembali ke Daftar Isi Utama](../README.md)
