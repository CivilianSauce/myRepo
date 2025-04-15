Lighttpd itu web server kayak Apache2, kalo mau nyoba:

1. Install dulu
```bash
sudo apt update
sudo apt install lighttpd
```

2. Nyalain sistemnya
```bash
sudo systemctl start lighttpd
sudo systemctl enable lighttpd
sudo systemctl status lighttpd
```

3. Atur hak akses file-nya (ga harus di /var/www, bisa di yang lain)
```bash
mkdir -p /home/user/mysite
sudo chown -R www-data:www -data /home/user/mysite
sudo chmod -R 755 /home/user/mysite
```

4. Tambahin file index.html-nya (kalo mau autoindex, liat tutor selanjutnya)
```bash
echo "<h1>kamu gg bang</h1>" > /home/user/mysite/index.html
```

5. (opsional) Nyalain fitur autoindex
```bash
sudo lighttpd-enable-mod dir-listing
```

6. Edit konfigurasi sistemnya
```bash
sudo nano /etc/lighttpd/lighttpd.conf
```

cari baris
    `server.document-root = "/var/www/html"`
ubah jadi
    `server.document-root = "/home/user/mysite"`

   ~ kalo mau bedain berdasarkan port, cari baris
      `server.port = 80`
      ubah jadi
      `server.port = 8080`  #misalnya

   ~ kalo mau autoindex, ubah/tambahin konfigurasi ini
```bash
      server.modules += ( "mod_dirlisting" )

      $HTTP["url"] =~ "^/" {
      dir-listing.activate = "enable"
      }
```

7. Restart sistemnya
```bash
sudo systemctl restart lighttpd
```

8. (opsional) Matiin autoindex
```bash
sudo lighttpd-disable-mod dir-listing
sudo systemctl restart lighttpd
```
