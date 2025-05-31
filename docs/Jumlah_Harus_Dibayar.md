# Dokumentasi Sheet: Jumlah Harus Dibayar

## 1. Tujuan Sheet

Sheet `Jumlah Harus Dibayar` berfungsi sebagai **master data untuk semua jenis tagihan atau iuran** yang berlaku di PONPES by Sheetizen. Sheet ini merinci deskripsi, nominal, dan periode setiap jenis pembayaran yang menjadi kewajiban santri. Ini menjadi dasar untuk menentukan berapa besar tagihan yang harus dibayar oleh santri.

## 2. Struktur Kolom dan Panduan Pengisian

Berikut adalah detail untuk setiap kolom dalam sheet `Jumlah Harus Dibayar`.

| Nama Kolom                | Tipe Data         | Wajib Diisi? | Contoh Isi                                | Keterangan                                                                                                                                  |
|---------------------------|-------------------|--------------|-------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| `Nama Bulan Masehi`              | Teks       | **YA** | `Januari`, `Februari`, ..., `Desember` | Bulan dalam Masehi. |
| `Nama Bulan Hijriah`       | Teks              | **YA** | `Muharram`, `Safar`, ..., `Dzulhijjah` | Bulan dalam Hijriah.                                                                                               |
| `Bulanan`        | Teks (Otomatis)    | **OTOMATIS** | `Syahriyah Makan`, `Syahriyah Pendidikan`	`Ianah Syahriyah` | Pengelompokan jenis tagihan BULANAN. Tagihan ini diambil dari sheet `SETUP`.                                                                          |
| `Tahunan`         | Teks (Otomatis)             | **OTOMATIS** | `LKS`, `Uang Gedung`                                  | Pengelompokkan jenis tagihan TAHUNAN. Tagihan ini diambil dari sheet `SETUP`.                                                    |
| `Insidental`         | Teks (Otomatis)    | **OTOMATIS** | `Uang Duka`, `Uang Transportasi` | Pengelompokkan jenis tagihan INSIDENTAL. Tagihan ini diambil dari sheet `SETUP`                                                                          |
| `TOTAL TAGIHAN`     | Angka (Otomatis)              | **OTOMATIS**        | `Rp14.350.000` | Total Tagihan adalah jumlah tagihan yang harus dibayar selama satu tahun.                             |

**Catatan Penting:**
* Semua data di sheet ini terisi otomatis.
* Tidak perlu mengubah apapun.
* Sheet ini berubah ketika mengubah nama santri di sheet `Data Bayar Per Santri`


---
[Kembali ke Daftar Isi Utama](../README.md)

[Sebelumnya - SETUP WA](../docs/SETUP_WA.md) | 
[Selanjutnya - Input Pembayaran](../docs/Input_Pembayaran.md)
