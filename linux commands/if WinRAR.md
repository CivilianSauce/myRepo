Secara langsung, **WinRAR** tidak tersedia untuk Linux dalam versi grafis seperti di Windows. Tapi kamu masih bisa menangani file RAR di Linux dengan beberapa cara:

### 1. **Menggunakan `unrar`**

`unrar` adalah tool command-line resmi dari pembuat WinRAR. Untuk memasangnya:

```bash
sudo apt install unrar   # untuk Debian/Ubuntu
```

Contoh penggunaan:

```bash
unrar x file.rar   # untuk mengekstrak file
```

> Catatan: Ada juga `unrar-free`, tapi fiturnya terbatas dan tidak selalu bisa membuka RAR versi baru.

---

### 2. **Menggunakan `7z` (7-Zip versi Linux)**

Instal dulu:

```bash
sudo apt install p7zip-full
```

Kemudian ekstrak:

```bash
7z x file.rar
```

---

### 3. **GUI Alternatif**

Kalau kamu ingin antarmuka grafis (GUI), ada beberapa alternatif seperti:

* **PeaZip** (punya GUI dan dukung RAR)
* **Ark** (di KDE, bisa pakai `unrar` di belakang layar)
* **File Roller** (di GNOME, juga butuh `unrar` terinstal)

---

Jadi, meskipun **WinRAR** versi Windows tidak tersedia di Linux, kamu tetap bisa membuka file RAR dengan alat-alat lain yang setara.
