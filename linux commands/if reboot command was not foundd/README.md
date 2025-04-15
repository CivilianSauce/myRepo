Jika perintah `reboot` tidak ditemukan di sistem kamu, kemungkinan karena perintah tersebut tidak tersedia atau tidak terpasang di dalam PATH. Kamu bisa mencoba beberapa alternatif berikut untuk melakukan reboot:

### **Metode 1: Menggunakan perintah `systemctl`**
Gunakan perintah `systemctl` untuk me-reboot sistem:
```bash
sudo systemctl reboot
```

### **Metode 2: Menggunakan perintah `shutdown`**
Kamu bisa menggunakan perintah `shutdown` dengan opsi untuk reboot:
```bash
sudo shutdown -r now
```
Perintah ini akan memulai reboot sistem segera setelah dijalankan.

### **Metode 3: Menggunakan perintah `init`**
Perintah `init` juga bisa digunakan untuk me-reboot sistem:
```bash
sudo init 6
```
Perintah ini akan mengubah runlevel sistem menjadi 6, yang memulai reboot.

Jika perintah-perintah tersebut masih tidak berfungsi, pastikan bahwa paket yang diperlukan untuk perintah tersebut sudah terinstal di sistem kamu.
