Ada beberapa alasan kenapa gambar di sebuah website **tidak bisa disimpan langsung** (misalnya dengan klik kanan > "Save image as"). Namun, gambar tersebut biasanya tetap bisa disimpan dengan beberapa cara berikut:

---

### ✅ **Cara Menyimpan Gambar yang Tidak Bisa Di-save:**

#### 1. **Gunakan Screenshot**

* **Windows:** Tekan `Windows + Shift + S`, pilih area gambar, lalu paste di Paint atau aplikasi lain dan simpan.
* **Mac:** Tekan `Cmd + Shift + 4`, lalu pilih area gambar.

> Cocok untuk: Gambar yang tidak terlalu besar atau tidak perlu resolusi tinggi.

---

#### 2. **Lihat di Developer Tools (F12)**

1. Klik kanan di halaman > **Inspect** (atau tekan `F12`).
2. Pergi ke tab **Network** > pilih sub-tab **Images**.
3. Reload halaman.
4. Cari file gambar di daftar (biasanya terlihat dari ukuran dan ekstensi `.jpg`, `.png`, `.webp`, dll).
5. Klik kanan pada file tersebut > **Open in new tab** > lalu simpan dengan klik kanan.

> Cocok untuk: Gambar yang diload secara dinamis atau sebagai latar belakang CSS.

---

#### 3. **Periksa Elemen Background Image**

Kadang gambar ditampilkan sebagai **background CSS**, bukan elemen `<img>`.

1. Klik kanan gambar > **Inspect**.
2. Lihat di panel Styles, cari `background-image: url(...)`.
3. Salin URL-nya, buka di tab baru, lalu simpan.

---

#### 4. **Gunakan Ekstensi Browser**

Ada ekstensi yang membantu mengambil gambar tersembunyi atau yang dilindungi:

* **Image Downloader** (Chrome)
* **DownThemAll!** (Firefox)

---

#### 5. **Gunakan Tools Pihak Ketiga**

Beberapa aplikasi atau situs online bisa mengunduh gambar dari URL atau tangkap layar dengan resolusi tinggi:

* **JDownloader** (desktop)
* **Screenshot Guru** (untuk screenshot website penuh)

---

### ⚠️ Catatan Penting

* Jika gambar dilindungi oleh **hak cipta atau aturan situs**, pastikan kamu menyimpannya hanya untuk **penggunaan pribadi**, bukan komersial.
* Beberapa situs pakai **overlay transparan** untuk mencegah klik kanan — tapi gambar tetap bisa diambil via Developer Tools.

---
