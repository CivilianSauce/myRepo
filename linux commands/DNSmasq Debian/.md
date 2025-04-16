## **🔹 Cara Menggunakan Domain Lokal Sendiri (Tanpa Edit DNS Klien)**
Agar semua perangkat di LAN otomatis menggunakan DNS lokal, cukup gunakan **dnsmasq** sebagai server DNS. Berikut langkahnya:  

### **1️⃣ Install dnsmasq**
```
sudo apt install dnsmasq
```
---

### **2️⃣ Konfigurasi dnsmasq**
Edit file konfigurasinya
```bash
sudo nano /etc/dnsmasq.conf
```

Tambahkan atau ubah baris berikut:  
```bash
# Gunakan interface LAN
interface=enp2s0   #tergantung pada interface yang dipakai

# Domain lokal sebagai contoh
domain=rumahku.local

# IP dari domain lokal yang akan digunakan
address=/server.rumahku.local/192.168.1.1
address=/printer.rumahku.local/192.168.1.10
address=/nas.rumahku.local/192.168.1.20

# Gunakan DNS publik untuk akses internet
server=8.8.8.8
server=1.1.1.1
```

Buka file resolv.conf
```bash
sudo nano /etc/resolv.conf
```
hapus semua isinya dan ubah menjadi 'nameserver 192.168.1.1'  #misal, tergantung IP Debian

Simpan dan restart dnsmasq
```
sudo systemctl restart dnsmasq
```
---

## **🔹 Uji Coba**
1️⃣ **Tes akses domain lokal:**  
```bash
ping server.rumahku.local
```
   Jika berhasil, akan merespons dengan **192.168.1.1**.  #misal, tergantung IP Debian

2️⃣ **Cek apakah domain lain tetap bisa diakses:**  
```bash
ping google.com
```
   Jika berhasil, berarti DNS forwarding berjalan dengan baik.
