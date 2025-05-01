Di GitHub (dan hampir semua platform yang mendukung Markdown), ada beberapa **sintaks khusus** yang sering dipakai untuk membuat tampilannya lebih terstruktur dan enak dibaca, apalagi buat dokumentasi teknis. Salah satunya yang kamu sebut: **tiga buah backtick (`) untuk membuat blok kode**.

Berikut beberapa sintaks penting di GitHub-flavored Markdown:

---

### 🔹 Blok Kode
Untuk membuat **blok kode** seperti command line, potongan kode Python, atau lainnya:

\`\`\` (tiga backtick)  
````markdown
```bash
ls -la
cd /home/user
```
````

Bisa juga tambahkan nama bahasanya setelah backtick untuk **highlight syntax**:

```markdown
```python
def hello():
    print("Halo dunia!")
```
```

---

### 🔹 Inline Code
Untuk kode pendek di dalam kalimat, pakai satu backtick:

```markdown
Gunakan perintah `ls` untuk melihat isi folder.
```

---

### 🔹 Checklist
Untuk membuat to-do list atau checklist (interaktif di GitHub):

```markdown
- [ ] Belajar Markdown
- [x] Minum kopi
```

---

### 🔹 Tabel
```markdown
| Nama  | Umur | Kota     |
|-------|------|----------|
| Ani   | 20   | Jakarta  |
| Budi  | 22   | Bandung  |
```

---

### 🔹 Blockquote (Kutipan)
```markdown
> Ini adalah kutipan inspiratif.
```

---

### 🔹 Gambar
```markdown
![Alt Text](https://link.ke.gambar.jpg)
```
