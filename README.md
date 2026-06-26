# AksaraLoka - Platform E-Commerce Multi-Vendor

AksaraLoka merupakan sebuah sistem informasi berbasis *web* yang mengimplementasikan model *e-commerce multi-vendor* (marketplace). Perangkat lunak ini dirancang untuk memfasilitasi aktivitas perdagangan secara digital dengan mengintegrasikan proses jual beli dari berbagai penjual independen ke dalam satu *platform* yang terpusat. 

Aplikasi ini dikembangkan untuk mengotomatisasi alur transaksi, mulai dari pemilihan barang melalui sistem keranjang belanja (*shopping cart*), proses konfirmasi pemesanan (*checkout*), hingga penyediaan manajemen toko yang terstruktur bagi para pelaku UMKM.

**🌐 Live Deployment:** [http://kelas-c-2.informatika-unjedir.web.id](http://kelas-c-2.informatika-unjedir.web.id)

<div align="center">
  <h3>👥 Anggota Kelompok:</h3>
  <p><strong>Ali Muhammad Firdaus</strong> - H1D024102</p>
  <p><strong>Aditya Alfandy</strong> - H1D024103</p>
  <p><strong>Yakfi 'Arofah Yuhdika Muftiady</strong> - H1D024114</p>
  <p><strong>Farrel Wildan Widodo</strong> - H1D024045</p>
</div>

---

## 🏗 Tech Stack & Deployment

Proyek ini menggunakan spesifikasi modern dengan fondasi:
* **Bahasa Pemrograman:** PHP 8.3+, ES6+
* **Framework Backend:** Laravel 13.x
* **Frontend:** Tailwind CSS 3.1.x & Alpine.js 3.4.x (Blade Templating Engine)
* **Autentikasi:** Laravel Breeze
* **Ekspor Laporan:** Barryvdh/laravel-dompdf (PDF Export)
* **Database:** MySQL
* **Deployment / Hosting:** Virtual Private Server (VPS) dengan HestiaCP (Nginx/Apache)

---

## 🚀 Fitur Utama

1. **Katalog & Detail Produk:** Antarmuka utama untuk mengeksplorasi daftar produk lengkap dengan detail dan harga.
2. **Keranjang Belanja (Shopping Cart):** Sistem keranjang sementara (*session-based*) untuk menampung pesanan sebelum *checkout*.
3. **Proses Checkout & Split Order:** Alur utama untuk pemesanan barang, dilengkapi fitur memecah tagihan otomatis (Split Order) jika membeli barang dari banyak toko.
4. **Dasbor Penjual (Seller Dashboard):** Panel khusus bagi mitra penjual untuk melihat ringkasan performa toko harian/bulanan.
5. **Manajemen Produk Toko (CRUD):** Fasilitas bagi penjual untuk menambah, mengubah, dan menghapus etalase produk mereka.
6. **Manajemen Pesanan (Order Tracking):** Fitur untuk memperbarui dan memantau status pesanan (menunggu, diproses, dikirim, selesai).
7. **Ekspor Laporan Penjualan (PDF):** Kemampuan untuk mencetak dan mengunduh riwayat rekapitulasi data pendapatan toko ke format PDF.
8. **Dasbor Administrator (Admin Panel):** Pusat kendali super admin untuk memonitor lalu lintas transaksi, mengelola kategori, dan hak akses pengguna.

---

## 🗄️ Struktur Database (Tabel Utama)

Aplikasi ini menggunakan basis data relasional (MySQL) dengan tabel-tabel inti sebagai berikut:
- `users` : Menyimpan data autentikasi dan status hak akses (role: admin, penjual, pembeli).
- `stores` : Menyimpan profil UMKM/toko yang dimiliki oleh pengguna penjual.
- `categories` : Menyimpan master data klasifikasi kategori produk.
- `products` : Menyimpan informasi detail barang dagangan yang terikat pada suatu toko.
- `product_images` : Menyimpan kumpulan galeri foto untuk masing-masing produk (*One-to-Many*).
- `orders` : Menyimpan rekaman transaksi utama (faktur tagihan dan status pesanan).
- `order_items` : Menyimpan rincian spesifik barang (kuantitas dan harga satuan) di dalam pesanan.
- `wishlists` : Menyimpan data produk favorit yang ditandai oleh pembeli.

---

## 📋 Persyaratan Sistem (Prerequisites)

Sebelum melakukan instalasi, pastikan komputer Anda telah terinstal perangkat lunak berikut:
- **PHP** (versi 8.3 atau lebih baru)
- **Composer** (untuk manajemen dependensi PHP)
- **Node.js & NPM** (untuk *build* aset *frontend* Tailwind & Vite)
- **MySQL Server** (bisa menggunakan XAMPP, Laragon, atau Laravel Herd)
- **Git** (untuk *clone* repositori)

---

## ⚙️ Petunjuk Instalasi Step-by-Step

Agar aplikasi berjalan pada lingkungan lokal Anda, ikuti langkah-langkah berikut:

1. **Clone repositori dari GitHub:**
   ```bash
   git clone https://github.com/cattlevya/Aksaralokaa.git
   cd Aksaralokaa
   ```

2. **Instal seluruh dependencies Composer dan NPM:**
   ```bash
   composer install
   npm install && npm run build
   ```

3. **Konfigurasi Environment Database:**
   Copy `.env.example` menjadi `.env`.
   ```bash
   cp .env.example .env
   ```
   Lalu buka file `.env`, atur koneksi spesifikasi *database* Anda sesuai environment lokal.

4. **Buat Application Key:**
   ```bash
   php artisan key:generate
   ```

5. **Link direktori Storage untuk gambar (SANGAT PENTING):**
   ```bash
   php artisan storage:link
   ```

6. **Migrasi Database sekaligus Populasikan (Seed) Master Data:**
   Langkah ini wajib untuk melengkapi katalog dan struktur role akun awal. *(Pastikan aplikasi MySQL server seperti XAMPP atau Laravel Herd Anda sudah berjalan).*
   ```bash
   php artisan migrate:fresh --seed
   ```

7. **Jalankan Aplikasi:**
   ```bash
   php artisan serve
   ```
   Buka terminal baru dan jalankan Vite untuk aset Frontend:
   ```bash
   npm run dev
   ```
   Akses `http://localhost:8000` melalui browser Anda.

---

## 🔑 Kredensial Pengujian (Seeder Default)

Proses *seeding* secara otomatis akan menciptakan data dummy dan 4 akun siap pakai dengan *password* default `password`:

| Role | Nama / Instansi | Email Login | Password |
| :--- | :--- | :--- | :--- |
| **Admin** | Admin AksaraLoka | `admin@aksaraloka.id` | `password` |
| **Penjual (Toko 1)** | Siti Rahayu | `siti@aksaraloka.id` | `password` |
| **Penjual (Toko 2)** | Bambang Wijaya | `bambang@aksaraloka.id` | `password` |
| **Pembeli** | Rina Susanti | `rina@email.com` | `password` |

Gunakan akses tersebut di `/login` untuk mencoba masing-masing fitur dasbor sesuai *role*.