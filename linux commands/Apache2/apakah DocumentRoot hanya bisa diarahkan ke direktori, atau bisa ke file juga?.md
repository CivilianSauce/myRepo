Jawaban singkat dan tegas:
**`DocumentRoot` di Apache *harus* menunjuk ke direktori, bukan ke file.**

Dan ini bukan batasan sepele, tapi **konsep dasar cara kerja web server**.

---

## Kenapa `DocumentRoot` tidak boleh ke file

### 1. `DocumentRoot` = akar *namespace* URL

Apache memetakan URL seperti ini:

```
URL path        → filesystem path
/               → DocumentRoot
/index.html     → DocumentRoot/index.html
/foo/bar.txt    → DocumentRoot/foo/bar.txt
```

Kalau `DocumentRoot` menunjuk ke file:

* `/` tidak punya arti
* `/index.html` jadi ambigu
* mapping URL → file **rusak secara konsep**

Apache butuh:

> satu direktori sebagai akar pohon

---

### 2. Apache melakukan banyak operasi berbasis direktori

Contoh:

* directory index (`DirectoryIndex`)
* permission traversal (`+x` pada direktori)
* `.htaccess`
* autoindex
* symlink
* content negotiation

Semua ini **diasumsikan bekerja pada direktori**.

---

### 3. Ini bukan cuma Apache

Semua web server arus utama:

* Apache
* Nginx
* Lighttpd

Menggunakan model:

> URL tree → directory tree

Bukan:

> URL → satu file

---

## Tapi… “aku cuma mau satu file doang”

Ini keinginan yang **masuk akal**, dan Apache *menyediakannya* — **dengan cara yang benar**.

### Cara-cara yang *benar*:

## Solusi paling tepat: **DirectoryIndex**

Ini **cara standar**, bersih, dan intended.

### Contoh konfigurasi Apache

```apache
<VirtualHost *:80>
    ServerName graph.net
    DocumentRoot /var/www/graph

    DirectoryIndex text.txt

    <Directory /var/www/graph>
        Require all granted
    </Directory>
</VirtualHost>
```

Isi direktori:

```
/var/www/graph/
└── text.txt
```

Hasil:

* `http://graph.net/` → menampilkan `text.txt`
* URL tetap bersih
* Model Apache **tidak dilanggar**

---

## Kalau filenya **bukan** `index.html`

Tidak masalah sama sekali.
`DirectoryIndex` boleh menunjuk ke:

* `.txt`
* `.php`
* apa pun yang Apache bisa serve

---

## Alternatif (kalau kamu ingin “tegas ke satu file”)

### Pakai `Alias`

```apache
<VirtualHost *:80>
    ServerName graph.net

    Alias / /var/www/graph/text.txt

    <Directory /var/www/graph>
        Require all granted
    </Directory>
</VirtualHost>
```

Ini juga valid, tapi:

* lebih “keras”
* kurang fleksibel kalau nanti ada file lain
