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
| `Jumlah_Pengeluaran`            | Angka             | **YA** | `250000`                                  | Nominal yang dikeluarkan (dalam Rupiah, tanpa titik atau koma).                                                                            |

| `Keterangan`          | Teks     | **YA** | `Gaji Guru Dzulhijjah 1446H` | Keterangan pengeluaran.                            |
| `Kategori Pengeluaran`          | Teks (Pilihan)    | **YA** | `Gaji Guru` | Jenis atau kelompok pengeluaran. Menggunakan Data Validation dari sheet `SETUP`.                                       |
| `Sub_Kategori_Pengeluaran`      | Teks (Pilihan)    | Tidak        | `ATK`, `Listrik`, `Air`, `Internet`, `Gaji Guru Tetap`, `Honor Ustadz Tamu` | Detail lebih lanjut dari `Kategori_Pengeluaran` (jika diperlukan). Sebaiknya terkait dengan Kategori Pengeluaran yang dipilih.             |
| `Deskripsi_Pengeluaran`         | Teks              | **YA** | `Pembelian kertas HVS A4 10 rim`, `Pembayaran Tagihan Listrik Mei 2025`, `Honorarium Ustadz Fulan - Kajian Subuh` | Penjelasan detail mengenai pengeluaran tersebut. Semakin detail semakin baik.                                                            |
| `Metode_Pembayaran_Keluar`      | Teks (Pilihan)    | **YA** | `Tunai Kas Besar`, `Transfer Bank A`, `Kas Kecil Bendahara` | Cara pembayaran yang dilakukan oleh ponpes. Sebaiknya gunakan Data Validation.                                                             |
| `Penerima_Pembayaran_Vendor`    | Teks              | Tidak        | `Toko ATK Barokah`, `PLN Persero`, `Ustadz Fulan` | Nama toko, vendor, atau individu yang menerima pembayaran dari ponpes.                                                                  |
| `Nomor_Referensi_Bukti`         | Teks              | Tidak        | `Nota00789`, `INV/2025/V/123`, `Kuitansi Honor` | Nomor nota, kuitansi, invoice, atau referensi lain dari bukti pengeluaran. Penting untuk arsip dan audit.                                   |
| `Diajukan_Oleh (Jika Ada)`      | Teks              | Tidak        | `Kepala Bagian Sarpras`                   | Nama pihak internal yang mengajukan atau bertanggung jawab atas pengeluaran (jika ada alur persetujuan).                                      |
| `Disetujui_Oleh (Jika Ada)`     | Teks              | Tidak        | `Bendahara Umum`                          | Nama pihak yang menyetujui pengeluaran (jika ada alur persetujuan).                                                                          |
| `Dicatat_Oleh`                  | Teks              | **YA** | `Staf Keuangan Ani`                       | Nama petugas ponpes yang mencatat transaksi pengeluaran ini.                                                                               |
| `Akun_Biaya_Terkait`            | Teks              | Tidak        | `5-1001 Biaya ATK`, `5-2001 Biaya Listrik` | Kode akun akuntansi terkait jika sistem ini terintegrasi dengan pencatatan akuntansi (opsional).                                             |
| `Catatan_Tambahan_Pengeluaran`  | Teks Panjang      | Tidak        | `Pembelian untuk kebutuhan ujian semester`  | Informasi tambahan lain yang relevan mengenai transaksi pengeluaran.                                                                     |

**Catatan Penting:**
* **`ID_Transaksi_Pengeluaran`**: Pastikan unik. Jika diisi manual, buatlah sistem penomoran yang konsisten (misalnya, `EXP` + TahunBulanTanggal + NomorUrut).
* **`Kategori_Pengeluaran`**: Penggunaan Data Validation sangat disarankan untuk memudahkan analisis pengeluaran per kategori.
* **`Jumlah_Pengeluaran`**: Masukkan angka saja.
* **Bukti Transaksi**: Meskipun hanya mencatat `Nomor_Referensi_Bukti`, pastikan bukti fisik atau digitalnya diarsipkan dengan baik.

## 3. Cara Mengisi Sheet Ini

1.  Setiap kali ada pengeluaran yang dilakukan oleh ponpes:
    * Tambahkan baris baru di sheet `Input Pengeluaran`.
    * Isi `ID_Transaksi_Pengeluaran` (jika manual).
    * Masukkan `Tanggal_Pengeluaran`.
    * Pilih `Kategori_Pengeluaran` yang paling sesuai. Isi `Sub_Kategori_Pengeluaran` jika perlu.
    * Tulis `Deskripsi_Pengeluaran` secara jelas dan lengkap.
    * Masukkan `Jumlah_Pengeluaran`.
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
