Untuk menghilangkan tulisan "Apache/2.X.X.X (Debian) Server at XXX.XXX.X.XX Port XXX" yang muncul pada halaman *autoindex* Apache di Debian, Anda dapat mengikuti langkah-langkah berikut:

1. **Edit file konfigurasi Apache:**
   Buka file konfigurasi Apache utama atau file konfigurasi virtual host yang digunakan untuk situs Anda. Biasanya file konfigurasi berada di `/etc/apache2/apache2.conf` atau di dalam direktori `/etc/apache2/sites-available/`.
   ```
   sudo nano /etc/apache2/apache2.conf
   ```

2. **Matikan `ServerTokens` dan `ServerSignature`:**
   Untuk menghilangkan informasi server (seperti "Apache/2.X.X.X (Debian)"), pastikan bahwa direktif `ServerTokens` dan `ServerSignature` diatur dengan benar.
   - Pastikan bahwa `ServerTokens` diatur ke `Prod` untuk menyembunyikan informasi versi Apache dan sistem operasi.
   - Atur `ServerSignature` ke `Off` untuk mematikan tanda tangan server di halaman error atau autoindex.
   Tambahkan atau pastikan baris-baris berikut ada di file `apache2.conf` atau dalam file konfigurasi virtual host:
   ```apache
   ServerTokens Prod
   ServerSignature Off
   ```

3. **Restart Apache:**
   Setelah melakukan perubahan, pastikan untuk me-restart Apache agar perubahan konfigurasi diterapkan:
   ```
   sudo systemctl restart apache2
   ```

Setelah itu, tulisan "Apache/2.X.X.X (Debian) Server at XXX.XXX.X.XX Port XXX" seharusnya tidak lagi muncul pada halaman *autoindex*.
