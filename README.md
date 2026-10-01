# [Pet Shop Relational Database System]
Informatika - UPN Veteran Yogyakarta

Anggota Kelompok:
Mukhlizardy Al Fauzan	 (123180041)
Taura Kaka Arissa 		 (123230207)
Andhiko Sakti 		     (123230228)
Bagoes Lanang Cahya 	 (123230231)
Kurniasari Salasa		   (123230236)


Proyek perancangan dan implementasi basis data relasional berbasis MySQL untuk kebutuhan operasional toko hewan peliharaan (Pet Shop). Sistem ini dirancang untuk mengelola entitas master (produk, kasir, pembeli) serta mencatat riwayat transaksi secara terintegrasi.

---

## Gambaran Umum
Sistem ini memodelkan proses bisnis ritel pet shop mulai dari pendataan stok pakan dan aksesoris hewan, data kasir bertugas, data pelanggan, hingga pencatatan struk transaksi pembelian.

- **Database Engine:** MySQL / MariaDB (InnoDB)[cite: 11]
- **Platform Pengujian:** phpMyAdmin[cite: 11, 13]
- **Normalisasi:** Memenuhi kriteria 3NF (Third Normal Form) untuk mencegah anomali data dan meminimalkan redundansi.

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
