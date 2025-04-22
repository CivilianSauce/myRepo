Saat Linux sedang booting, menekan tombol *Esc* bisa menampilkan proses booting dalam bentuk *teks (verbose mode)*. Biasanya yang terlihat adalah *log output* dari systemd atau init, semacam:


[  OK  ] Started GNOME Display Manager.
[FAILED] Failed to start Network Manager.


Tapi ini tergantung juga pada distro Linux yang kamu pakai dan bagaimana konfigurasi *bootloader-nya* (biasanya GRUB). Berikut penjelasan lebih detail:

---

### 🔧 Kapan tombol Esc bisa dipakai saat booting?

- *Pada distros seperti Ubuntu, Fedora, Debian, dan turunannya*:
  - Kalau tampil splash screen (gambar logo atau animasi), kamu bisa tekan *Esc* untuk menyembunyikan splash dan menampilkan teks boot (log output).
  - Kalau sudah diatur quiet splash di GRUB, maka log boot tidak langsung muncul. Nah, Esc ini semacam override.

---

### 🧪 Tips: Kalau kamu ingin log boot selalu muncul (tanpa tekan Esc)

Edit konfigurasi GRUB:

1. Buka terminal.
2. Edit file GRUB:  
   bash
   sudo nano /etc/default/grub
   
3. Cari baris:
   
   GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
   
   Ubah menjadi:
   
   GRUB_CMDLINE_LINUX_DEFAULT=""
   
   atau kalau kamu ingin tampil teks dan tidak ingin splash sama sekali.

4. Simpan, lalu update grub:
   bash
   sudo update-grub
