Anda bisa mencapai kompresi video yang mirip dengan YouTube menggunakan tool offline di Linux. YouTube menggunakan kombinasi teknik **codec canggih, bitrate optimization, dan resolusi yang dinamis** untuk mengurangi ukuran file. Berikut beberapa tool dan metode yang bisa Anda gunakan di Linux:
‎
‎---
‎
‎### **1. Menggunakan FFmpeg (Tool Paling Powerful)**
‎FFmpeg adalah alat command-line yang sangat kuat untuk kompresi video. Anda bisa meniru kompresi YouTube dengan parameter yang tepat.
‎
‎#### **Contoh Kompresi dengan H.264 (mirip YouTube):**
‎```bash
‎ffmpeg -i input.mp4 -c:v libx264 -crf 23 -preset slow -c:a aac -b:a 128k -vf "scale='if(gt(iw,ih),min(1280,iw),-2)':flags=lanczos" output.mp4
‎```
‎- **`-crf 23`** (Constant Rate Factor): Nilai 18-28 (semakin besar, semakin kecil ukuran, tapi kualitas turun).
‎- **`-preset slow`** (Semakin lambat preset, semakin efisien kompresinya).
‎- **`-vf scale=...`** Menyesuaikan resolusi (misal, maksimal 1280px lebar).
‎- **`-c:a aac -b:a 128k`** Kompres audio ke AAC dengan bitrate 128kbps.
‎
‎#### **Untuk Kompresi Lebih Ekstrem (Seperti YouTube 480p):**
‎```bash
‎ffmpeg -i input.mp4 -c:v libx264 -crf 28 -preset veryslow -tune film -c:a aac -b:a 64k -vf "scale=640:-2" output_small.mp4
‎```
‎
‎#### **Menggunakan HEVC (H.265) untuk Kompresi Lebih Baik:**
‎```bash
‎ffmpeg -i input.mp4 -c:v libx265 -crf 28 -preset slow -c:a aac -b:a 128k output_h265.mp4
‎```
‎(H.265 lebih efisien daripada H.264, tetapi butuh lebih banyak waktu kompresi.)  *this is what i use
‎
‎---
‎
‎### **2. Menggunakan HandBrake (GUI & CLI)**
‎HandBrake adalah frontend untuk FFmpeg dengan preset mudah digunakan.
‎- Install:  
‎  ```bash
‎  sudo apt install handbrake handbrake-cli
‎  ```
‎- Contoh CLI:
‎  ```bash
‎  HandBrakeCLI -i input.mp4 -o output.mp4 --preset="Fast 1080p30" --quality=22 --audio-bitrate=128
‎  ```
‎
‎---
‎
‎### **3. Menggunakan MPV + Shaders untuk Kompresi Lossless**
‎Jika Anda ingin mengurangi ukuran **tanpa kehilangan kualitas**, Anda bisa menggunakan:
‎```bash
‎ffmpeg -i input.mp4 -c:v libx264 -crf 0 -preset ultrafast lossless_output.mp4
‎```
‎(Tapi file akan tetap besar, tidak seperti YouTube.)
‎
‎---
‎
‎### **4. Optimasi dengan Tiny Encoder (Alternatif Ringan)**
‎```bash
‎ffmpeg -i input.mp4 -c:v libx264 -b:v 800k -c:a aac -b:a 96k -movflags +faststart output_lowbitrate.mp4
‎```
‎(Menggunakan bitrate tetap untuk kontrol lebih ketat.)
‎
‎---
‎
‎### **5. Mengurangi Frame Rate (Jika Tidak Perlu 60fps)**
‎```bash
‎ffmpeg -i input.mp4 -r 24 -c:v libx264 -crf 23 output_24fps.mp4
‎```
‎
‎---
‎
‎### **Perbandingan Hasil:**
‎| Tool/Metode | Ukuran Output | Kualitas | Kecepatan Kompresi |
‎|-------------|--------------|----------|-------------------|
‎| `x264 (CRF 23)` | ~50-70% lebih kecil | Baik | Cepat |
‎| `x265 (CRF 28)` | ~40-60% lebih kecil | Sangat Baik | Lambat |
‎| `Bitrate Rendah (800k)` | Sangat Kecil | Sedang | Cepat |
‎
‎---
‎
‎### **Kesimpulan:**
‎- **Untuk hasil terbaik** → Gunakan **H.265 (libx265)** dengan `-crf 28` dan `-preset slow`.
‎- **Untuk kompatibilitas luas** → Gunakan **H.264 (libx264)** dengan `-crf 23`.
‎- **Jika ukuran lebih penting daripada kualitas** → Turunkan resolusi (`-vf scale=640:-2`) dan gunakan bitrate rendah.
‎
‎Anda bisa bereksperimen dengan parameter untuk mendapatkan hasil yang optimal sesuai kebutuhan. 🚀
