Kalau kamu mau menggunakan `cat` untuk *melihat* **baris tertentu** dari sebuah file, sebenarnya `cat` sendiri **tidak bisa langsung** dipakai untuk itu. `cat` hanya menampilkan seluruh isi file apa adanya.

Kalau kamu mau menampilkan **baris tertentu**, biasanya dipadukan dengan tools lain, seperti `sed`, `awk`, atau `head` + `tail`.  
Contoh-contohnya:

---

### 1. Pakai `sed`
```bash
sed -n '5p' namafile.txt
```
Artinya: tampilkan hanya baris ke-5 dari `namafile.txt`.

Kalau mau baris 5 sampai 10:
```bash
sed -n '5,10p' namafile.txt
```

---

### 2. Pakai `awk`
```bash
awk 'NR==5' namafile.txt
```
Artinya: tampilkan baris ke-5.

Kalau mau range baris (misalnya 5-10):
```bash
awk 'NR>=5 && NR<=10' namafile.txt
```

---

### 3. Kombinasi `head` dan `tail`
Misalnya mau ambil baris ke-5:
```bash
head -n 5 namafile.txt | tail -n 1
```
Artinya: ambil 5 baris pertama, lalu dari situ ambil baris terakhir (berarti baris ke-5).

Kalau mau ambil baris 5 sampai 10:
```bash
head -n 10 namafile.txt | tail -n 6
```
(ambil 10 baris pertama, lalu dari situ ambil 6 baris terakhir → baris 5 sampai 10)

---

Kalau kamu mau **tetap** pakai `cat`, biasanya digabung juga misal:

```bash
cat namafile.txt | sed -n '5p'
```
Tapi itu kurang efisien dibanding langsung pakai `sed` atau `awk` langsung ke file.

---

Mau sekalian aku buatkan contoh kecil file dummy + contoh perintah lengkapnya? 🚀  
(cepat kamu bisa tes di terminal!)
