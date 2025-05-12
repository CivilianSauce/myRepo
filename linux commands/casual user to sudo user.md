### 1. Install sudo dengan masuk ke root terlebih dahulu
```bash
apt install sudo
```

### 2. Edit file ini
```bash
nano /etc/group
```
dan tambahkan username pada file group
```bash
sudo:x:27:{username yang ingin diberi akses sudo}
```
contoh:
```bash
sudo:x:27:antix
```

### 3. Mulai ulang Linux
```bash
systemctl reboot
```
