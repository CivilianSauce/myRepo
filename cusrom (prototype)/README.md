```
dd if=/sdcard/twrp.img of=/dev/block/bootdevice/by-name/recovery
```
- https://get.pixelexperience.org/rosy
- https://wiki.pixelexperience.org/devices/rosy/install/
- https://wiki.pixelexperience.org/devices/rosy/build/
- https://twrp.me/xiaomi/xiaomiredmi5.html
- https://miuirom.org/updates/mi-flash-unlock

------

Polanya bisa dirangkum seperti ini:

---

### 📦 **Langkah-langkah Pola untuk Unlock dan Flashing:**

1. **Siapkan ADB dan Fastboot di Linux**:
   - Pastikan ponsel sudah di **fastboot mode** di Linux (`adb reboot bootloader`).
   - **Jangan cabut kabel USB**.

2. **Pindah ke Windows**:
   - Restart atau reboot ke **Windows**.
   - Ponsel masih tetap berada di mode **fastboot** setelah reboot.

3. **Install Mi Unlock Tool di Windows**:
   - Download dan install **Mi Unlock Tool** di Windows.
   - Login menggunakan **akun Xiaomi** yang sudah terdaftar dan memerlukan waktu beberapa hari (biasanya 7 hari atau lebih).

4. **Unlock Bootloader**:
   - Setelah login di Mi Unlock Tool, klik **Unlock** dan tunggu proses selesai.

5. **Flash TWRP atau Custom ROM**:
   - Setelah bootloader ter-unlock, kamu bisa lanjut ke **flash TWRP** atau **custom ROM** (gunakan **fastboot** command atau TWRP recovery).

---

### 💡 **Kenapa Bisa Sukses:**
- **Mode Fastboot tetap aktif** selama ponsel terhubung via USB. Ketika kamu reboot ke Windows, ponsel masih di fastboot mode dan dapat dideteksi oleh Mi Unlock Tool.
- Windows akan **mendeteksi ponsel di fastboot mode**, dan kamu bisa melakukan **unlock** tanpa masalah.

---

Jadi, walaupun host berubah dari Linux ke Windows, **ponsel tetap bisa diatur** dalam mode fastboot tanpa masalah, dan kamu tetap bisa melanjutkan ke langkah berikutnya setelah unlock.

Semoga pola ini membuat prosesnya lebih jelas! Ada bagian lain yang perlu dijelaskan atau ada masalah lain yang muncul?
