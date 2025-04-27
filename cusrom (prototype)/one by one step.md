Jika kabel EDL yang kamu gunakan sudah dilengkapi dengan tombol untuk memaksa ponsel masuk ke **EDL mode**, prosesnya akan jauh lebih sederhana karena kamu tidak perlu mencari cara lain untuk menghubungkan ponsel ke **EDL** menggunakan kabel atau metode hardware lain.

Berikut adalah tahapan yang lebih rinci menggunakan **kabel EDL dengan tombol**:

### **1. Persiapan Sebelum Memulai**
- **Backup data**: Sebelum memulai, pastikan untuk membackup data penting dari ponsel karena beberapa proses, seperti flashing firmware atau TWRP, dapat menghapus data.
- Siapkan **PC** dengan sistem operasi **Ubuntu/Linux** atau **Windows**, pastikan sudah menginstal **ADB** dan **Fastboot**.

---

### **2. Menggunakan Kabel EDL dengan Tombol**

1. **Matikan Ponsel**:
   - Tekan dan tahan tombol **Power** pada ponsel untuk mematikannya sepenuhnya.
   
2. **Hubungkan Kabel EDL dengan Tombol**:
   - **Pasang Kabel EDL** ke **PC** dan ke ponsel.
   - Jika kabel EDL sudah dilengkapi tombol, kamu hanya perlu menekan tombol tersebut (biasanya di bagian tengah kabel atau di ujungnya yang terhubung dengan ponsel).
   
3. **Tekan Tombol untuk Masuk ke EDL Mode**:
   - Setelah kabel terhubung ke ponsel dan PC, **tekan dan tahan tombol EDL** pada kabel **selama beberapa detik** (biasanya 5–10 detik) hingga ponsel masuk ke **EDL mode**.
   - **LED indikator** atau layar ponsel (tergantung model) biasanya akan menunjukkan bahwa ponsel dalam mode **EDL**, atau ponsel akan terdeteksi oleh PC.

4. **Verifikasi Koneksi ke PC**:
   - Setelah ponsel berada di **EDL mode**, pastikan ponsel terdeteksi oleh PC.
   - Jalankan perintah berikut di terminal **Linux** (atau **Command Prompt** di **Windows**) untuk memeriksa apakah perangkat terdeteksi:
     ```bash
     sudo lsusb
     ```
   - Output yang muncul harus mencantumkan ponselmu, misalnya:
     ```text
     Bus 001 Device 016: ID 2717:ff48 Xiaomi Inc. Mi/Redmi series (MTP + ADB)
     ```

---

### **3. Flash Firmware atau Fastboot ROM**

Setelah ponsel terdeteksi di **EDL mode**, kamu dapat melanjutkan proses flashing dengan **MiFlash** (Windows) atau menggunakan **Fastboot** (Linux). Berikut langkah-langkah untuk keduanya:

#### **A. Flash Firmware Resmi (Menggunakan MiFlash di Windows)**

1. **Install MiFlash**:
   - Jika kamu menggunakan **Windows**, install **MiFlash** dan pastikan **drivers Xiaomi** terinstal.
   - Ekstrak file **Fastboot ROM** yang sudah kamu unduh sebelumnya ke folder di PC.

2. **Flash Firmware Menggunakan MiFlash**:
   - Jalankan **MiFlash**, pilih folder tempat kamu mengekstrak file **Fastboot ROM**, dan tekan tombol **Flash**.
   - Proses ini akan mem-flash firmware resmi ke ponselmu melalui **EDL mode**.

#### **B. Flash Firmware Menggunakan Fastboot di Linux**

1. **Masuk ke Fastboot Mode (Jika Belum)**:
   - Jika ponsel sudah berada di **EDL**, kamu dapat menggunakan perintah berikut di terminal untuk memindahkan ponsel ke **Fastboot mode** (jika perlu):
     ```bash
     sudo fastboot reboot bootloader
     ```
   
2. **Flash Firmware Menggunakan Fastboot**:
   - Setelah ponsel berada di **Fastboot mode**, kamu bisa mem-flash file **Fastboot ROM** menggunakan perintah:
     ```bash
     sudo fastboot flash all <path_to_fastboot_rom>.tgz
     ```

---

### **4. Masukkan TWRP Recovery dan Custom ROM**

Setelah firmware berhasil di-flash, kamu bisa melanjutkan ke tahap berikutnya untuk memasang **TWRP** dan **Custom ROM**.

1. **Flash TWRP Recovery**:
   - Jika kamu sudah menyiapkan file **TWRP recovery** (misalnya **KewL-TWRP-3.4.0-rosy.img**), gunakan perintah berikut untuk mem-flash recovery:
     ```bash
     sudo fastboot flash recovery <twrp_filename>.img
     ```

2. **Reboot ke TWRP**:
   - Setelah flashing selesai, kamu dapat melakukan reboot ke **TWRP** dengan perintah:
     ```bash
     sudo fastboot boot <twrp_filename>.img
     ```

3. **Install Custom ROM**:
   - Di dalam **TWRP**, pilih **Install**, lalu pilih file **Custom ROM** dalam format **.zip** yang sudah kamu siapkan.
   - Geser untuk mengonfirmasi flashing ROM.
   - Setelah flashing selesai, lakukan **Wipe Data** dan reboot ke sistem baru.

---

### **5. Selesai**

Setelah langkah-langkah di atas selesai, ponsel kamu akan menjalankan **Custom ROM** yang baru, dan **TWRP recovery** sudah terpasang.

---

**Catatan Penting**:
- Selalu pastikan bahwa kabel EDL dan prosesnya berjalan dengan lancar. Jika kabel EDL dengan tombol tidak berhasil, kamu perlu mencoba metode lain untuk memasukkan ponsel ke **EDL mode**.
- Proses flashing dan modifikasi ponsel bisa menghapus data, jadi pastikan sudah melakukan backup.
- Pastikan untuk menggunakan file **ROM** yang sesuai dengan model ponselmu.

Jika ada langkah yang masih membingungkan atau ada masalah yang muncul, beri tahu saja!
