**Cara buat USB Bootable**
---
Gunakan tool seperti:

* **Balena Etcher** (Windows/Linux/macOS)
* **Rufus** (Windows)
* **dd** (Linux command line, untuk pengguna mahir)

Contoh `dd` (hati-hati!):

```bash
sudo dd if=RedoRescue.iso of=/dev/sdX bs=4M status=progress && sync
```

*Ganti `/dev/sdX` dengan USB-mu (pastikan tidak salah drive!).*
