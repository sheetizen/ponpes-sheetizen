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
* **CUKUP ISI KOLOM ATAU SEL YANG BERWARNA ABU-ABU**
* **KOLOM BERWARNA PUTIH OTOMATIS TERISI**
* **JANGAN HAPUS FORMULA DI SEL WARNA PUTIH**
* **`Jumlah_Bayar`**: Masukkan angka saja.

## 3. Cara Mengisi Sheet Ini

1.  Setiap kali ada pembayaran yang diterima:
    * Tambahkan baris baru di sheet `Input Pembayaran`.
    * Masukkan `Tanggal_Bayar`.
    * Masukkan `Nama Santri` yang melakukan pembayaran. Pastikan `Kelas` yang muncul (jika otomatis) sudah benar.
    * Pilih `Kategori` yang sesuai.
    * Masukkan `Nominal` yang diterima.
    * Pilih `Metode Pembayaran`.
    * Cek `Nomor Kuitansi` (otomatis).
2.  Lakukan pengecekan ulang data yang diinput sebelum beralih ke transaksi berikutnya.

## 4. Cetak Kuitansi dan Kirim WA Pembayaran

Setelah yakin data sudah sesuai, Anda dapat mencetak kuitansi (dalam bentuk PDF) dan otomatis mengirim ke WA Wali/orang tua santri. Ada 3 cara untuk mencetak kuitansi.
* [Cetak Berdasarkan Baris yang Dipilih](#cetak-berdasarkan-baris-yang-dipilih)
* [Cetak Berdasarkan Nomor Kuitansi](#cetak-berdasarkan-nomor-kuitansi)
* [Cetak Berdasarkan Tanggal](#cetak-berdasarkan-tanggal)

### Cetak Berdasarkan Baris yang Dipilih
1. Tandai Baris yang dipilih, disarankan maksimal 10 baris agar scriptnya berjalan dengan optimal. Untuk akun Google Script yang gratis sekali menjalankan script maksimal 6 menit, jika lebih dari itu, tidak akan diproses. Jadi, gunakan maksimal 10 baris saja.
2. Klik menu `Laporan & Kuitansi`
3. Pilih `Kuitansi Pembayaran`
4. Pilih `Cetak & Kirim WA (Belum Proses) - Baris Terpilih`
5. Otomatis akan mencetak PDF dan kirim WA ke nomor wali/ortu santri jika belum ada status cetak.
6. Jika sudah ada emoji ✅	atau 📧, tidak akan diproses. Hal ini untuk menghindari dobel kuitansi atau kirim WA.


### Cetak Berdasarkan Nomor Kuitansi
1. Copy nomor kuitansi yang ingin dicetak (hanya bisa satu nomor kuitansi per jalankan script). Contoh nomor kuitansi `KWI/280525/001`
2. Klik menu `Laporan & Kuitansi`
3. Pilih `Kuitansi Pembayaran`
4. Pilih `Cetak & Kirim WA berdasarkan nomor jika Belum Diproses`
5. Otomatis akan mencetak PDF dan kirim WA ke nomor wali/ortu santri jika belum ada status cetak.
6. Jika sudah ada emoji ✅	atau 📧, tidak akan diproses. Hal ini untuk menghindari dobel kuitansi atau kirim WA.


### Cetak Berdasarkan Tanggal
1. Copy tanggal yang ingin dicetak (hanya bisa satu nomor kuitansi per jalankan script). Contoh nomor kuitansi `28/05/2025` dibaca 28 Mei 2025.
2. Klik menu `Laporan & Kuitansi`
3. Pilih `Kuitansi Pembayaran`
4. Pilih `Cetak & Kirim WA berdasarkan tanggal jika Belum Diproses`
5. Otomatis akan mencetak PDF dan kirim WA ke nomor wali/ortu santri jika belum ada status cetak.
6. Jika sudah ada emoji ✅	atau 📧, tidak akan diproses. Hal ini untuk menghindari dobel kuitansi atau kirim WA.

## 5. Keterkaitan dengan Sheet Lain

* **`Database Santri`**: Mengambil `Nama Santri` sebagai referensi utama. Data santri lain (kelas) bisa ditampilkan dari sini.
* **`Jumlah Harus Dibayar`**: Mengambil `Kategori` sebagai referensi jenis tagihan. Detail tagihan (deskripsi, nominal standar) bisa ditampilkan dari sini.
* **`Data Bayar Per Santri`**: Sheet ini adalah **sumber data utama** untuk sheet `Data Bayar Per Santri`. Data pembayaran disinkronisasi per santri di sheet tersebut.
* **`Dashboard`**: Total penerimaan, penerimaan per metode bayar, dll., di `Dashboard` berasal dari sinkronisasi data di sheet ini.
* **`SETUP WA`**: Data dari sini (`Nama_Santri`, `Deskripsi_Pembayaran`, `Jumlah_Bayar`, `Tanggal_Bayar`) digunakan untuk mengisi template notifikasi pembayaran via WhatsApp.
* **`Template_Kuitansi`**: Data dari sheet ini akan digunakan untuk mengisi detail pada kuitansi yang akan dicetak.

---
---

[Kembali ke Daftar Isi Utama](../README.md)

[Sebelumnya - Database Santri](../docs/Database_Santri.md) | 
[Selanjutnya - Input Pengeluaran](../docs/Input_Pengeluaran.md)
