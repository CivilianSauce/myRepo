### Berikut langkah-langkahnya
Instal scrcpy sesuai yang ada di [Github](https://github.com/Genymobile/scrcpy).

---

1. Pastikan HP dan PC terhubung kabel USB dengan USB debugging menyala

2. Ketik di PC lalu cabut kabel USB
```bash
adb tcpip 5555
```

3. Ketik di PC dengan mengganti {ip} dengan alamat IP HP
```bash
adb connect {ip}:5555
```

4. Nyalakan scrcpy
```bash
scrcpy
```
