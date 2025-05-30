# Dokumentasi Sheet: Input Pengeluaran

## 1. Tujuan Sheet

Sheet `Input Pengeluaran` digunakan untuk **mencatat semua transaksi pengeluaran** yang dilakukan oleh PONPES by Sheetizen. Setiap baris mewakili satu transaksi pengeluaran. Pencatatan yang akurat dan detail di sheet ini penting untuk pelaporan biaya operasional, analisis pengeluaran, dan penyusunan laporan keuangan ponpes secara keseluruhan.

## 2. Struktur Kolom dan Panduan Pengisian

Berikut adalah perkiraan detail untuk setiap kolom dalam sheet `Input Pengeluaran`.

| Nama Kolom                      | Tipe Data         | Wajib Diisi? | Contoh Isi                                | Keterangan                                                                                                                               |
|---------------------------------|-------------------|--------------|-------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| `Nomor`      | Angka (Urut) | **OTOMATIS** | `01` (Otomatis)              | Nomor (angka urut).                             |
| `Tanggal (M)`           | Tanggal Masehi           | **YA** | `29/05/2025` (format DD/MM/YYYY)          | Tanggal ketika pengeluaran dilakukan atau dicatat.                                                                                         |
| `Tanggal (H)`           | Tanggal Hijriah           | **OTOMATIS** | `1 Dzulhijjah 1446 H`          | Tanggal ketika pengeluaran dilakukan atau dicatat.                                                                                         |
| `Keterangan`          | Teks     | **YA** | `Gaji Guru Dzulhijjah 1446H` | Keterangan pengeluaran.                            |
| `Nominal`            | Angka             | **YA** | `250000`                                  | Nominal yang dikeluarkan (dalam Rupiah, tanpa titik atau koma).                                                                            |
| `Kategori Pengeluaran`          | Teks (Pilihan)    | **YA** | `Gaji Guru` | Jenis atau kelompok pengeluaran. Menggunakan Data Validation dari sheet `SETUP`.                                       |
| `Sumber Dana`      | Teks (Pilihan)    | **YA**        | `Syahriyah Makan`| Sumber dana dari `Input Pembayaran`|
| `Aset Asal`      | Teks (Pilihan)    | **YA**        | `Bank Jago`| Aset asal dari `Input Pembayaran`|
| `Aset Tujuan`      | Teks (Pilihan)    | **YA**        | `Bank Jago`| Aset tujuan, khusus untuk jenis pengeluaran `PINDAH ASET`|
| `Status WA`      | Emoji    | **OTOMATIS**        | `📧`| Status WA sudah dikirim. Jika WA belum dikirim , tidak ada emoji.|

**Catatan Penting:**
* **`Jumlah_Pengeluaran`**: Masukkan angka saja.
* Isi bagian yang berwarna abu-abu. Kolom berwarna putih akan otomatis terisi. 

## 3. Cara Mengisi Sheet Ini

1.  Setiap kali ada pengeluaran yang dilakukan oleh ponpes:
    * Tambahkan baris baru di sheet `Input Pengeluaran`.
    * Isi `Tanggal (M)`.
    * Masukkan `Keterangan Pengeluaran`.
    * Masukkan `Nominal`.
    * Pilih `Kategori Pengeluaran` yang paling sesuai.
    * Pilih `Sumber Dana`.
    * Pilih `Aset Asal`
    * `Status WA` akan terisi otomatis setelah kirim WA notif pengeluaran.

## 4. Kirim WA Pengeluaran ke Pimpinan

Setelah yakin data sudah sesuai, Anda dapat mengirim pengeluu (dalam bentuk PDF) dan otomatis mengirim ke WA Wali/orang tua santri. Ada 3 cara untuk mencetak kuitansi.
* [Cetak Berdasarkan Baris yang Dipilih](#cetak-berdasarkan-baris-yang-dipilih)
* [Cetak Berdasarkan Tanggal](#cetak-berdasarkan-tanggal)

### Cetak Berdasarkan Baris yang Dipilih
1. Tandai Baris yang dipilih, disarankan maksimal 10 baris agar scriptnya berjalan dengan optimal. Untuk akun Google Script yang gratis sekali menjalankan script maksimal 6 menit, jika lebih dari itu, tidak akan diproses. Jadi, gunakan maksimal 10 baris saja.
2. Klik menu `Laporan & Kuitansi`
3. Pilih `Laporan Pengeluaran`
4. Pilih `Kirim Rincian WA - Baris Terpilih`
5. Otomatis akan kirim WA ke nomor pimpian (di sheet `SETUP WA` jika belum ada status kirim WA.
6. Jika sudah ada emoji 📧, tidak akan diproses. Hal ini untuk menghindari dobel kirim WA.

### Cetak Berdasarkan Tanggal
1. Copy tanggal yang ingin dicetak (hanya bisa satu tanggal kuitansi per jalankan script). Contoh tanggal `28/05/2025` dibaca 28 Mei 2025.
2. Klik menu `Laporan & Kuitansi`
3. Pilih `Laporan Pengeluaran`
4. Pilih `Kirim Rincian WA - Per Tanggal`
5. Otomatis akan kirim WA ke nomor pimpinan jika belum ada status cetak.
6. Jika sudah ada emoji 📧, tidak akan diproses. Hal ini untuk menghindari dobel kirim WA.

## 5. Keterkaitan dengan Sheet Lain

* **`Dashboard`**: Sheet ini adalah **sumber data utama** untuk analisis pengeluaran di `Dashboard` (misalnya, total pengeluaran, pengeluaran per kategori, aset).

---

[Kembali ke Daftar Isi Utama](../README.md)

[Sebelumnya - Input Pembayaran](../docs/Input_Pembayaran.md) |
[Selanjutnya - Data Bayar Per Santri](../docs/Data_Bayar_Per_Santri.md) | 
