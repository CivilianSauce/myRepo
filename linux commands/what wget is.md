**`wget`** adalah salah satu command-line tool di Linux yang digunakan untuk **mengunduh file** dari web melalui protokol seperti HTTP, HTTPS, dan FTP. Tool ini dirancang untuk bekerja tanpa antarmuka grafis dan sangat berguna untuk mengotomatisasi unduhan atau melakukan pengambilan data di latar belakang.

---

### **Fungsi Utama `wget`**
1. **Mengunduh File**: Dapat mengunduh file tunggal dari URL.
2. **Melanjutkan Unduhan yang Terputus**: Mendukung pengunduhan file yang terputus karena gangguan jaringan.
3. **Mengunduh Direktori**: Bisa mengunduh seluruh situs web atau direktori dengan opsi rekursif.
4. **Pengunduhan Background**: Dapat berjalan di latar belakang tanpa pengawasan.
5. **Mendukung Proksi**: Bisa digunakan dengan server proksi.

---

### **Sintaks Dasar**
```bash
wget [opsi] [URL]
```

---

### **Contoh Penggunaan `wget`**

#### 1. **Mengunduh File Tunggal**
```bash
wget https://example.com/file.zip
```

#### 2. **Mengubah Nama File Hasil Unduhan**
```bash
wget -O custom_name.zip https://example.com/file.zip
```

#### 3. **Melanjutkan Unduhan yang Terputus**
```bash
wget -c https://example.com/largefile.zip
```

#### 4. **Mengunduh Situs Web Secara Rekursif**
```bash
wget --mirror --convert-links --no-parent https://example.com/
```
- **`--mirror`**: Mengunduh seluruh situs.
- **`--convert-links`**: Mengubah tautan agar berfungsi secara lokal.
- **`--no-parent`**: Tidak mengunduh direktori di atas direktori target.

#### 5. **Membatasi Kecepatan Unduh**
```bash
wget --limit-rate=200k https://example.com/file.zip
```
- Membatasi kecepatan unduhan hingga 200 KB/s.

#### 6. **Unduh dengan Autentikasi**
```bash
wget --user=username --password=password https://example.com/securefile.zip
```

#### 7. **Menggunakan File Daftar URL**
Jika Anda memiliki banyak URL untuk diunduh:
```bash
wget -i list_of_urls.txt
```

#### 8. **Mode Background**
```bash
wget -b https://example.com/largefile.zip
```
- **`-b`**: Mengunduh file di latar belakang.

#### 9. **Melewati Sertifikat SSL**
Jika menghadapi masalah sertifikat SSL:
```bash
wget --no-check-certificate https://example.com/file.zip
```

---

### **Manfaat `wget`**
- **Ringan dan Cepat**: Ideal untuk server atau sistem yang tidak memiliki GUI.
- **Mudah Diotomatisasi**: Bisa digunakan dalam skrip untuk pengunduhan massal atau terjadwal.
- **Ketersediaan Luas**: Sudah tersedia di sebagian besar distribusi Linux dan dapat diinstal dengan mudah jika belum ada.

---

### **Instalasi `wget`**
Jika `wget` belum terinstal di sistem Anda, Anda dapat menginstalnya dengan perintah berikut:
- **Ubuntu/Debian**:
  ```bash
  sudo apt update
  sudo apt install wget
  ```
- **Fedora/RHEL**:
  ```bash
  sudo dnf install wget
  ```

---

=============================================================================

Untuk mengunduh seluruh isi direktori dari sebuah website lokal (atau bahkan website online yang memungkinkan akses direktori secara langsung), Anda dapat menggunakan **`wget`** dengan opsi rekursif. Berikut langkah-langkahnya:

---

### **Langkah Mengunduh Semua Direktori dengan `wget`**

1. **Gunakan `wget` dengan opsi rekursif**:
   ```bash
   wget -r -np -nH --cut-dirs=1 -R "index.html*" <URL-direktori>
   ```

2. **Penjelasan Opsi**:
   - **`-r`**: Rekursif, untuk mengunduh semua file dan subdirektori.
   - **`-np`**: No Parent, mencegah wget naik ke direktori induk.
   - **`-nH`**: No Host, agar tidak membuat folder berdasarkan nama domain di direktori hasil unduhan.
   - **`--cut-dirs=N`**: Menghapus N tingkat direktori dari struktur yang diunduh.
     - Misalnya, untuk URL `http://example.com/folder/subfolder/`, jika Anda ingin mulai dari `subfolder`, gunakan `--cut-dirs=2`.
   - **`-R "index.html*"`**: Mengabaikan file `index.html` (yang biasanya otomatis diunduh).
   - **`<URL-direktori>`**: URL direktori yang ingin Anda unduh.

3. **Contoh**:
   Jika direktori yang ingin diunduh ada di `http://localhost/data/`:
   ```bash
   wget -r -np -nH --cut-dirs=1 -R "index.html*" http://localhost/data/
   ```

---

### **Catatan Penting**
- **Izin Akses**: Pastikan direktori yang ingin Anda unduh di-host oleh server dengan pengaturan yang mengizinkan pengindeksan direktori (biasanya terlihat dengan tampilan seperti daftar folder dan file).
- **Ukuran Unduhan**: Jika direktori memiliki file besar atau banyak file, pastikan Anda memiliki ruang penyimpanan yang cukup di sistem Anda.
- **Rate Limiting (Opsional)**: Jika server memiliki batas bandwidth, tambahkan opsi `--limit-rate`. Misalnya:
  ```bash
  wget --limit-rate=500k -r -np -nH --cut-dirs=1 -R "index.html*" http://localhost/data/
  ```
- **Proxy atau VPN**: Jika server lokal membutuhkan akses melalui jaringan tertentu, pastikan konfigurasi proxy atau VPN sudah sesuai.

---

Dengan perintah ini, seluruh isi direktori beserta subdirektorinya akan diunduh ke folder lokal Anda. Anda dapat menyesuaikan opsi berdasarkan kebutuhan spesifik Anda! 😊
