Kamu bisa menggunakan `xargs` untuk menggabungkan beberapa baris menjadi satu baris dengan spasi sebagai pemisah. Berikut adalah caranya:

```bash
xargs < file.txt
```

### Penjelasan:
- `xargs` membaca input dari `file.txt`, menghapus newline (`\n`), dan menggantikannya dengan spasi secara otomatis.

### Contoh:
Misalkan `file.txt` berisi:
```
baris1
baris2
baris3
```
Jika menjalankan:
```bash
xargs < file.txt
```
Hasilnya:
```
baris1 baris2 baris3
```

Jika ingin hasilnya disimpan ke dalam file baru:
```bash
xargs < file.txt > output.txt
```

Gunakan `xargs` jika ingin solusi yang sederhana dan cepat! 🚀
