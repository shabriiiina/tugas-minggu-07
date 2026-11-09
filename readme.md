# Dokumentasi Tugas Minggu 07 - Halaman Registrasi Pengguna dengan Database MySQL

Proyek ini merupakan pengembangan dari Tugas Minggu 06, di mana sistem penyimpanan sementara berbasis `$_SESSION` digantikan dengan penyimpanan permanen menggunakan **Database MySQL**.

## Struktur File Proyek

- `index.php` : File utama yang berisi logika pemrosesan form, validasi server-side, integrasi PDO MySQL, serta antarmuka HTML/CSS/JS.
- `schema.sql` : Script DDL SQL untuk membuat database `db_tugas07` dan tabel `users`.
- `readme.md` : Dokumentasi penulisan code dan penjelasan aplikasi.

## Fitur Utama & Pembaruan

1. **Penyimpanan Permanen (MySQL)**:
   - Penggunaan ekstensi **PDO (PHP Data Objects)** untuk koneksi database.
   - Menggunakan **Prepared Statements** (`$pdo->prepare()`) pada seluruh eksekusi query untuk mencegah ancaman **SQL Injection**.

2. **Validasi Formulir (Server-Side & Client-Side)**:
   - **Nama Lengkap**: Minimal 3 karakter.
   - **Email**: Harus sesuai format email dan unik di tabel `users`.
   - **Username**: Format `[a-zA-Z0-9_]{4,20}` dan unik di tabel `users`.
   - **Password**: Minimal 8 karakter, wajib dicocokkan dengan konfirmasi password.
   - **Preservasi Form**: Nilai input sebelumnya tidak terhapus jika terdapat kesalahan server-side.

3. **Keamanan Aplikasi**:
   - **Enkripsi Password**: Menggunakan `password_hash()` dengan algoritma Bcrypt standar PHP.
   - **XSS Protection**: Menggunakan fungsi helper `htmlspecialchars()` untuk menyaring output yang ditampilkan ke browser.
   - **CSRF Protection**: Menggunakan token anti-CSRF yang divalidasi dengan `hash_equals()`.

## Petunjuk Penggunaan

1. **Pengaturan Database**:
   - Impor file `schema.sql` ke dalam MySQL Server lokal (misalnya menggunakan phpMyAdmin).
2. **Konfigurasi Koneksi**:
   - Buka file `index.php`, sesuaikan variabel `$user` dan `$pass` sesuai kredensial web server lokal Anda.
3. **Pengujian**:
   - Akses `index.php` melalui browser (`http://localhost/tugas07/index.php`).
   - Coba lakukan registrasi data baru, pengubahan data (*edit*), serta pengujian validasi unik untuk email dan username.