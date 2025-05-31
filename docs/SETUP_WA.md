# Dokumentasi Sheet: SETUP GOOGLE APPS SCRIPT DAN SETUP WA

## 1. Tujuan Sheet

Sheet `SETUP WA` bertujuan untuk menyimpan semua parameter konfigurasi yang berkaitan dengan integrasi sistem notifikasi WhatsApp (WA). Pengaturan ini akan digunakan jika sistem Spreadsheet ini dihubungkan dengan layanan eksternal atau skrip untuk mengirim pesan WhatsApp otomatis (misalnya, notifikasi pembayaran, pengingat tagihan).

**Penting**: Fungsi ini akan bekerja dengan skrip Google Apps Script. Script akan membaca konfigurasi ini dan berinteraksi dengan API WhatsApp (FONNTE).

## 2. Struktur Kolom dan Panduan Pengisian

Berikut adalah **Contoh Baris Data Pengaturan WA:** di sheet `SETUP WA`. 

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

* **`Nomor WA Notif Pengeluaran`**: akan digunakan untuk mengirim detail pengeluaran ke pimpinan ponpes.
* **`Nama Pengirim di WA` dan `Footer Tambahan WA`**: akan digunakan sebagai detail informasi di notif WA cetak kuitansi kirim ke wali atau orang tua santri.

# Panduan Akses dan Memberikan Izin (Otorisasi) Google Apps Script

Google Apps Script adalah platform pengembangan berbasis JavaScript yang memungkinkan Anda membuat aplikasi bisnis yang terintegrasi dengan layanan Google Workspace seperti Sheets, Docs, Forms, Gmail, dll. Dalam file PONPES by Sheetizen, Anda menggunakan fitur otomatisasi kustom (misalnya, pembuatan kuitansi otomatis dalam bentuk PDF, pengiriman kuitansi pembayaran via WhatsApp ke wali/ortu santri, pengiriman laporan keuangan ke pimpinan, dan menu kustom).

Bagian ini menjelaskan cara mengakses editor skrip dan proses pemberian izin (otorisasi) yang biasanya diperlukan saat pertama kali skrip dijalankan atau saat ada pembaruan yang memerlukan izin baru.

## 1. Mengakses Editor Google Apps Script dari Google Sheets

Ikuti langkah-langkah berikut ini

1.  **Buka File Google Sheets**: Buka file Spreadsheet PONPES by Sheetizen di Google Sheets.
2.  **Akses Editor Skrip**:
    * Pada menu bar di bagian atas, klik **"Ekstensi"** (atau **"Tools"** dalam versi bahasa Inggris lama, lalu **"Script editor"**).
    * Pilih **"Apps Script"**.
3.  Sebuah tab atau jendela baru akan terbuka, menampilkan **Editor Google Apps Script**. Di sinilah kode skrip yang mengontrol otomatisasi Spreadsheet Anda berada. Anda akan melihat 5 file dengan ekstensi `.gs` (`Konversi Hijriah.gs`, `Kuitansi PDF.gs`, `Kuitansi WA.gs`, `WA Pengeluaran.gs`, `Rangkum Pengeluaran.gs`).

## 2. Menjalankan Fungsi Skrip dan Proses Otorisasi

Saat Anda (atau pengguna lain yang memiliki akses edit ke Spreadsheet) pertama kali menjalankan fungsi dari skrip yang memerlukan akses ke data Anda atau layanan Google lainnya, Anda akan diminta untuk memberikan izin.

**Kapan Otorisasi Diperlukan?**
* Saat pertama kali menjalankan fungsi apa pun dari skrip tersebut.
* Jika Anda membuat pemicu (trigger) otomatis untuk skrip.

**Langkah-langkah Umum Proses Otorisasi:**

1.  **Menjalankan Fungsi Skrip:**
    * Ini bisa terjadi melalui beberapa cara:
        * **Menu Kustom:** Skrip di sini akan menambahkan menu kustom di antarmuka Google Sheets (menu "Laporan & Kuitansi" > "Kuitansi Pembayaran"), mengklik salah satu opsi menu tersebut akan menjalankan fungsi terkait.
        * **Langsung dari Editor Skrip:** Anda dapat memilih fungsi tertentu dari dropdown di atas area kode di editor Apps Script dan mengklik tombol "Jalankan" (ikon ▶️).
        * 
2.  **Jendela "Authorization Required" (Izin Diperlukan):**
    * Saat skrip memerlukan izin, sebuah dialog akan muncul dengan pesan seperti **"Authorization Required"** atau **"Izin Diperlukan"**.
    * Klik **"Continue"** atau **"Lanjutkan"**.
    
3.  **Pilih Akun Google:**
    * Anda akan diminta untuk memilih akun Google yang ingin Anda gunakan untuk memberikan izin. **Pilih akun Google yang Anda gunakan untuk mengakses Spreadsheet PONPES by Sheetizen tersebut.**
    
4.  **Peringatan "Google hasn’t verified this app" (Google belum memverifikasi aplikasi ini) - JIKA MUNCUL:**
    * Peringatan ini sering muncul untuk skrip yang dibuat secara internal dan belum diajukan untuk verifikasi oleh Google (proses yang biasanya untuk add-on publik). **Ini adalah hal yang normal untuk skrip internal.**
    * Untuk melanjutkan:
        * Klik **"Advanced"** atau **"Lanjutan"** (biasanya berupa tautan kecil di bagian bawah).
        * Kemudian, klik **"Go to Konversi Hijriah (unsafe)"** atau **"Buka Konversi Hijriah (tidak aman)"**. .
          
5.  **Tinjau Izin yang Diminta (Review Permissions):**
    * Sebuah layar akan muncul yang merinci izin apa saja yang diminta oleh skrip.
      
6.  **Berikan Izin:**
    * Gulir atau scroll ke bawah lalu klik tombol **"Allow"** atau **"Izinkan"**.
    
7.  **Otorisasi Selesai:**
    * Setelah Anda mengklik "Allow", proses otorisasi selesai. Fungsi skrip yang Anda coba jalankan akan dilanjutkan.
    * Anda biasanya hanya perlu melakukan proses otorisasi ini sekali untuk setiap cakupan izin baru.

## 3. Mencabut Izin Aplikasi (Jika Diperlukan)

Jika Anda ingin meninjau atau mencabut izin yang telah diberikan kepada skrip atau aplikasi lain yang terhubung ke Akun Google Anda:

1.  Buka halaman **Keamanan Akun Google Anda**: [https://myaccount.google.com/security](https://myaccount.google.com/security)
2.  Gulir ke bawah ke bagian **"Aplikasi pihak ketiga dengan akses akun"** (atau "Third-party apps with account access").
3.  Klik **"Kelola akses pihak ketiga"** (atau "Manage third-party access").
4.  Anda akan melihat daftar semua aplikasi dan skrip yang memiliki akses ke akun Anda. Klik pada nama skrip/proyek yang ingin Anda tinjau atau cabut izinnya.
5.  Klik tombol **"HAPUS AKSES"** (atau "REMOVE ACCESS").

**Catatan:** Mencabut izin akan menyebabkan skrip tidak lagi dapat berfungsi sampai Anda memberikan izin kembali melalui proses otorisasi seperti di atas.

## 4. Tips Keamanan dan Praktik Terbaik

* **Jangan Bagikan Spreadsheet dengan Skrip Sensitif kepada Pihak yang Tidak Berwenang:**

Dengan mengikuti proses ini, Anda dapat dengan aman menggunakan fitur-fitur otomatisasi yang ada di Spreadsheet PONPES by Sheetizen.


---
[Kembali ke Daftar Isi Utama](../README.md)

[Sebelumnya - Setup](../docs/SETUP.md) | 
[Selanjutnya - Jumlah Harus Dibayar](../docs/Jumlah_Harus_Dibayar.md)
