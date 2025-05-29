# Dokumentasi Sheet: SETUP WA

## 1. Tujuan Sheet

Sheet `SETUP WA` bertujuan untuk menyimpan semua parameter konfigurasi yang berkaitan dengan integrasi sistem notifikasi WhatsApp (WA). Pengaturan ini akan digunakan jika sistem Spreadsheet ini dihubungkan dengan layanan eksternal atau skrip untuk mengirim pesan WhatsApp otomatis (misalnya, notifikasi pembayaran, pengingat tagihan).

**Penting**: Fungsi ini akan bekerja dengan skrip Google Apps Script. Script akan membaca konfigurasi ini dan berinteraksi dengan API WhatsApp (FONNTE).

## 2. Struktur Kolom dan Panduan Pengisian

Berikut adalah perkiraan detail untuk setiap kolom dalam sheet `SETUP WA`.

| Nama Kolom         | Tipe Data      | Wajib Diisi?                | Contoh Isi                                                                       | Keterangan                                                                                                                              |
|--------------------|----------------|-----------------------------|----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| `Parameter_WA`     | Teks           | **YA** | `API_KEY_WA_GATEWAY`                                                             | Label atau deskripsi dari item konfigurasi WhatsApp.                                                                                     |
| `Nilai_Parameter`  | Teks           | **YA (jika fitur aktif)** | `abcdef123456xyz789`                                                             | Nilai aktual dari item konfigurasi WhatsApp.                                                                                             |
| `Deskripsi_Fungsi` | Teks           | Tidak                       | `Kunci API untuk layanan WhatsApp Gateway XYZ`                                     | Penjelasan fungsi dari parameter tersebut.                                                                                              |

**Contoh Baris Data Pengaturan WA:**

| Parameter_WA                        | Nilai_Parameter                                                                                             | Deskripsi_Fungsi                                                               |
|-------------------------------------|-------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| `AKTIFKAN_NOTIFIKASI_WA`            | `YA` / `TIDAK`                                                                                              | Mengaktifkan atau menonaktifkan semua fitur notifikasi WA.                       |
| `API_KEY_WA_GATEWAY`                | `abcdef123456xyz789`                                                                                        | Kunci API dari penyedia layanan WhatsApp Gateway (jika menggunakan).              |
| `NOMOR_WA_PENGIRIM`                 | `+6281200000000`                                                                                            | Nomor WhatsApp yang terdaftar di Gateway sebagai pengirim pesan.                 |
| `URL_ENDPOINT_WA_GATEWAY`           | `https://api.wagateway.com/send`                                                                            | URL endpoint API untuk mengirim pesan dari layanan Gateway.                        |
| `TEMPLATE_NOTIFIKASI_PEMBAYARAN`    | `Terima kasih Bpk/Ibu Wali Santri {NAMA_SANTRI}, pembayaran {DESKRIPSI_PEMBAYARAN} sejumlah Rp {JUMLAH_BAYAR} pada {TANGGAL_BAYAR} telah kami terima. Salam, Bendahara PONPES YOGS VERSE.` | Template pesan untuk notifikasi pembayaran berhasil. Gunakan placeholder seperti `{NAMA_SANTRI}`. |
| `TEMPLATE_PENGINGAT_TAGIHAN`        | `Yth. Wali Santri {NAMA_SANTRI}, kami mengingatkan tagihan {DESKRIPSI_TAGIHAN} sejumlah Rp {JUMLAH_TAGIHAN} akan jatuh tempo pada {TANGGAL_JATUH_TEMPO}. Mohon segera melakukan pembayaran. Terima kasih.` | Template pesan untuk pengingat tagihan.                                        |
| `TEMPLATE_INFO_UMUM`                | `Pengumuman dari PONPES YOGS VERSE: {ISI_PENGUMUMAN}`                                                         | Template untuk pengumuman umum.                                                  |
| `TARGET_NOTIFIKASI_ADMIN`           | `+6281211112222`                                                                                            | Nomor WA admin/bendahara untuk menerima notifikasi internal (jika ada).         |

**Catatan Penting:**
* Setiap baris mewakili satu item konfigurasi WhatsApp.
* Placeholder seperti `{NAMA_SANTRI}`, `{JUMLAH_BAYAR}`, `{TANGGAL_BAYAR}` dalam template pesan akan digantikan dengan data aktual oleh skrip/layanan pengirim WA. Pastikan nama placeholder konsisten dengan data yang tersedia di sheet lain.
* Jika Anda tidak menggunakan fitur notifikasi WhatsApp, sheet ini bisa dikosongkan atau diisi dengan nilai `AKTIFKAN_NOTIFIKASI_WA` = `TIDAK`.

## 3. Cara Mengisi Sheet Ini

1.  Jika Anda berencana menggunakan notifikasi WhatsApp, tentukan parameter apa saja yang dibutuhkan oleh skrip atau layanan WhatsApp Gateway Anda.
2.  Isi kolom `Parameter_WA` dengan nama parameter yang dikenali oleh sistem WA Anda.
3.  Isi kolom `Nilai_Parameter` dengan data yang sesuai (misalnya, API Key, nomor telepon, template pesan).
4.  Gunakan placeholder yang logis dalam template pesan Anda yang bisa diisi dari data di sheet `Database Santri`, `Input Pembayaran`, atau `Jumlah Harus Dibayar`.
5.  Pastikan parameter `AKTIFKAN_NOTIFIKASI_WA` (atau sejenisnya) diatur ke `YA` jika ingin fitur ini berjalan.

## 4. Keterkaitan dengan Sheet Lain

* **`Database Santri`**: `No_HP_Wali` dan `Nama_Santri` akan digunakan untuk personalisasi pesan WA.
* **`Input Pembayaran`**: Data seperti `Jumlah_Bayar`, `Tanggal_Bayar`, `Deskripsi_Pembayaran` akan digunakan untuk mengisi template notifikasi pembayaran.
* **`Jumlah Harus Dibayar`**: Data seperti `Deskripsi_Tagihan`, `Nominal_Tagihan` bisa digunakan untuk pengingat tagihan.
* **Skrip/Layanan Eksternal**: Sheet ini secara krusial dibaca oleh skrip atau layanan eksternal yang bertugas mengirim pesan WhatsApp.

---
[Kembali ke Daftar Isi Utama](../README.md)
