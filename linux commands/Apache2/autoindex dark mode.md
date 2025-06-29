Ya, tampilan **autoindex** di Apache2 bisa diubah agar memiliki **background hitam dan teks putih** (dark mode) — tapi tidak secara langsung lewat konfigurasi Apache. Perlu sedikit trik karena autoindex secara default menggunakan gaya HTML sederhana yang di-*generate* otomatis oleh `mod_autoindex`. Cara melakukannya:

---

### 🔧 **Menggunakan `HeaderName` untuk Menambahkan CSS Sendiri**

Apache memungkinkan kita menyisipkan **file header HTML** ke bagian atas direktori listing melalui opsi `HeaderName`.

#### Langkah-langkah:

1. **Aktifkan `mod_autoindex` dan `mod_headers`**
   Biasanya sudah aktif. Kalau belum:

   ```bash
   sudo a2enmod autoindex
   sudo a2enmod headers
   sudo systemctl restart apache2
   ```

2. **Buat file bernama `HEADER.html` di direktori tersebut**, misalnya:

   ```html
   <style>
   body {
       background-color: #000;
       color: #fff;
   }
   a { color: #9cf; }
   </style>
   ```

3. **Buat/ubah `.htaccess` di direktori itu:**

   ```apache
   Options +Indexes
   HeaderName HEADER.html
   ```

   atau jika langsung dari virtual host:

   ```apache
   <Directory /var/www/html/yourdir>
       Options +Indexes
       HeaderName HEADER.html
   </Directory>
   ```

**Hasilnya**: halaman autoindex akan memuat HTML tambahan dari `HEADER.html` yang bisa menginjeksi CSS seperti `dark mode`.
