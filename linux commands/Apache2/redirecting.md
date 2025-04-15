Kalau kamu ingin menggunakan **Apache** untuk membuat IP lokal mengarahkan ke link lain, kamu bisa mengatur konfigurasi VirtualHost atau menggunakan `.htaccess`. Berikut caranya:

---

### **1. Redirect Menggunakan VirtualHost**  
Kamu bisa mengatur VirtualHost di Apache agar IP lokal (misalnya `192.168.1.100`) mengarahkan ke link lain.

#### **Langkah-langkahnya:**
1. **Buka file konfigurasi Apache** (biasanya ada di `/etc/apache2/sites-available/000-default.conf` di Debian/Ubuntu atau `/etc/httpd/conf/httpd.conf` di CentOS).
2. **Tambahkan konfigurasi berikut:**
   
   ```apache
   <VirtualHost *:80>
       ServerName 192.168.1.100
       Redirect 301 / https://www.example.com
   </VirtualHost>
   ```

3. **Simpan dan restart Apache:**
   ```bash
   sudo systemctl restart apache2  # Debian/Ubuntu
   sudo systemctl restart httpd    # CentOS/RHEL
   ```

Sekarang, setiap kali ada yang mengakses `http://192.168.1.100`, mereka akan langsung dialihkan ke `https://www.example.com`.

---

### **2. Redirect Menggunakan .htaccess**
Jika kamu tidak bisa mengedit konfigurasi Apache, bisa pakai `.htaccess` di dalam direktori `DocumentRoot` (misalnya di `/var/www/html/.htaccess`):

```apache
Redirect 301 / https://www.example.com
```

Pastikan modul **mod_rewrite** aktif dengan perintah:

```bash
sudo a2enmod rewrite
sudo systemctl restart apache2
```

---

### **3. Redirect dengan mod_rewrite (Lebih Fleksibel)**
Jika ingin aturan lebih kompleks, gunakan **mod_rewrite** di `.htaccess`:

```apache
RewriteEngine On
RewriteCond %{HTTP_HOST} ^192\.168\.1\.100$
RewriteRule ^(.*)$ https://www.example.com/$1 [R=301,L]
```

Ini memastikan hanya permintaan ke `192.168.1.100` yang diarahkan ke `https://www.example.com`.

---

#### **Mana yang harus dipilih?**
- **VirtualHost:** Jika kamu punya akses ke konfigurasi Apache dan ingin solusi permanen.
- **.htaccess:** Jika kamu hanya ingin mengubah konfigurasi tanpa menyentuh file utama Apache.
- **mod_rewrite:** Jika ingin redirect yang lebih fleksibel berdasarkan kondisi tertentu.

*catatan: portnya juga bisa diotak-atik, selama udah ditambahin di
└─# nano /etc/apache2/ports.conf
