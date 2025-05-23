Untuk langsung masuk ke Debian tanpa menampilkan menu GRUB (seperti opsi *Debian GNU/Linux* dan *Advanced Options*), kamu bisa mengatur GRUB agar langsung boot ke sistem default. Berikut langkah-langkahnya:

---

### **1. Edit Konfigurasi GRUB**
- Buka file konfigurasi GRUB dengan editor teks (gunakan `nano` jika tidak ada editor lain):
  ```bash
  sudo nano /etc/default/grub
  ```

- Temukan dan ubah baris berikut:
  1. **Ubah timeout menjadi 0 (atau 1 untuk jaga-jaga):**
     ```bash
     GRUB_TIMEOUT=0
     ```
     Ini akan membuat GRUB langsung boot tanpa menunggu.

  2. **Pastikan opsi default diatur ke sistem utama:**
     ```bash
     GRUB_DEFAULT=0
     ```
     Angka `0` mengacu pada entri pertama dalam daftar menu GRUB (biasanya Debian GNU/Linux).

---

### **2. Terapkan Perubahan GRUB**
- Setelah mengedit file, simpan dan keluar dari editor:
  - Tekan `CTRL+O` untuk menyimpan.
  - Tekan `CTRL+X` untuk keluar.

- Perbarui konfigurasi GRUB agar perubahan berlaku:
  ```bash
  sudo update-grub
  ```

---

### **3. Restart Sistem**
- Reboot sistem untuk memeriksa apakah menu GRUB dilewati:
  ```bash
  sudo reboot
  ```

---

### **4. (Opsional) Mengembalikan Menu GRUB**
Jika di masa depan kamu butuh kembali ke menu GRUB (misalnya, untuk masuk ke *Advanced Options*), tahan tombol **Shift** atau **Esc** saat sistem menyala untuk menampilkan menu GRUB.

---

### **Catatan**
Jika ada masalah atau kamu tidak yakin dengan pengaturan, pastikan kamu menyimpan file backup sebelum mengubah konfigurasi GRUB:
```bash
sudo cp /etc/default/grub /etc/default/grub.bak
```

---

### **0. Kalau yang ingin diubah adalah tampilan saat booting (GRUB wallpaper),**
bisa dengan edit konfigurasi GRUB
```bash
sudo nano /etc/default/grub                                 
```

Ubah/tambahkan baris:
```bash
GRUB_BACKGROUND=/path/to/image.png
```

Lalu update GRUB
```bash
sudo update-grub                                            
```
