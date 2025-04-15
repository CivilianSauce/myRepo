Untuk mengaktifkan **autologin** pada Linux Desktop berbasis **Debian**, caranya tergantung pada **display manager** yang digunakan. Berikut adalah langkah-langkah untuk beberapa **display manager** yang umum digunakan.

---

## **1. LightDM (default pada XFCE, LXDE, MATE)**
1. **Edit file konfigurasi LightDM**  
   ```bash
   sudo nano /etc/lightdm/lightdm.conf
   ```
2. **Cari dan ubah bagian berikut** (jika tidak ada, tambahkan di bawah `[Seat:*]`):  
   ```ini
   [Seat:*]
   autologin-user=nama_pengguna
   autologin-user-timeout=0
   ```
   Ganti `nama_pengguna` dengan username Anda.

3. **Simpan dan keluar** (tekan `CTRL + X`, lalu `Y`, lalu `ENTER`).
4. **Restart LightDM** atau reboot sistem:  
   ```bash
   sudo systemctl restart lightdm
   ```

---

## **2. GDM (GNOME)**
1. **Edit file konfigurasi GDM**  
   ```bash
   sudo nano /etc/gdm3/custom.conf
   ```
2. **Cari bagian berikut dan ubah/aktifkan:**  
   ```ini
   [daemon]
   AutomaticLoginEnable=True
   AutomaticLogin=nama_pengguna
   ```
   Ganti `nama_pengguna` dengan username Anda.

3. **Simpan dan keluar**, lalu restart GDM atau reboot:  
   ```bash
   sudo systemctl restart gdm3
   ```

---

## **3. SDDM (KDE Plasma, LXQt)**
1. **Edit file konfigurasi SDDM**  
   ```bash
   sudo nano /etc/sddm.conf
   ```
2. **Tambahkan atau ubah bagian berikut:**  
   ```ini
   [Autologin]
   User=nama_pengguna
   Session=plasma.desktop
   ```
   Ganti `nama_pengguna` dengan username Anda, dan pastikan `Session=` sesuai dengan desktop yang digunakan (misalnya `xfce.desktop` untuk XFCE, `lxqt.desktop` untuk LXQt).

3. **Simpan dan keluar**, lalu restart SDDM atau reboot:  
   ```bash
   sudo systemctl restart sddm
   ```

---

Setelah mengikuti langkah-langkah di atas, sistem seharusnya langsung login secara otomatis ke desktop tanpa meminta password. Jika masih tidak berfungsi, pastikan user Anda tidak memiliki **password login yang kosong** atau **autologin tidak diblokir oleh policy tertentu**.

**Karena Anda menggunakan XFCE**, kemungkinan besar LightDM adalah display manager yang digunakan. Coba metode **LightDM** terlebih dahulu. 🚀
