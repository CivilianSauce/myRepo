## Cara remote Termux menggunakan SSH (Secure Shell)

### 1. Instal OpenSSH di Termux
```bash
pkg update && pkg upgrade
pkg install openssh
```

### 2. Cek username dan atur password baru
```bash
whoami
passwd
```

### 3. Jalankan SSH Server di Termux
```bash
sshd
```

### 4. Cek IP perangkat  
```bash
ifconfig
```
atau  
```bash
ip a
```

### 5. Remote Termux dari perangkat lain (dari Linux/macOS/Windows dengan PowerShell atau Git Bash):
```bash
ssh username@192.168.1.100 -p 8022
```
FYI: Termux juga bisa remote sesamanya
