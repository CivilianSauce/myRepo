kita masuk ke **Samba read-only share**, di mana kamu ingin orang **bisa melihat dan mengakses file**, tapi **tidak bisa mengubah atau menambahkan apapun**.

---

## 🧭 Tujuan:

Kamu ingin folder di-share via Samba, **tapi hanya untuk dibaca** (seperti katalog atau tempat download).

---

## 🧱 Langkah-langkah

Misal kamu ingin share folder `/mnt/data/public` secara **read-only**.

---

### 1. **Pastikan Samba sudah terinstal**

```bash
sudo apt update
sudo apt install samba
```

---

### 2. **Edit konfigurasi Samba**

Buka file konfigurasi:

```bash
sudo nano /etc/samba/smb.conf
```

Lalu tambahkan di bagian bawah (atau bagian `[global]` bisa tetap, asal ini berada di bawah):

```ini
[PublicShare]
   path = /mnt/data/public
   browseable = yes
   read only = yes
   guest ok = yes
   force user = nobody
```

Penjelasan:

* `read only = yes` → inilah yang bikin Samba hanya mengizinkan baca
* `guest ok = yes` → mengizinkan akses tanpa login
* `force user = nobody` → supaya akses dilakukan sebagai user non-privileged

> Kalau kamu ingin lebih aman, bisa ganti `nobody` dengan user khusus untuk share itu.

---

### 3. **Atur permission di sistem file**

Beri izin baca saja untuk semua orang (dan eksekusi agar bisa akses direktori):

```bash
sudo chmod -R a=rX /mnt/data/public
```

atau yang lebih manual:

```bash
sudo find /mnt/data/public -type d -exec chmod 755 {} \;
sudo find /mnt/data/public -type f -exec chmod 644 {} \;
```

* Direktori → `755` = `rwxr-xr-x`
* File → `644` = `rw-r--r--`

---

### 4. **Restart Samba**

```bash
sudo systemctl restart smbd
```

---

## ✅ Hasilnya:

* Folder bisa diakses oleh siapa pun di jaringan (tergantung firewall).
* Semua file **bisa dibaca dan disalin**, tapi **tidak bisa dihapus, diganti, atau ditulis** dari Windows maupun Linux.

---
yang mungkin ditanyakan:

---

## 🔍 Penjelasan `chmod -R a=rX`

### Format simbolik:

```
chmod [siapa]=[izin]
```

### Rinciannya:

* `-R` → recursive: semua file dan folder di dalam juga diubah
* `a` = **all** (owner, group, others)
* `=` → mengganti permission dengan yang ditentukan
* `r` = read
* `X` (huruf besar!) = **execute hanya jika itu direktori, atau file yang sudah executable**

> `X` berbeda dengan `x` biasa.
>
> * `x` → selalu memberi permission eksekusi
> * `X` → **conditional**: hanya memberi `x` jika:
>
>   * target adalah direktori
>   * atau target file sudah punya `x`

---

## 🤔 Kenapa pakai `X`, bukan `x`?

Karena:

* Kamu **nggak mau semua file jadi executable** (bayangkan `.txt`, `.jpg` jadi punya `x` 😬)
* Tapi kamu **butuh semua direktori bisa diakses (`cd`)**, dan direktori butuh `x` untuk itu

Dengan `X`, kita bisa:

✅ Memberi `x` ke direktori
❌ Tanpa memberi `x` ke file biasa

---

## 🧪 Contoh Perilaku `chmod -R a=rX`

Misal struktur:

```
public/
├── info.txt
└── subfolder/
    └── more.txt
```

Setelah:

```bash
chmod -R a=rX public/
```

Izin jadi:

```
dr-xr-xr-x  public
-r--r--r--  public/info.txt
dr-xr-xr-x  public/subfolder
-r--r--r--  public/subfolder/more.txt
```

Hasilnya:

* Semua bisa lihat isi folder dan file
* Tidak ada file yang executable
* Semua folder bisa dimasuki (`x` ada)

---

## 📌 Singkatnya:

| Perintah        | Arti                                                                         |
| --------------- | ---------------------------------------------------------------------------- |
| `chmod 755`     | Set izin ke `rwxr-xr-x` (angka, tidak selektif antara file dan folder)       |
| `chmod -R a=rX` | Set semua jadi read-only, tapi direktori tetap bisa diakses (`cd`)           |
| `chmod -R a+rx` | Tambah `r` dan `x` ke semua (termasuk file, jadi file juga bisa executable!) |
