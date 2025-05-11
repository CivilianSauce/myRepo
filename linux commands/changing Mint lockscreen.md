Di Linux Mint, GUI `Login Window` jadi cara paling aman dan ringkas untuk mengganti lockscreen.

---

### 📌 Rekap singkat (untuk disimpan atau dicatat):

1. **Buat direktori khusus untuk wallpaper login:**

   ```bash
   sudo mkdir -p /usr/share/backgrounds/custom
   sudo cp ~/Pictures/wallpaper.jpg /usr/share/backgrounds/custom/
   sudo chmod 644 /usr/share/backgrounds/custom/wallpaper.jpg
   ```

2. **Buka GUI Login Window:**

   ```bash
   sudo lightdm-settings
   ```

   atau cari di menu: **Login Window**

3. **Di tab *Appearance*, pilih wallpaper baru**
   Pilih dari lokasi `/usr/share/backgrounds/custom/`

4. **Restart LightDM (jika ingin segera lihat hasilnya):**

   ```bash
   sudo systemctl restart lightdm
   ```
