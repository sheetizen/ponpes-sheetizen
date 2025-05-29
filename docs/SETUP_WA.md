# Dokumentasi Sheet: SETUP WA

## 1. Tujuan Sheet

Sheet `SETUP WA` bertujuan untuk menyimpan semua parameter konfigurasi yang berkaitan dengan integrasi sistem notifikasi WhatsApp (WA). Pengaturan ini akan digunakan jika sistem Spreadsheet ini dihubungkan dengan layanan eksternal atau skrip untuk mengirim pesan WhatsApp otomatis (misalnya, notifikasi pembayaran, pengingat tagihan).

**Penting**: Fungsi ini akan bekerja dengan skrip Google Apps Script. Script akan membaca konfigurasi ini dan berinteraksi dengan API WhatsApp (FONNTE).

## 2. Struktur Kolom dan Panduan Pengisian

Berikut adalah detail setiap kolom dalam sheet `SETUP WA`.

| Nama Kolom         | Tipe Data      | Wajib Diisi?                | Contoh Isi                                                                       | Keterangan                                                                                                                              |
|--------------------|----------------|-----------------------------|----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| `Parameter_WA`     | Teks           | **YA** | `API_KEY_WA_GATEWAY`                                                             | Label atau deskripsi dari item konfigurasi WhatsApp.                                                                                     |
| `Nilai_Parameter`  | Teks           | **YA (jika fitur aktif)** | `abcdef123456xyz789`                                                             | Nilai aktual dari item konfigurasi WhatsApp.                                                                                             |
| `Deskripsi_Fungsi` | Teks           | Tidak                       | `Kunci API untuk layanan WhatsApp Gateway XYZ`                                     | Penjelasan fungsi dari parameter tersebut.                                                                                              |

**Contoh Baris Data Pengaturan WA:**

| Parameter_WA                        | Nilai_Parameter                                                                                             | Deskripsi_Fungsi                                                               |
|-------------------------------------|-------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| `API atau Token Fonnte`            | `abcdef123456xyz789`                                                                                              | Kunci API dari penyedia layanan WhatsApp Gateway (jika menggunakan).                       |
| `Aktifkan Kirim WA`                | `YA` / `TIDAK` (checkbox)                                                                                        | Mengaktifkan atau menonaktifkan fitur notifikasi WA.              |
| `Nama Pengirim di WA`                 | `PONPES SHEETIZEN`                                                                                            | Nama Ponpes sebagai pengirim pesan.                 |
| `Footer Tambahan di WA`           | `Dikirim pada 1 Dzulhijjah 1446 H`                                                                            | Bagian akhir chat WA yang dikirim ke wali atau ortu santri.                        |
| `Nomor WhatsApp Notif Pengeluaran`    | `62822xxxxxx` | Nomor WA yang menerima notifikasi `PENGELUARAN`. |

**Catatan Penting:**
* Setiap baris mewakili satu item konfigurasi WhatsApp.
* Jika Anda tidak menggunakan fitur notifikasi WhatsApp, sheet ini bisa dikosongkan atau diisi dengan nilai `AKTIFKAN_NOTIFIKASI_WA` = `TIDAK` (matikan checkbox).

## 3. Keterkaitan dengan Sheet atau Script Lain

* **`Input Pengeluaran`**: `Nomor WA Notif Pengeluaran`: akan digunakan untuk mengirim detail pengeluaran ke pimpinan ponpes.
* **`Nama Pengirim di WA` dan `Footer Tambahan WA`**: akan digunakan sebagai detail informasi di notif WA cetak kuitansi kirim ke wali atau orang tua santri.

---
[Kembali ke Daftar Isi Utama](../README.md)
