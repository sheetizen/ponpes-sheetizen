# Dokumentasi Sheet: Dashboard

## 1. Tujuan Sheet

Sheet `Dashboard` dalam sistem Spreadsheet PONPES by Sheetizen adalah antarmuka visual utama yang dirancang untuk menyajikan **ringkasan pemasukan, pengeluaran, saldo/aset, jumlah tagihan yang seharusnya dibayar oleh seluruh santri setiap bulannya**. Tujuannya adalah untuk memberikan pemahaman yang cepat dan mudah dicerna mengenai kondisi terkini, yang vital untuk pemantauan, analisis, dan pengambilan keputusan oleh pimpinan, bendahara, atau staf administrasi.

**PENTING: Sheet `Dashboard` yang Anda lihat dan gunakan di aplikasi Spreadsheet sepenuhnya OTOMATIS.** Semua angka, tabel ringkas, dan grafik yang ditampilkan adalah hasil dari formula Spreadsheet dan fitur charting yang secara dinamis mengambil dan mengolah data dari sheet-sheet sumber lainnya (seperti `Input Pembayaran`, `Input Pengeluaran`.). **Tidak ada proses input data manual yang dilakukan langsung di area visual Dashboard.**

## 2. Komponen Umum yang Disajikan di Dashboard PONPES by Sheetizen

Dashboard visual di aplikasi PONPES by Sheetizen terdiri dari berbagai elemen berikut.

### A. Ringkasan Keuangan Utama
Disajikan angka-angka penting yang mudah terlihat, seringkali dengan indikator tren untuk periode yang dipilih dari sel B5 (awal periode), C5 (akhir periode).

* **Total Pemasukan:**
    - Menampilkan keseluruhan dana yang diterima ponpes selama periode yang dipilih. Angka ini merupakan hasil penjumlahan dari kolom `Nominal` pada sheet `Input Pembayaran` untuk periode relevan dan berfungsi sebagai indikator utama kesehatan aliran kas masuk ponpes.
    - Menampilkan realisasi PEMASUKAN setiap kategori.

* **Total Pengeluaran:**
    - Menunjukkan jumlah total dana yang dikeluarkan oleh ponpes selama periode yang dipilih. Nilai ini adalah hasil penjumlahan dari kolom `Nominal` pada sheet `Input Pengeluaran` untuk periode yang sama.
    - Menampilkan realisasi PENGELUARAN setiap kategorinya.

* **Total Aset**
    - Merupakan selisih antara `Total Pemasukan` dan `Total Pengeluaran` untuk periode yang dipilih. Nilai positif menandakan surplus (penerimaan lebih besar dari pengeluaran), sedangkan nilai negatif menunjukkan defisit.
    - Menampilkan realisasi aset di periode yang dipilih.

* **Persentase Realisasi Anggaran (Jika sistem anggaran digunakan):**
    Menyajikan perbandingan antara realisasi penerimaan atau pengeluaran aktual terhadap target anggaran yang telah ditetapkan untuk periode tertentu. Dihitung dengan formula (`Realisasi Aktual` / `Nilai Anggaran`) * 100%, yang datanya memerlukan sheet anggaran terpisah sebagai sumber. Indikator ini penting untuk menilai sejauh mana pencapaian target anggaran.

### B. Rincian Pembayaran Santri
Menyajikan ringkasan data yang berasal dari analisis lebih detail di sheet `Input Pembayaran`.

* **Jumlah Santri:**
    Menampilkan jumlah total santri yang saat ini terdaftar dan berstatus aktif di ponpes. Angka ini dihitung dari sheet `Database Santri`.

* **Total Tagihan Bulan Ini:**
    Total tagihan yang harus dibayar oleh seluruh santri pada periode yang dipilih.

* **Sudah Dibayar:**
    Menunjukkan jumlah total dana yang sudah dibayarkan oleh semua santri secara kumulatif dalam rentang periode  dipilih.

* **Belum Dibayar:**
    Menunjukkan jumlah total dana yang masih belum dibayarkan oleh semua santri secara kumulatif dalam rentang periode dipilih. Angka ini merupakan hasil penjumlahan (`SUM`) dari kolom `Input Pembayaran` (yang bernilai positif) di sheet `Data Bayar Per Santri`, yang menggambarkan besaran piutang ponpes dari para santri.

### C. Fitur Interaktif pada Dashboard Visual
* **Filter Periode:** Pilihan untuk mengubah rentang tanggal data yang ditampilkan.

## **CATATAN PENTING***
* **Amati Informasi yang Tersaji**: Lihat angka-angka utama, grafik, dan tabel untuk mendapatkan gambaran umum kondisi keuangan dan operasional.
* **Perhatikan Periode Data yang Ditampilkan**: Perhatikan periode waktu untuk memastikan Anda menginterpretasikan data dengan benar.
* **JANGAN UBAH DATA SECARA MANUAL**: Ingat, Dashboard adalah tampilan hasil. Jika ada data yang perlu dikoreksi, lakukan perubahan pada sheet sumbernya (misalnya, `Input Pembayaran`, dan `Input Pengeluaran` jika ada kesalahan input transaksi). Perubahan manual pada Dashboard visual akan tertimpa saat data diperbarui, atau bisa merusak formula.

## Keterkaitan dengan Sheet Lain (Sebagai Sumber Data Utama)

Keakuratan dan kelengkapan Dashboard visual **sepenuhnya bergantung** pada kualitas data di sheet-sheet berikut:

* **`Input Pembayaran`**: Menyediakan data mentah untuk semua analisis penerimaan.
* **`Input Pengeluaran`**: Menyediakan data mentah untuk semua analisis pengeluaran.
* **`Database Santri`**: Menyediakan data jumlah santri dan atribut lainnya untuk konteks.
* **`SETUP`**: Menyediakan informasi kontekstual umum (Jumlah Santri, Kategori Pemasukan, Kategori Pengeluaran, dan Aset) yang ditampilkan.

Jika data di sheet-sheet sumber ini akurat dan terisi dengan baik, maka Dashboard akan menyajikan informasi yang andal dan bermanfaat untuk pengambilan keputusan.

---
[Kembali ke Daftar Isi Utama](../README.md)

[Sebelumnya - Dashboard](../docs/Dashboard.md) | 
[Selanjutnya - Template Kuitansi](../docs/Template_Kuitansi.md)
