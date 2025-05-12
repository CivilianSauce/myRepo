## Menggunakan ImageMagick, alat serbaguna untuk manipulasi gambar di Linux

### Jika belum terinstal, bisa instal terlebih dahulu
```bash
sudo apt install imagemagick  # Debian/Ubuntu
sudo pacman -S imagemagick    # Arch Linux
sudo dnf install imagemagick  # Fedora
pkg install imagemagick       # Termux
```

### Command untuk menggunakan ImageMagick
```bash
convert gambar1.jpg gambar2.jpg gambar3.jpg -append hasil.jpg  #untuk menggabungkan secara vertikal
convert gambar1.jpg gambar2.jpg gambar3.jpg +append hasil.jpg  #untuk menggabungkan secara horizontal
```

### Kalau ingin menggabungkan banyak gambar dari satu folder tanpa menulis satu per satu:
```bash
convert *.jpg -append hasil.jpg  # atau `+append`, tergantung kebutuhan
```
