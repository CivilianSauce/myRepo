### 1. Instal paket-paket yang diperlukan

- untuk Debian-based Linux
```bash
sudo apt install python3 python3-pip python3-venv -y
python3 -m venv ~/venv-ftp
source ~/venv-ftp/bin/activate
pip install pyftpdlib
```

- untuk Termux
```bash
pkg install python python-pip -y
pip install pyftpdlib
```

### 2. Atur kepemilikan direktori
```bash
termux-setup-storage   # untuk izin baca-tulis storage di Termux, Linux lainnya tidak perlu
mkdir ~/shared
chmod -R 777 ~/shared
```

### 3. Cek IP Linux untuk koneksi ke komputer lain
```bash
ifconfig   # karena `ip -c a` tidak berlaku di Termux
```

### 4. Aktifkan server FTP (username dan password bebas, namun jika dikosongkan berarti anonim)
```bash
python -m pyftpdlib -p 2121 -u username -P password -d ~/shared -w &
```
Makna opsi-opsi di atas
- `-p` -> menentukan port yang akan digunakan
- `-u` -> membuat username yang diizinkan
- `-P` -> men-set password berdasarkan username tadi
- `-d` -> menentukan direktori yang akan menjadi root server FTP
- `-w` -> mengizinkan tulis di direktori tersebut
- `&`  -> agar shell tetap dapat digunakan

### 5. Akses FTP server dari komputer lain sesuai dengan IP Termux
`ftp://{IP Termux}:2121`

### 6. Untuk mematikan FTP server setelah digunakan, ketik:
```bash
pkill -f pyftpdlib
```
