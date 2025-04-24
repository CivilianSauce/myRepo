Ya, *TWRP (Team Win Recovery Project)* perlu diunduh dan dipasang terlebih dahulu sebelum kamu dapat melakukan flashing ROM seperti *Pixel Experience. TWRP adalah **custom recovery* yang memungkinkan kamu untuk melakukan berbagai tugas pemeliharaan sistem Android, termasuk *install ROM, **backup, **wipe data*, dan lainnya.

### Langkah-Langkah Mengunduh dan Menginstal *TWRP* Sebelum Flashing

#### 1. *Unduh TWRP untuk Perangkatmu*
   - Kunjungi situs resmi TWRP: [https://twrp.me](https://twrp.me)
   - Pilih *device* yang sesuai dengan model ponselmu dari daftar perangkat yang didukung.
   - Unduh file *.img* TWRP yang sesuai dengan perangkatmu.

#### 2. *Memasang TWRP Menggunakan ADB Over Wi-Fi*
   Setelah ADB terhubung melalui Wi-Fi, kamu bisa menggunakan ADB untuk menginstal TWRP ke perangkat. Ikuti langkah-langkah ini untuk menginstal *TWRP recovery*:

##### *Langkah-langkah untuk Memasang TWRP*:

1. *Transfer File TWRP ke Ponsel* (Opsional, jika diperlukan)
   Kamu bisa mentransfer file TWRP .img ke ponselmu menggunakan perintah adb push. Gantilah /path/to/twrp.img dengan path file TWRP yang telah kamu unduh, dan /sdcard/ dengan direktori tujuan di ponsel.

   bash
   adb push /path/to/twrp.img /sdcard/
   

2. *Reboot ke Fastboot Mode*:
   Untuk menginstal TWRP, kamu harus memulai ponsel dalam *fastboot mode*. Kamu bisa melakukannya dengan perintah ADB berikut:
   bash
   adb reboot bootloader
   

   Ponselmu akan reboot ke *fastboot mode*. Pastikan perangkatmu sudah terdeteksi di mode fastboot dengan perintah:
   bash
   fastboot devices
   

3. *Flash TWRP ke Perangkat*:
   Setelah perangkat masuk ke *fastboot mode*, kamu bisa menginstal TWRP recovery dengan perintah berikut:
   bash
   fastboot flash recovery /sdcard/twrp.img
   

   Gantilah /sdcard/twrp.img dengan lokasi file *TWRP* yang sudah kamu transfer ke ponsel.

4. *Reboot ke Recovery*:
   Setelah TWRP selesai dipasang, kamu bisa me-reboot ponsel ke recovery mode dengan perintah:
   bash
   fastboot reboot recovery
   

   Ponsel akan reboot dan masuk ke *TWRP recovery*.

#### 3. *Melakukan Flash ROM Pixel Experience* (Setelah TWRP Terpasang)
Sekarang, dengan *TWRP recovery* yang terpasang, kamu bisa melanjutkan ke langkah-langkah yang telah dibahas sebelumnya untuk menginstal *Pixel Experience*:

- *Install ROM: Pilih file **Pixel Experience ZIP* yang telah kamu transfer ke ponsel dan mulai proses flashing.

#### Alternatif untuk Pengunduhan TWRP
Jika kamu lebih suka *menggunakan komputer untuk mengunduh TWRP* langsung dari internet, kamu bisa menyalin file *TWRP* langsung ke perangkat setelah diunduh melalui komputer, atau menggunakan *perangkat Android lain* untuk mendownloadnya, jika kamu sudah menyiapkan akses ke perangkat lain yang mendukung.

---

### Kesimpulan
Untuk memasang *TWRP recovery* dan melanjutkan proses flashing ROM seperti *Pixel Experience, kamu memang perlu mengunduh **TWRP recovery* terlebih dahulu. Begitu TWRP terpasang, kamu dapat melanjutkan ke proses flashing ROM tanpa perlu kabel USB, cukup dengan menggunakan *ADB over Wi-Fi*.

Jika ada hal lain yang masih membingungkan atau butuh penjelasan lebih lanjut, jangan ragu untuk bertanya! 😊
