Untuk mengubah warna hyperlink (tautan) di HTML agar tidak berwarna biru kusam (warna default browser), kamu bisa menggunakan CSS.

Berikut cara-caranya:

---

### ✅ **1. Inline CSS (langsung di tag `<a>`)**

```html
<a href="https://example.com" style="color: #ff6600;">Tautan Berwarna</a>
```

* `color: #ff6600;` bisa diganti dengan warna lain (nama warna atau kode HEX/RGB).

---

### ✅ **2. Internal CSS (di dalam tag `<style>` di `<head>`)**

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    a {
      color: #ff6600;
      text-decoration: none; /* jika ingin menghilangkan garis bawah */
    }

    a:hover {
      color: #cc3300; /* saat mouse diarahkan ke link */
    }
  </style>
</head>
<body>
  <a href="https://example.com">Tautan Stylish</a>
</body>
</html>
```

---

### ✅ **3. External CSS (jika pakai file `.css` terpisah)**

File: `style.css`

```css
a {
  color: #ff6600;
  text-decoration: none;
}

a:hover {
  color: #cc3300;
}
```

File HTML:

```html
<link rel="stylesheet" href="style.css">
<a href="https://example.com">Tautan dari CSS</a>
```

---

### 🎨 Tips Warna

* Warna yang sering digunakan untuk hyperlink modern:

  * `#007BFF` (biru muda Bootstrap)  `#9cf`
  * `#FF6600` (oranye terang)
  * `#1DB954` (hijau Spotify)
  * `#000` atau `#333` untuk gaya minimalis
