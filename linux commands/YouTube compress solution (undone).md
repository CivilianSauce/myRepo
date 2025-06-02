Ada beberapa **tool offline** yang sangat bagus untuk **mengompres video** tanpa perlu upload ke YouTube atau internet. Bahkan, banyak di antaranya memberikan kontrol lebih besar atas kualitas dan ukuran file dibandingkan metode online atau lewat YouTube. Berikut beberapa rekomendasi tool offline:

---

### ✅ 1. **HandBrake (Windows, macOS, Linux)**

* **Gratis dan open-source.**
* Mendukung banyak format video (MP4, MKV, dll).
* Bisa pilih kualitas, resolusi, codec (H.264, H.265), dan bitrate.
* Tersedia preset untuk kompresi ringan sampai tinggi.

**Kelebihan:**

> Fleksibel, cocok untuk semua level pengguna.

---

### ✅ 2. **FFmpeg (Windows, macOS, Linux)**

* Tool berbasis command line (tapi sangat powerful).
* Cocok untuk pengguna yang paham teknis.
* Bisa konversi, kompresi, ekstrak audio, dll.

**Contoh kompresi video dengan FFmpeg:**

```bash
ffmpeg -i input.mp4 -vcodec libx265 -crf 28 output.mp4
```

(CRF 23-28 adalah rentang umum untuk kompresi ringan sampai sedang.)

---

### ✅ 3. **Shotcut (Windows, macOS, Linux)**

* Editor video gratis yang juga bisa digunakan untuk **export video dengan setting kompresi tertentu**.
* Lebih user-friendly dibanding FFmpeg.

---

### ✅ 4. **Avidemux (Windows, macOS, Linux)**

* Ringan dan sederhana untuk pemotongan serta kompresi.
* Mendukung codec H.264 dan H.265.

---

### ✅ 5. **VLC Media Player (Windows, macOS, Linux)**

* Tidak hanya untuk menonton, VLC juga bisa konversi dan kompresi video.
* Menu: **Media > Convert / Save** → pilih format dan bitrate.

---

Kalau kamu ingin **hasil kompresi mirip YouTube**, biasanya cukup dengan:

* Resolusi dikurangi (misal dari 1080p ke 720p).
* Codec H.264 atau H.265.
* Bitrate disesuaikan, misal 1000–2000 kbps untuk 720p.

# *again, this is undone

Kalau kamu ingin **mengompres video dengan FFmpeg agar hasilnya mirip dengan kompresi YouTube**, kita akan fokus ke:

* Codec: `libx264` (umum & kompatibel) atau `libx265` (lebih efisien, tapi butuh lebih banyak proses)
* Bitrate: sekitar **2–3 Mbps untuk 1080p**, **1 Mbps untuk 720p**
* Audio: **AAC 128 kbps**
* Container: `.mp4`

---

### ✅ Contoh FFmpeg Command (H.264 – seperti YouTube)

```bash
ffmpeg -i input.mp4 -c:v libx264 -b:v 2500k -preset slow -c:a aac -b:a 128k -movflags +faststart output.mp4
```

**Penjelasan:**

* `-i input.mp4`: input video
* `-c:v libx264`: pakai codec H.264
* `-b:v 2500k`: target bitrate video 2.5 Mbps (cocok untuk 1080p mirip YouTube)
* `-preset slow`: kompresi lebih efisien (pilihan lain: veryfast, fast, medium, slow, slower)
* `-c:a aac -b:a 128k`: audio dikompresi jadi AAC 128 kbps
* `-movflags +faststart`: optimisasi untuk streaming (seperti YouTube lakukan)
* `output.mp4`: file output

---

### ✅ Versi Lebih Modern (H.265 – hasil lebih kecil, kualitas tetap)

```bash
ffmpeg -i input.mp4 -c:v libx265 -b:v 1500k -preset slow -c:a aac -b:a 128k -movflags +faststart output_hevc.mp4
```

* `libx265`: codec H.265 (lebih efisien dari H.264)
* `b:v 1500k`: bitrate lebih rendah dari H.264 untuk kualitas serupa

⚠️ *Note*: Tidak semua perangkat/browser support H.265, jadi pastikan kompatibel kalau mau dibagikan.

---

### ✅ Ingin File Lebih Ringan Lagi?

Untuk video 720p mirip YouTube:

```bash
ffmpeg -i input.mp4 -vf scale=1280:720 -c:v libx264 -b:v 1000k -preset slow -c:a aac -b:a 128k -movflags +faststart output_720p.mp4
```
