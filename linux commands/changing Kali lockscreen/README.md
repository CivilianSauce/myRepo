Di Kali Linux, login screen menggunakan **GDM (GNOME Display Manager)** jika Anda menggunakan lingkungan desktop GNOME. Jika Anda menggunakan **LightDM** (misalnya untuk XFCE), langkahnya berbeda. Berikut adalah cara mengganti wallpaper login sesuai dengan display manager yang Anda gunakan.

---

### **1. Jika Menggunakan GDM (GNOME Display Manager)**
#### **Cara Mengubah Wallpaper Login Screen**
1. **Buka Terminal** dan jalankan perintah berikut untuk membuka editor konfigurasi GDM:
   ```bash
   sudo nano /etc/alternatives/gdm3.css
   ```
2. **Cari bagian berikut** di dalam file:
   ```css
   #lockDialogGroup {
       background: #2c001e;
       background-repeat: no-repeat;
       background-size: cover;
       background-position: center;
   }
   ```
3. **Ganti dengan path gambar yang diinginkan**, misalnya:
   ```css
   #lockDialogGroup {
       background: url(file:///usr/share/backgrounds/login-wallpaper.jpg);
       background-repeat: no-repeat;
       background-size: cover;
       background-position: center;
   }
   ```
4. **Simpan perubahan** dengan menekan `CTRL + X`, lalu tekan `Y`, dan `Enter`.
5. **Salin gambar wallpaper ke direktori yang sesuai** (misalnya di `/usr/share/backgrounds/`):
   ```bash
   sudo cp /path/to/your/image.jpg /usr/share/backgrounds/login-wallpaper.jpg
   ```
6. **Pastikan hak akses gambar sudah benar**:
   ```bash
   sudo chmod 644 /usr/share/backgrounds/login-wallpaper.jpg
   ```
7. **Restart GDM** agar perubahan diterapkan:
   ```bash
   sudo systemctl restart gdm
   ```

---

### **2. Jika Menggunakan LightDM (Untuk XFCE atau Desktop Ringan Lainnya)**
#### **Cara Mengubah Wallpaper Login Screen**
1. **Buka Terminal** dan edit konfigurasi LightDM:
   ```bash
   sudo nano /etc/lightdm/lightdm-gtk-greeter.conf
   ```
2. **Cari baris yang mengatur latar belakang**:
   ```ini
   background=
   ```
3. **Ubah dengan path gambar yang diinginkan**, misalnya:
   ```ini
   background=/usr/share/backgrounds/login-wallpaper.jpg
   ```
4. **Simpan perubahan** dengan menekan `CTRL + X`, lalu tekan `Y`, dan `Enter`.
5. **Salin gambar wallpaper ke direktori yang sesuai**:
   ```bash
   sudo cp /path/to/your/image.jpg /usr/share/backgrounds/login-wallpaper.jpg
   ```
6. **Pastikan hak akses gambar sudah benar**:
   ```bash
   sudo chmod 644 /usr/share/backgrounds/login-wallpaper.jpg
   ```
7. **Restart LightDM agar perubahan diterapkan**:
   ```bash
   sudo systemctl restart lightdm
   ```

---

Setelah restart, login screen Kali Linux akan menggunakan wallpaper baru. Jika ada masalah, coba pastikan path gambar benar dan periksa konfigurasi yang diedit. 😊
