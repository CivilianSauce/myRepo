Tanda `\` dalam command tersebut berfungsi sebagai line continuation (penerusan baris).
Dalam shell Linux, perintah biasanya dieksekusi per baris. Tapi jika ingin menuliskan perintah panjang agar lebih mudah dibaca, kita bisa menggunakan `\` untuk memberitahu shell bahwa baris berikutnya masih merupakan bagian dari perintah yang sama.

### Contoh 1: Tanpa \ (Satu Baris)
Command ini tetap valid, tetapi sulit dibaca karena terlalu panjang:
```
sudo apt install ffmpeg libsdl2-2.0-0 adb wget gcc git pkg-config meson ninja-build libsdl2-dev libavcodec-dev libavdevice-dev libavformat-dev libavutil-dev libswresample-dev libusb-1.0-0 libusb-1.0-0-dev
```

### Contoh 2: Dengan \ (Lebih Mudah Dibaca)
Dengan menggunakan `\`, kita bisa membagi command panjang menjadi beberapa baris:
```
# for Debian/Ubuntu
sudo apt install ffmpeg libsdl2-2.0-0 adb wget \
                 gcc git pkg-config meson ninja-build libsdl2-dev \
                 libavcodec-dev libavdevice-dev libavformat-dev libavutil-dev \
                 libswresample-dev libusb-1.0-0 libusb-1.0-0-dev
```
Hasilnya sama saja, tetapi lebih rapi dan mudah dibaca.

Tapi ingat, `\` harus berada di akhir baris. Kalau ada spasi setelah `\`, command bisa gagal dieksekusi.
Jadi, tanda `\` hanya untuk mempermudah pembacaan, bukan bagian dari sintaks yang wajib. Kalau kamu mau, bisa saja menuliskan command dalam satu baris tanpa `\`.
