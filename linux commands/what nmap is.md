`nmap` (singkatan dari *Network Mapper*) adalah sebuah tool open-source yang digunakan untuk melakukan **pemindaian jaringan** dan **auditing keamanan**. Dengan `nmap`, kamu bisa mengetahui perangkat apa saja yang terhubung ke jaringan, port apa saja yang terbuka, serta layanan apa yang berjalan di port-port tersebut.

### Fungsi utama `nmap`:

* Menemukan host yang aktif dalam jaringan.
* Mendeteksi port terbuka (open ports).
* Mengidentifikasi layanan dan versinya (seperti versi web server).
* Melakukan deteksi sistem operasi (*OS detection*).
* Melakukan deteksi firewall atau filter jaringan.

---

### Contoh Penggunaan:

```bash
nmap 192.168.1.1
```

Memindai alamat IP `192.168.1.1` untuk port terbuka.

```bash
nmap -sS 192.168.1.0/24
```

Melakukan *SYN scan* ke seluruh subnet `192.168.1.0/24`.

```bash
nmap -A example.com
```

Scan lengkap termasuk deteksi OS, versi layanan, dan traceroute.

```bash
nmap -p 22,80,443 example.com
```

Memindai hanya port 22 (SSH), 80 (HTTP), dan 443 (HTTPS) pada domain tertentu.

---

Kalau kamu tertarik dunia jaringan atau keamanan siber, `nmap` adalah salah satu alat paling mendasar dan wajib dipelajari.  
<!--Ingin aku bantu jelaskan salah satu opsi atau contoh penggunaannya lebih lanjut?-->
