Ya, **Lighttpd bisa melakukan redirect** menggunakan **mod_redirect** atau **mod_rewrite**, tergantung pada kebutuhanmu.  

Berikut beberapa cara redirect di Lighttpd:  

---

## **1. Redirect Permanen (301) atau Sementara (302)**
Kalau ingin mengarahkan **seluruh lalu lintas** dari satu domain ke domain lain, gunakan **mod_redirect**.

🔹 **Contoh Redirect 301 (permanen) dari `oldsite.com` ke `newsite.com`**  

Buka file konfigurasi Lighttpd:
```bash
sudo nano /etc/lighttpd/lighttpd.conf
```
Tambahkan:
```
server.modules += ( "mod_redirect" )

$HTTP["host"] == "oldsite.com" {
    url.redirect = ( "^/(.*)" => "https://newsite.com/$1" )
}
```
Simpan (`CTRL+X`, `Y`, `ENTER`), lalu restart:
```bash
sudo systemctl restart lighttpd
```

Sekarang setiap permintaan ke `oldsite.com` akan diarahkan ke `newsite.com` dengan kode **301 Moved Permanently**.

---

## **2. Redirect dari HTTP ke HTTPS**
Kalau ingin memaksa semua pengguna HTTP ke HTTPS:

Tambahkan ini ke **lighttpd.conf**:
```
$HTTP["scheme"] == "http" {
    url.redirect = ( ".*" => "https://example.com$0" )
}
```
Atau kalau pakai port spesifik:
```
$SERVER["socket"] == ":80" {
    url.redirect = ( ".*" => "https://example.com$0" )
}
```
Restart Lighttpd:
```bash
sudo systemctl restart lighttpd
```

Sekarang semua yang mengakses `http://example.com` akan otomatis diarahkan ke `https://example.com`.

---

## **3. Redirect Halaman Tertentu dengan `mod_redirect`**
Jika hanya ingin mengalihkan halaman tertentu:

```
$HTTP["host"] == "example.com" {
    url.redirect = (
        "/oldpage.html" => "/newpage.html",
        "/blog" => "https://blog.example.com/"
    )
}
```
Ini akan mengarahkan:
- `example.com/oldpage.html` → `example.com/newpage.html`
- `example.com/blog` → `https://blog.example.com/`

---

## **4. Redirect dengan `mod_rewrite` (Lebih Fleksibel)**
Kalau ingin redirect berdasarkan pola lebih kompleks, pakai **mod_rewrite**.

🔹 **Contoh: Redirect Semua Halaman `/old/xxx` ke `/new/xxx`**  
Aktifkan modul rewrite:
```bash
sudo lighttpd-enable-mod rewrite
sudo systemctl restart lighttpd
```
Edit konfigurasi:
```bash
sudo nano /etc/lighttpd/lighttpd.conf
```
Tambahkan:
```
server.modules += ( "mod_rewrite" )

$HTTP["host"] == "example.com" {
    url.rewrite-once = (
        "^/old/(.*)$" => "/new/$1"
    )
}
```
Simpan & restart:
```bash
sudo systemctl restart lighttpd
```

Sekarang akses ke `example.com/old/something` akan diarahkan ke `example.com/new/something`.

---

### **Kesimpulan**
✅ **Redirect 301/302** → Pakai `mod_redirect`  
✅ **Redirect HTTP ke HTTPS** → Pakai `mod_redirect`  
✅ **Redirect berdasarkan pola (regex)** → Pakai `mod_rewrite`  

Kalau ada kasus spesifik yang mau kamu coba, kasih tahu aja! 🚀
