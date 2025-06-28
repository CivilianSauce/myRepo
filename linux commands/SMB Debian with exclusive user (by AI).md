Untuk membuat folder berbagi lokal di Linux, Anda bisa menggunakan Samba atau NFS, tergantung pada kebutuhan Anda. Berikut adalah cara membuat folder berbagi lokal menggunakan Samba, 
yang lebih umum digunakan di lingkungan campuran (Linux dan Windows):

### 1. Instal Samba
Jika Samba belum terinstal di sistem Anda, install terlebih dahulu. Di terminal, jalankan perintah berikut:

```bash
sudo apt update
sudo apt install samba
```

### 2. Buat Folder yang Akan Dibagikan
Buat folder yang akan dibagikan. Misalnya, buat folder di /home/username/SharedFolder:

```bash
mkdir -p /home/username/SharedFolder
```

Gantilah username dengan nama pengguna Anda.

### 3. Setel Izin Akses
Atur izin akses ke folder yang baru dibuat agar dapat dibaca dan ditulis oleh orang lain (misalnya, grup pengguna sambashare):

```bash
sudo chmod 777 /home/username
sudo chmod 777 /home/username/SharedFolder
```

### 4. Konfigurasi Samba
Sekarang, buka file konfigurasi Samba untuk menambahkan folder berbagi lokal:

```bash
sudo nano /etc/samba/smb.conf
```

Di bagian bawah file tersebut, tambahkan konfigurasi berikut:

```bash
[SharedFolder]
   path = /home/username/SharedFolder
   valid users = resident
   available = yes  #jika ingin menonaktifkan samba tanpa menghapus konfigurasinya, ubah menjadi `no`
   browsable = yes
   writable = yes
   read only = no
   public = yes
```

Gantilah username dengan nama pengguna Anda.

### 5. Menambahkan Pengguna Samba
Jika Anda ingin membatasi akses ke folder berbagi dengan username dan password, Anda perlu menambahkan pengguna Samba:

```bash
sudo useradd resident
sudo smbpasswd -a resident
```

Setelah itu, ikuti instruksi untuk mengatur kata sandi.

### 6. Restart Samba
Setelah konfigurasi selesai, restart layanan Samba agar perubahan diterapkan:

```bash
sudo systemctl restart smbd
```

### 7. Akses Folder Berbagi
Untuk mengakses folder berbagi dari mesin lain, gunakan alamat IP mesin Linux diikuti dengan nama folder yang dibagikan. Misalnya:

```
\\192.168.1.10\SharedFolder
```

Jika menggunakan Windows, Anda bisa mengetikkan alamat tersebut di Explorer. Jika di Linux, Anda bisa mengaksesnya melalui aplikasi pengelola file (file manager), pilih "Network" atau gunakan perintah `smb://`.

**Jika ingin menghapus user,**
gunakan:
```bash
sudo userdel resident   #tambahkan opsi `-r` jika ingin sekalian menghapus direktori terkait user tersebut
```

**Jika user sedang login,**
kamu perlu logout user tersebut atau gunakan:
```bash
sudo pkill -u resident
```
lalu coba hapus lagi.
Pastikan tidak menghapus user yang penting, seperti user utama atau root.

Dengan cara ini, folder berbagi lokal Anda sudah siap untuk diakses!
