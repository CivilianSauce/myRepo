#### jika kita perlu index.html di setiap direktori documentroot website agar tetap menampilkan sesuatu, apakah command `cp index.html ./*/` bisa berlaku jika sifat tiap direktorinya homogen?

---

Command `cp index.html ./*/` **tidak akan berjalan seperti yang kamu harapkan**, meskipun semua direktori dalam `./` homogen. Ini karena:

* Shell akan melakukan ekspansi `./*/` menjadi daftar direktori (misal: `./dir1/ ./dir2/ ./dir3/`)
* Lalu command itu menjadi:

  ```bash
  cp index.html ./dir1/ ./dir2/ ./dir3/
  ```
* **Ini artinya** `cp` akan menyalin `index.html` ke *semua direktori tersebut*, **tetapi hanya menyalin satu file ke semua tujuan**, dan bukan ke dalam masing-masing direktori dengan nama tetap (`index.html`).

Dan ini **berfungsi seperti yang kamu inginkan** **hanya jika**:

* Semua entri dalam `./*/` memang direktori.
* Tidak ada wildcard yang menghasilkan error (misal, jika tidak ada subdirektori, `./*/` akan tetap ada di argumen, dan `cp` bisa error).

---

### Alternatif yang lebih aman dan eksplisit:

Kalau kamu ingin memastikan `index.html` ada di setiap subdirektori dari document root (misal di `./dir1/index.html`, `./dir2/index.html`, dll), lebih baik pakai loop:

```bash
for dir in ./*/; do
  cp index.html "$dir"
done
```

Atau jika kamu ingin memastikan hanya direktori yang valid:

```bash
for dir in */; do
  [ -d "$dir" ] && cp index.html "$dir"
done
```

Kalau kamu ingin memastikannya juga di sub-subdirektori (rekursif), kamu bisa pakai `find`:

```bash
find . -type d -exec cp index.html {}/ \;
```

---

### Kesimpulan:

* `cp index.html ./*/` **mungkin bekerja** untuk kasus sederhana, tapi **tidak aman secara universal**.
* Gunakan loop (`for` atau `find`) agar lebih jelas dan aman, terutama jika kamu ingin hasilnya konsisten dan tidak tergantung pada ekspansi shell.
