### 1. Update dan instal yang diperlukan
```bash
sudo apt update && sudo apt install samba -y
```

### 2. Edit file ini
```bash
sudo nano /etc/samba/smb.conf
```
scroll ke paling bawah, lalu masukkan
```
[{opsional1}]
path = /home/{opsional2}/
browseable = yes
writeable = yes
guest ok = yes
read only = no
public = yes
```

### 3. Buat direktori dengan ketik
```bash
sudo mkdir /home/{opsional2}/
```

### 4. Atur izin dan kepemilikan
```bash
sudo chmod 777 /home/{opsional2}/
```

### 5. Restart SMB
```bash
sudo systemctl restart smbd
```

### 6. Cek IP
```bash
ip -c a
```
lalu masukkan ip Linux tersebut di komputer Windows lain dengan Win+R lalu ketik  
`\\{IP Linux}, atau bisa dengan ketik smb://{IP Linux}`.
