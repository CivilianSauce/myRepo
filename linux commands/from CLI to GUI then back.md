### update paket-paket sistem terlebih dahulu
```bash
sudo apt update && sudo apt upgrade
```

### instal komponen dasar GUI
```bash
sudo apt install xorg
```

### pilih salah satu desktop environment yang diinginkan
```bash
sudo apt install gnome
sudo apt install kde-plasma-desktop
sudo apt install task-xfce-desktop
sudo apt install lxde
```

### set ke tampilan GUI
```bash
sudo systemctl set-default graphical.target
```

### mulai ulang sistem
```bash
sudo reboot
```

### jika GUI tidak muncul otomatis
```bash
startx
```

### kembali ke tampilan CLI
```bash
sudo systemctl set-default multi-user.target
```

*atau kalo lu males*

###  **Apa Itu TTY di Linux?**  
**TTY (TeleTYpewriter)** di Linux adalah terminal tekstual yang memungkinkan pengguna berinteraksi dengan sistem menggunakan antarmuka berbasis teks. Secara historis, istilah ini berasal dari mesin teletype yang digunakan untuk mengoperasikan komputer sebelum adanya GUI.

---

### ###  **1. TTY dalam Linux Modern**  
Di sistem Linux modern, **TTY mengacu pada virtual console (VC)**, yaitu terminal berbasis teks yang berjalan tanpa GUI. Secara default, Linux menyediakan beberapa **TTY virtual** yang bisa diakses dengan kombinasi tombol:

- **Ctrl + Alt + F1 hingga F6** → Beralih ke mode terminal TTY 1 sampai 6 (tanpa GUI).
- **Ctrl + Alt + F7 atau F2** → Kembali ke sesi GUI (jika menggunakan display manager).

---

### ###  **2. Cara Menggunakan TTY**  
Jika sistem mengalami masalah dengan GUI (seperti crash atau freeze), Anda bisa masuk ke **TTY mode** untuk memperbaiki sistem:

1. **Masuk ke TTY**  
   - Tekan `Ctrl + Alt + F3` (bisa juga F1, F2, dst.).
   - Masukkan **username** dan **password**.
   - Sekarang Anda bisa menjalankan perintah dalam mode teks.

2. **Keluar dari TTY dan Kembali ke GUI**  
   - Tekan `Ctrl + Alt + F7` atau `Ctrl + Alt + F2` (tergantung distribusi Linux).

---

### ###  **3. Perbedaan TTY, PTY, dan Terminal Emulator**
| **Istilah**  | **Penjelasan** |
|--------------|----------------|
| **TTY (TeleTYpewriter)** | Terminal fisik atau virtual di Linux. |
| **PTY (Pseudo Terminal)** | Terminal virtual yang digunakan oleh aplikasi GUI seperti terminal emulator. |
| **Terminal Emulator** | Aplikasi seperti `gnome-terminal`, `xfce4-terminal`, `konsole`, dll., yang berjalan di GUI tetapi bekerja seperti terminal TTY. |

---

### ###  **4. Kegunaan TTY**
- Memperbaiki sistem jika GUI crash.
- Mengelola server Linux tanpa GUI.
- Login ke sesi yang berbeda secara simultan.
- Menghemat sumber daya dibandingkan GUI.

Jika ingin mencoba, tekan **Ctrl + Alt + F3** di sistem Linux Anda, lalu login untuk melihat bagaimana TTY bekerja! 🚀
