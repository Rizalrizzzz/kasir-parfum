# Aplikasi Kasir Parfum

Aplikasi ini dirancang untuk memudahkan proses transaksi penjualan di toko parfum, mulai dari transaksi, rekap barang, penambahan barang, pengelolaan stok, pengelolaan supplier barang dan pencetakan struk.

## Daftar Isi

- Tujuan Aplikasi
- Fitur Utama
- Teknologi yang Digunakan
- Struktur File Aplikasi
- Struktur Database
- Alur Kerja Penggunaan Aplikasi
- Contoh Data
- Validasi & Penanganan Error
- Cara Menggunakan Aplikasi
- Pengembang

## Tujuan Aplikasi

1. Mempermudah proses penjualan parfum di toko.
2. Mengelola stok parfum secara akurat berdasarkan transaksi dan pemasokan barang.
3. Menyimpan data penjualan harian, mingguan, atau bulanan untuk keperluan laporan.
4. Menyediakan sistem login kasir agar penggunaan sistem lebih aman dan terkontrol.
5. Mengelola data supplier dan riwayat barang masuk.

## Fitur Utama

Aplikasi kasir parfum ini dilengkapi dengan berbagai fitur untuk mendukung operasional toko parfum:

1. Sistem Login:
   - Autentikasi login pengguna menggunakan username dan password.
2. Koneksi Database:
   - Menggunakan MySQL untuk menyimpan semua data transaksi, stok, supplier, dan user login.
3. Dashboard:
   - Menampilkan total parfum terjual, total parfum, dan total supplier
4. Manajemen Transaksi:
   - Memasukkan nama pembeli, kode parfum, jumlah botol, dan otomatis menghitung total harga.
   - Menyimpan riwayat transaksi ke dalam database.
   - Mencatat detail seperti uang pembeli dan kembalian.
   - Mencetak struk pembelian.
5. Rekap Penjualan:
   - Menampilkan seluruh riwayat transaksi yang tersimpan di database.
   - Dapat digunakan sebagai laporan penjualan.
6. Manajemen Parfum:
   - Menampilkan daftar parfum dengan kode, nama, harga per ml, dan stok.
   - Menambah data parfum baru ke sistem.
   - Mengedit atau menghapus data parfum.
7. Pemasokan Barang (Barang Masuk):
   - Mencatat data parfum yang masuk dari supplier.
   - Mencatat tanggal, nama supplier, kode parfum, dan jumlah stok yang ditambahkan.
8. Supplier:
   - Menambahkan dan menyimpan data supplier ke dalam sistem.
   - Menampilkan daftar supplier lengkap dengan nama, no hp, dan alamat.
9. Logout:
   - Keluar dari aplikasi.

## Teknologi yang Digunakan

- Bahasa Pemrograman: Java Swing
- IDE: NetBeans IDE
- Database: MySQL
- Server: XAMPP (untuk menjalankan Apache dan MySQL)

## Struktur File Aplikasi

File |Fungsi
MenuDataParfum.java |Menampilkan dan mengelola daftar parfum yang tersedia.
MenuSeller.java |Menambahkan stok parfum yang diterima dari supplier.
Menu Transaksi.java |Modul untuk mencatat transaksi penjualan.
CariProduk.java |Untuk mencari produk yang digunakan untuk class MenuTransaksi.java dan class MenuSeller.java
Menu Rekap.java |Menampilkan riwayat transaksi dan laporan penjualan.
Login.java |Halaman login pengguna aplikasi.
KoneksiDatabase.java|Mengatur koneksi ke database MySQL.
Main.java |Entry point aplikasi (main program).
MenuDataSuplier.java|Menampilkan dan mengelola daftar supplier.
MenuDashboard.java |Menampilkan total parfum terjual, total parfum, dan total supplier.
Struk.jrxml |Mencetak dan menampilkan struk yang di gunakan untuk class MenuTransaksi.java.

## Struktur Database

Database db_parfum terdiri dari tabel-tabel berikut:

- barang_parfum: Menyimpan data parfum (kode, nama, harga, stok).
- barang_masuk: Mencatat stok masuk dari supplier (relasi ke barang_parfum dan data_supplier).
- rekap_penjualan: Menyimpan detail transaksi (dengan uang pelanggan & kembalian).
- tabel_transaksi: Menyimpan ringkasan transaksi yang terjadi.
- data_supplier: Menyimpan data supplier (nama, no HP, alamat).
- user_login: Untuk autentikasi pengguna.
  Relasi antar tabel:
- barang_masuk.kode_parfum > barang_parfum.kode_parfum
- barang_masuk.nama_supplier > data_supplier.nama_supplier
- rekap_penjualan.kode_parfum > barang_parfum.kode_parfum
- tabel_transaksi.kode_parfum > barang_parfum.kode_parfum

## Validasi error

- Aplikasi memeriksa:
  - Apakah stok cukup sebelum transaksi.
  - Apakah data parfum/supplier sudah ada sebelum digunakan.
  - Input numerik seperti harga, jumlah, dan uang tidak boleh kosong.
- Saat koneksi ke database gagal, aplikasi akan menampilkan dialog peringatan.
- Username/password salah akan ditolak oleh sistem login.
