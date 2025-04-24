*Ya, ADB over Wi-Fi memungkinkan meskipun ponselmu belum pernah terhubung sebelumnya dengan komputer. Yang penting adalah, **untuk pertama kali, kamu perlu melakukan koneksi melalui kabel USB* agar bisa mengaktifkan ADB melalui Wi-Fi. Setelah ADB diaktifkan melalui kabel, kamu bisa melanjutkan penggunaan ADB tanpa kabel, sepanjang perangkatmu dan komputer terhubung ke jaringan Wi-Fi yang sama.

Berikut adalah langkah-langkah yang lebih jelas mengenai bagaimana cara mengaktifkan dan menggunakan *ADB over Wi-Fi* bahkan jika ponselmu belum pernah terhubung ke komputer sebelumnya:

---

### Langkah-langkah Menggunakan ADB Over Wi-Fi Tanpa Koneksi Kabel

1. *Aktifkan USB Debugging di Ponsel*
   - Buka *Settings > About phone* dan tap *Build number* 7 kali untuk mengaktifkan *Developer Options*.
   - Masuk ke *Settings > Developer Options* dan aktifkan *USB Debugging*.

2. *Hubungkan Ponsel ke Komputer via Kabel USB* (untuk pertama kali)
   - Gunakan kabel USB untuk menghubungkan ponsel ke komputer, agar ADB dapat mengakses perangkat untuk pertama kali.
   - Buka terminal di Linux Mint, dan ketik:
     bash
     adb devices
     
   - Setelah itu, kamu akan melihat ID perangkat ponselmu muncul di layar jika perangkat berhasil terdeteksi. Kamu mungkin diminta untuk *mengizinkan akses USB debugging* pada perangkat Androidmu (pastikan untuk mengizinkannya).

3. *Aktifkan ADB Over Wi-Fi*
   - Di terminal, jalankan perintah berikut untuk mengaktifkan ADB melalui Wi-Fi:
     bash
     adb tcpip 5555
     
     Perintah ini akan mengaktifkan ADB di perangkat pada port *5555*.

4. *Temukan IP Ponsel*
   - Pada perangkat Android, buka *Settings > About phone > Status, cari bagian **IP address*.
   - Atau, kamu bisa mengetikkan perintah ini di terminal untuk mengetahui IP ponsel:
     bash
     adb shell ip route
     
     Biasanya IP akan tertera setelah wlan0.

5. *Sambungkan ADB ke Ponsel Melalui Wi-Fi*
   - Setelah mendapatkan alamat IP ponsel, sambungkan perangkat ke Wi-Fi dengan mengetikkan perintah berikut di terminal:
     bash
     adb connect <IP perangkat>:5555
     
     Gantilah *<IP perangkat>* dengan alamat IP yang kamu temukan tadi. Misalnya:
     bash
     adb connect 192.168.1.100:5555
     

6. *Cek Koneksi ADB*
   - Setelah itu, kamu bisa memeriksa apakah koneksi berhasil dengan mengetikkan perintah:
     bash
     adb devices
     
   - Jika semuanya berjalan dengan baik, kamu akan melihat ID perangkat di daftar perangkat yang terhubung, meskipun tidak ada kabel yang digunakan.

7. *Gunakan ADB seperti Biasanya*
   - Sekarang kamu sudah bisa menggunakan *ADB over Wi-Fi* untuk berbagai operasi seperti install APK, flashing ROM, atau menjalankan perintah shell pada ponselmu tanpa kabel USB.

---

### Apa yang Perlu Diperhatikan
- *Koneksi Wi-Fi: Pastikan ponsel dan komputer terhubung ke **jaringan Wi-Fi yang sama*, agar ADB over Wi-Fi bisa bekerja dengan baik.
- *Kecepatan Wi-Fi*: Koneksi Wi-Fi yang stabil dan cepat sangat penting untuk memastikan transfer data atau perintah ADB berjalan lancar. Jaringan yang lambat bisa menyebabkan ADB lebih lambat atau tidak stabil.
- *Keamanan*: Pastikan jaringan Wi-Fi yang kamu gunakan aman, karena koneksi ADB over Wi-Fi bisa membuka celah keamanan jika jaringanmu tidak terlindungi dengan baik.

---

### Kesimpulan
Dengan *ADB over Wi-Fi*, kamu tidak perlu kabel USB setelah mengaktifkan ADB pertama kali. Selama ponsel dan komputer berada di jaringan Wi-Fi yang sama, kamu bisa menghubungkan keduanya tanpa kabel untuk transfer data, flashing ROM, atau perintah ADB lainnya. Ini adalah solusi yang sangat berguna jika kamu ingin menghindari kerusakan port USB atau keterbatasan kabel, seperti yang kamu sebutkan sebelumnya.

Jadi, meskipun ponselmu tidak pernah terhubung ke komputer sebelumnya, ADB over Wi-Fi masih bisa diaktifkan dengan langkah-langkah yang tepat. Jika ada hal lain yang perlu dijelaskan atau jika kamu mengalami masalah, jangan ragu untuk bertanya lagi! 😊

note: this still needs cable at the very first step
