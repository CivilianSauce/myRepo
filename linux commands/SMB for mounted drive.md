**Linux juga bisa** mengatur folder di drive selain root (`/`) untuk sharing file (misalnya lewat SMB/Samba), dan drive tersebut bisa dilepas/konek kembali. Tapi ada beberapa hal yang perlu diperhatikan karena Linux cenderung lebih eksplisit dan manual dalam urusan mounting dan permission.

---

## 📁 Konsep Dasar

1. **Drive** = partisi yang di-*mount* ke suatu direktori (misalnya `/mnt/usb`, `/media/namauser/share`, dst).
2. **Folder sharing** = kamu bisa memakai Samba (untuk sharing ke Windows).
3. **Mounting dinamis** = kalau kamu lepas drive-nya, folder sharing akan "hilang" (sama seperti di Windows).

---

## ✔️ Contoh: Folder Sharing di Drive Eksternal (USB/HDD) via Samba

Misal kamu punya drive eksternal yang dimount ke `/media/user/USBDrive`, dan ingin share folder `SharedStuff` di dalamnya.

### 1. Mount drive secara otomatis (opsional)

Kalau drive ini selalu kamu pasang, kamu bisa atur agar selalu ter-mount di lokasi yang tetap lewat `fstab`, atau cukup pastikan lokasinya konsisten saat kamu pasang.

### 2. Install Samba (kalau belum)

```bash
sudo apt update
sudo apt install samba
```

### 3. Tambahkan konfigurasi di `/etc/samba/smb.conf`

Misalnya:

```ini
[SharedStuff]
   path = /media/user/USBDrive/SharedStuff
   read only = no
   browsable = yes
   guest ok = yes
```

Lalu restart Samba:

```bash
sudo systemctl restart smbd
```

### 4. Permissions

Pastikan folder yang di-*share* bisa dibaca/tulis oleh siapa pun yang mengakses (tergantung konfigurasi kamu), contoh:

```bash
sudo chmod -R 777 /media/user/USBDrive/SharedStuff
```

---

## ⚠️ Perhatian

* Kalau drive dilepas, maka folder share akan tidak bisa diakses (sama seperti di Windows).
* Pastikan lokasi *mount point* tetap konsisten jika kamu sering colok-lepas (gunakan `UUID` atau label).
* Jika kamu pakai *GUI* (misal Nautilus), pastikan kamu tahu mount path-nya.

---

## 📌 Catatan

Kamu perlu:

* tahu di mana drive-nya di-*mount*
* pastikan permission dan path benar
