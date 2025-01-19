Jika Anda menggunakan **Debian 12** dengan antarmuka **CLI (Command-Line Interface)** dan ingin mengatur agar sistem langsung masuk (autologin) tanpa diminta login, Anda dapat mengonfigurasi **getty** (layanan login di terminal) untuk melakukan autologin. Berikut langkah-langkahnya:

---

### **1. Edit File `getty@.service`:**
1. **Buka Terminal**:
   Jika Anda sudah login, buka terminal. Jika belum login, masuk sebagai root terlebih dahulu atau gunakan `sudo` jika pengguna Anda memiliki hak akses.
   
2. **Salin Unit File untuk Getty:**
   Salin file unit default dari sistem agar dapat dimodifikasi:
   ```bash
   sudo cp /lib/systemd/system/getty@.service /etc/systemd/system/getty@tty1.service
   ```

3. **Edit File yang Disalin:**
   Buka file dengan editor teks:
   ```bash
   sudo nano /etc/systemd/system/getty@tty1.service
   ```
   
4. **Tambahkan Opsi Autologin:**
   Cari baris berikut di dalam file:
   ```plaintext
   ExecStart=-/sbin/agetty -o '-p -- \\u' --noclear %I $TERM
   ```
   Ganti baris tersebut dengan:
   ```plaintext
   ExecStart=-/sbin/agetty --noclear -a nama_pengguna %I $TERM
   ```
   Ganti `nama_pengguna` dengan nama pengguna yang ingin Anda gunakan untuk autologin (root juga bisa, selama paham resikonya).

5. **Simpan dan Keluar**:
   Tekan `Ctrl + O` untuk menyimpan, lalu `Ctrl + X` untuk keluar dari editor.

---

### **2. Muat Ulang Layanan Systemd:**
Setelah selesai mengedit file, reload systemd agar perubahan diterapkan:
```bash
sudo systemctl daemon-reload
```

---

### **3. Aktifkan Autologin pada tty1:**
Aktifkan layanan yang sudah dikonfigurasi untuk tty1:
```bash
sudo systemctl restart getty@tty1.service
```

---

### **4. Uji Hasilnya:**
1. **Reboot Sistem**:
   Restart sistem Anda dengan:
   ```bash
   sudo reboot
   ```
2. Sistem seharusnya langsung masuk ke terminal dengan akun pengguna yang telah Anda tentukan tanpa meminta login.

---

### **Catatan Penting:**
1. **Keamanan**:
   - Jangan gunakan autologin untuk akun root atau sistem yang membutuhkan keamanan ekstra.
2. **Nonaktifkan Autologin Jika Diperlukan**:
   Jika ingin kembali ke pengaturan login manual, cukup hapus atau kembalikan file `/etc/systemd/system/getty@tty1.service` ke versi default:
   ```bash
   sudo rm /etc/systemd/system/getty@tty1.service
   sudo systemctl daemon-reload
   ```

Semoga berhasil! 😊
