Masalah "command not found" pada `shutdown` di Debian biasanya terjadi karena salah satu alasan berikut:  

### 1. **Package `systemd-sysv` Tidak Terinstal**
Perintah `shutdown` adalah bagian dari paket *systemd*. Jika tidak ada, Anda perlu menginstalnya:
```bash
sudo apt update
sudo apt install systemd-sysv
```

### 2. **Path Tidak Benar**
Pastikan direktori yang berisi perintah `shutdown` ada di PATH. Biasanya, `shutdown` berada di `/sbin`. Jalankan ini untuk memeriksa:
```bash
echo $PATH
```
Jika `/sbin` tidak ada, tambahkan:
```bash
export PATH=$PATH:/sbin:/usr/sbin
```

### 3. **Tidak Menggunakan Hak Akses Root**
Perintah `shutdown` membutuhkan hak akses root. Jika Anda pengguna biasa, gunakan `sudo`:
```bash
sudo shutdown now
```

### 4. **Menggunakan Sistem Minimal**
Jika Anda menggunakan sistem minimal (misalnya Debian tanpa GUI atau instalasi ringan), beberapa utilitas mungkin belum terinstal. Anda bisa menambahkan dengan:
```bash
sudo apt update
sudo apt install coreutils systemd-sysv
```

Coba jalankan ulang perintah setelah melakukan salah satu langkah di atas!
