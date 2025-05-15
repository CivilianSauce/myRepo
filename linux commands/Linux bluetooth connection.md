```bash
Untuk menghubungkan perangkat Bluetooth di Linux melalui command line, kamu bisa menggunakan `bluetoothctl`. Berikut langkah-langkahnya:

1. Pastikan Bluetooth Aktif
└─$ rfkill unblock bluetooth
└─$ systemctl start bluetooth

2. Masuk ke Bluetoothctl
└─$ bluetoothctl

3. Aktifkan Bluetooth dan Scanning
Di dalam mode `bluetoothctl`, jalankan perintah berikut:
[bluetooth]# power on
[bluetooth]# agent on
[bluetooth]# scan on

Perintah ini akan mengaktifkan Bluetooth, mengaktifkan agen pairing, dan mulai memindai perangkat.

4. Temukan Perangkat
Tunggu beberapa saat hingga perangkat yang ingin kamu hubungkan muncul, lalu catat alamat MAC-nya (misalnya `AA:BB:CC:DD:EE:FF`).

5. Pairing dengan Perangkat
[bluetooth]# pair AA:BB:CC:DD:EE:FF

Jika diminta PIN, masukkan sesuai yang ditampilkan di perangkat.

6. Trust dan Connect
[bluetooth]# trust AA:BB:CC:DD:EE:FF
[bluetooth]# connect AA:BB:CC:DD:EE:FF

Setelah ini, perangkat harus sudah terhubung.

7. Matikan Scanning (Opsional)
Jika sudah tidak perlu mencari perangkat lain, matikan scanning:
[bluetooth]# scan off

8. Keluar dari Bluetoothctl
[bluetooth]# exit

Jika perangkat tidak tersambung secara otomatis setelah reboot, kamu bisa menyalakan ulang Bluetooth dengan:
└─$ systemctl restart bluetooth

Kalau ada kendala, coba cek status service Bluetooth dengan:
└─$ systemctl status bluetooth

Atau lihat apakah ada konflik dengan:
└─$ dmesg | grep -i bluetooth
```
