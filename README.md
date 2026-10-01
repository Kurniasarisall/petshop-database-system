# [Pet Shop Relational Database System]
Informatika - UPN Veteran Yogyakarta

Anggota Kelompok:
- Mukhlizardy Al Fauzan	 (123180041)
- Taura Kaka Arissa 		 (123230207)
- Andhiko Sakti 		     (123230228)
- Bagoes Lanang Cahya 	 (123230231)
- Kurniasari Salasa		   (123230236)


Proyek perancangan dan implementasi basis data relasional berbasis MySQL untuk kebutuhan operasional toko hewan peliharaan (Pet Shop). Sistem ini dirancang untuk mengelola entitas master (produk, kasir, pembeli) serta mencatat riwayat transaksi secara terintegrasi.

---

## Gambaran Umum
Sistem ini memodelkan proses bisnis ritel pet shop mulai dari pendataan stok pakan dan aksesoris hewan, data kasir bertugas, data pelanggan, hingga pencatatan struk transaksi pembelian.

- **Database Engine:** MySQL / MariaDB (InnoDB)
- **Platform Pengujian:** phpMyAdmin
- **Normalisasi:** Memenuhi kriteria 3NF (Third Normal Form) untuk mencegah anomali data dan meminimalkan redundansi.

---

## Berkas Skrip SQL (Source Code)

Di dalam repositori ini, kode SQL dipecah secara modular menjadi tiga bagian utama agar mudah diuji dan dipelajari:

1. **`schema.sql` (Data Definition Language / DDL)**
   * Berisi instruksi inisialisasi basis data `pet_shop` beserta definisi 4 tabel utama: `kasir`, `pembeli`, `produk`, dan tabel relasi `pembelian`.
   * Mengatur tipe data atribut, *Primary Key* (PK), serta pendefinisian aturan relasi *Foreign Key* (FK) dengan klausa `ON DELETE CASCADE` dan `ON UPDATE CASCADE` untuk menjamin integritas referensial data antar-tabel.

2. **`dummy_data.sql` (Data Manipulation Language / DML - Seeding)**
   * Berisi dataset awal untuk pengujian operasional basis data yang mencakup data master pegawai kasir, pelanggan/pembeli, variasi produk pet shop, dan histori transaksi pembelian.
   * Diimpor setelah `schema.sql` dieksekusi agar tabel memiliki data realistis sebelum dilakukan pengujian kueri.

3. **`queries.sql` (Data Query Language / DQL - Business Insights)**
   * Kumpulan kueri analitikal SQL untuk menghasilkan laporan operasional toko:
     * **Multi-table JOIN:** Menggabungkan 4 tabel sekaligus (`pembelian`, `pembeli`, `produk`, `kasir`) untuk mencetak rekap transaksi lengkap per struk belanja.
     * **Agregasi Kasir (`COUNT`, `SUM`, `GROUP BY`):** Menghitung total omset pendapatan toko dan performa volume transaksi yang dilayani oleh masing-masing kasir.
     * **Analisis Produk Terlaris:** Menghitung frekuensi pembelian per item produk untuk mengetahui produk yang paling diminati pembeli.

---

## Struktur Entitas & Relasi Tabel (RAT)
Sistem memiliki 4 entitas utama yang saling terhubung:

1. **`kasir`** (Master Data Kasir)
   * `ID_Kasir` (PK), `Nama_Kasir`, `Tanggal_Lahir`, `Email_kasir`
2. **`pembeli`** (Master Data Pelanggan)
   * `ID_Pembeli` (PK), `Nama_Pembeli`, `Alamat_Pembeli`, `Email_Pembeli`
3. **`produk`** (Master Data Barang & Layanan)
   * `ID_Produk` (PK), `Nama_Produk`, `Jenis_Produk`, `Ukuran`, `Harga`
4. **`pembelian`** (Tabel Transaksi / Junction Table)
   * `ID_Pembelian` (PK)
   * Relasi Foreign Key: `ID_Kasir` (FK), `ID_Pembeli` (FK), `ID_Produk` (FK)

---

## Cara Import Database
1. Buka **phpMyAdmin** (`http://localhost/phpmyadmin`).
2. Buat database baru dengan nama `pet_shop`.
3. Masuk ke tab **Import**, pilih file `schema.sql` (atau file dump `.sql`), lalu klik **Go / Kirim**.
4. Seluruh tabel beserta sampel data dan relasi foreign key siap digunakan.
