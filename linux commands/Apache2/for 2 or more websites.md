Misalkan kita punya dua domain (jika belum punya, buat DNS terlebih dahulu):  
`website1.com`  
`website2.com`  

---

### 1. Buat direktori untuk masing-Masing Website
```bash
mkdir /var/www/website1 /var/www/website2
```

### 2. Buat halaman sederhana untuk masing-masing website
```bash
echo "<h1>Website 1</h1>" > /var/www/website1/index.html
echo "<h1>Website 2</h1>" > /var/www/website2/index.html
```

### 3. Masuk ke direktori konfigurasi Apache2
```bash
cd /etc/apache2/sites-available/
```

### 4. Salin file default/template untuk virtualhost Apache2
```bash
cp 000-default.conf 001-default.conf 
cp 000-default.conf 002-default.conf 
```

### 5. Buat konfigurasi virtualhost-nya
```bash
nano 001-default.conf 
nano 002-default.conf   
```

- Pada bagian `ServerName`, hapus tanda `#` untuk mengaktifkannya (berlaku pada kedua file di atas)
- Pada bagian `www.example.com`, hapus dan ganti sesuai dengan domain yang dibuat (berlaku pada kedua file di atas, 
  pastikan kedua domain berbeda agar tidak bentrok)
- Pada bagian `DocumentRoot`, ganti path direktori sesuai dengan yang dibuat di nomor 1 tadi
 (opsional) Jika ingin membedakan beberapa website berdasarkan port dan bukan domain, cukup edit di bagian 
            `<VirtualHost *:80>` menjadi angka port yang tersedia (8080 misalnya) -> `<VirtualHost *:8080>`,
            tapi harus menambahkan `Listen 8080` di file ports.conf:
```bash
nano /etc/apache2/ports.conf
```

### 6. Atur kepemilikan dan izin (tidak wajib)
```bash
chown -R www-data:www-data /var/www/website1
chown -R www-data:www-data /var/www/website2
chmod -R 755 /var/www
```

### 7. Aktifkan Virtual Hosts
```bash
a2ensite 001-default.conf
a2ensite 002-default.conf
```

### 8. Restart Apache
```bash
systemctl restart apache2
```
