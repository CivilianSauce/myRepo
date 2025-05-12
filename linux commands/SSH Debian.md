```bash
apt install ssh
nano /etc/ssh/sshd_config
```

- Pada bagian Port, hapus tanda `#` agar port menyala  
(opsional: ganti angkanya menjadi angka di antara 5000-6000 untuk batas aman)

- Setelah itu ketik:
```bash
systemctl restart ssh
```

- Jika ingin diakses Linux lain di jaringan yang sama, ketik:
```bash
ssh {username_debian}@{ip_debian} -p {angka_port}
```
