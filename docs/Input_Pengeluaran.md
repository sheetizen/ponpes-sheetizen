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
| `Status WA`      | Emoji    | **OTOMATIS**        | `emoji`| Status WA sudah dikirim. Jika WA belum dikirim , tidak ada emoji.|

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
    * Pilih `Metode_Pembayaran_Keluar`.
    * Catat `Penerima_Pembayaran_Vendor` dan `Nomor_Referensi_Bukti`.
    * Isi kolom `Diajukan_Oleh` dan `Disetujui_Oleh` jika alur tersebut berlaku.
    * Masukkan nama `Dicatat_Oleh`.
    * Tambahkan `Catatan_Tambahan_Pengeluaran` jika ada.
2.  Simpan semua bukti pengeluaran (nota, kuitansi, invoice) secara terorganisir, idealnya dengan mencantumkan `ID_Transaksi_Pengeluaran` pada bukti fisiknya untuk kemudahan pencarian.

## 4. Keterkaitan dengan Sheet Lain

* **`Dashboard`**: Sheet ini adalah **sumber data utama** untuk analisis pengeluaran di `Dashboard` (misalnya, total pengeluaran, pengeluaran per kategori, perbandingan pengeluaran dengan anggaran jika ada).
* **Laporan Keuangan**: Data dari sheet ini akan menjadi komponen penting dalam penyusunan Laporan Laba Rugi (jika dibuat), khususnya pada bagian Biaya/Beban.
* **Analisis Anggaran**: Jika ada sheet anggaran, data pengeluaran aktual dari sini dapat dibandingkan dengan anggaran yang telah ditetapkan.

---
[Kembali ke Daftar Isi Utama](../README.md)
