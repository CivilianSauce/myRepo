Misalkan kita punya dua domain (jika belum punya, buat DNS terlebih dahulu):
- `example1.com`
- `example2.com`  

1. Buat direktori untuk masing-Masing Website
```bash
sudo mkdir /var/www/website1 /var/www/website2
```

2. Buat halaman sederhana untuk masing-masing website
```bash
sudo echo "<h1>Website 1</h1>" > /var/www/website1/index.html
sudo echo "<h1>Website 2</h1>" > /var/www/website2/index.html
```

3. Edit konfigurasi sistemnya
```bash
sudo nano /etc/lighttpd/lighttpd.conf
```
   tambahin ini di akhir file
```bash
    server.modules += ( "mod_simple_vhost" )

    $HTTP["host"] == "example1.com" {
        server.document-root = "/var/www/website1"
    }

    $HTTP["host"] == "example2.com" {
        server.document-root = "/var/www/website2"
    }
```

   ~ kalo mau bedain berdasarkan port, tambahin
```bash
      $SERVER["socket"] == ":8081" {
          server.document-root = "/var/www/website1"
      }

      $SERVER["socket"] == ":8082" {
          server.document-root = "/var/www/website2"
      }
```

4. Restart sistemnya
```bash
sudo systemctl restart lighttpd
```
