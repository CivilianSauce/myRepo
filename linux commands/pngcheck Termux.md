Berikut panduan **paling akurat dan terbaru** untuk menginstall `pngcheck` di Termux:

---

### **1. Install alat bantu kompilasi**

```bash
pkg update
pkg install wget clang make
```

---

### **2. Unduh source resmi dari situs resminya**

```bash
wget http://www.libpng.org/pub/png/src/pngcheck-2.4.0.tar.gz
```

> Versi terbaru saat ini adalah 2.4.0 — kamu bisa cek di [http://www.libpng.org/pub/png/pngapps.html](http://www.libpng.org/pub/png/pngapps.html)

---

### **3. Ekstrak dan build**

```bash
tar -xvzf pngcheck-2.4.0.tar.gz
cd pngcheck-2.4.0
make -f Makefile.unx
```

Setelah itu, akan terbentuk file `pngcheck` (executable) di direktori tersebut.

---

### Lanjut: Pindahkan ke path global (opsional tapi disarankan)

```bash
cp pngcheck $PREFIX/bin/
```

Sekarang kamu bisa jalankan dari mana saja:

```bash
pngcheck gambar.png
```
