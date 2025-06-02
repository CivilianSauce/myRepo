Berikut langkah-langkah untuk mengonfigurasi **Super + L** agar bekerja seperti **Windows + L** untuk mengunci layar:

### 1. **Pastikan Screen Locking Dikonfigurasi**

* Pertama, pastikan fitur kunci layar sudah aktif di sistem.
* Buka **Menu** > **Settings** > **Power Manager**.
* Pergi ke tab **"Security"** dan pastikan opsi **"Lock screen when system is idle"** diaktifkan.

### 2. **Buka Pengaturan Keyboard**

* Klik kanan pada menu aplikasi atau buka **Menu** > **Settings** > **Keyboard**.
* Di jendela **Keyboard**, pilih tab **Application Shortcuts**.

### 3. **Tambahkan Shortcut Kunci Layar**

* Klik tombol **"+ Add"** di bagian bawah.

* Di jendela yang muncul, masukkan perintah berikut di kolom **Command**:

  ```bash
  light-locker-command --lock
  ```

  Perintah ini akan langsung mengunci layar tanpa membuka menu logout.

* Kemudian, klik pada kolom sebelah kanan dan tekan **Super + L** untuk menetapkannya sebagai shortcut.

### 4. **Selesai**

* Sekarang, ketika kamu menekan **Super + L**, layar akan terkunci langsung, sama seperti di Windows!

Jika kamu menggunakan **light-locker** sebagai aplikasi pengunci layar, perintah di atas harus berfungsi dengan baik. Jika kamu tidak menggunakan light-locker, bisa jadi kamu perlu menginstalnya terlebih dahulu:

### Menginstal light-locker (jika belum ada):

1. Buka **Terminal**.
2. Jalankan perintah:

   ```bash
   sudo apt-get install light-locker
   ```
