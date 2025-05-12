### 1.Update dan upgrade Debian
```bash
apt update && apt upgrade
```

### 2.Instal Apache2 dan Bind9
```bash
apt install apache2 dnsutils bind9
```

### 3.Masuk ke directory Bind9
```bash
cd /etc/bind/
```

### 4.Ganti nama salah satu file
```bash
mv named.conf.local named.conf.local.ori  #nama file opsional selama nama file berbeda dari sebelumnya
```

### 5.Salin dan ganti nama file yang disalin
```bash
cp named.conf.default-zones named.conf.local
cp db.127 db.192
cp db.local db.dikali  #nama file opsional
```

### 6.Buka file yang tadi
```bash
nano db.dikali
```

Ganti semua yang bertuliskan `localhost` menjadi nama domain, caranya:
- klik Win+R,
- ketik `localhost`,
- klik Enter,
- ketik domain `dikali.net`  #misal
- klik A untuk mengganti semuanya,
- ganti IP yang ada menjadi IP Debian
  `127.0.0.1` -> `192.168.1.1`  #misal, tergantung IP Debian
- jika ingin membuat subdomain, lakukan ini pada baris terakhirnya:
  - ketik `www`
  - klik Tab
  - ketik `IN`
  - klik Tab
  - ketik `A`
  - klik Tab
  - ketik IP Debian `192.168.1.1`  #misal, tergantung IP Debian
- save file db.dikali

### 7.Buka file db.192 yang tadi
```bash
nano db.192
```

Ganti semua yang bertuliskan `localhost` menjadi nama domain, caranya:
- klik Win+R,
- ketik `localhost`,
- klik Enter,
- ketik domain `dikali.net`
- klik A untuk mengganti semuanya,
- hapus IP pada pojok kiri bawah dan ganti dengan hanya angka oktet terakhir IP Debian
- save file db.192

### 8.Buka file named.conf.local
```bash
nano named.conf.local
```

- Hapus 9 baris teratas dan baris ke19 sampai seterusnya
- Ganti yang bertuliskan `localhost` menjadi domain `dikali.net`
- Ganti yang bertuliskan `127.in-addr.arpa` menjadi 3 oktet pertama IP Debian yang dibalik 
  (misal jika IP Debian 192.168.1.1 maka ganti menjadi `1.168.192.in-addr.arpa`)
- Ganti lokasi file pada baris ke-3
  `file "/etc/bind/db.dikali";`
- Ganti lokasi file pada baris ke-8
  `file "/etc/bind/db.192";`
- Simpan file named.conf.local

### 9.Buka file resolv.conf
```bash
nano /etc/resolv.conf
```
tambahkan atau hapus semua isinya dan ubah menjadi `nameserver 192.168.1.1`  #misal, tergantung IP Debian

### 10.Restart Bind9 dan Network
```bash
systemctl restart bind9 networking
```

---

Untuk memastikan ini berhasil, ketik  
```bash
nslookup dikali.net
```

Jika tidak ada tulisan NXDOMAIN atau SERVFAIL, maka sudah berhasil
```bash
ping dikali.net
ping www.dikali.net
```

Jika TTL maka berhasil
