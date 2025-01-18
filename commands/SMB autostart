Untuk menjalankan perintah `systemctl restart smbd` secara otomatis setelah komputer dihidupkan, kamu dapat menggunakan beberapa metode berikut:

### **Metode 1: Menggunakan systemd Service Override (Rekomendasi)**
1. Buat file override untuk `smbd` service:
   ```bash
   sudo systemctl edit smbd
   ```
2. Tambahkan konfigurasi berikut:
   ```ini
   [Service]
   ExecStartPost=/bin/systemctl restart smbd
   ```
3. Simpan dan tutup editor.
4. Jalankan perintah ini agar perubahan diterapkan:
   ```bash
   sudo systemctl daemon-reload
   ```

### **Metode 2: Menambahkan Perintah ke crontab**
1. Edit crontab untuk root user:
   ```bash
   sudo crontab -e
   ```
2. Tambahkan baris berikut untuk menjalankan perintah setelah boot:
   ```bash
   @reboot systemctl restart smbd
   ```

### **Metode 3: Menggunakan rc.local (Metode Lama)**
1. Edit file `/etc/rc.local`:
   ```bash
   sudo nano /etc/rc.local
   ```
2. Tambahkan perintah berikut sebelum `exit 0`:
   ```bash
   systemctl restart smbd
   ```
3. Pastikan file tersebut executable:
   ```bash
   sudo chmod +x /etc/rc.local
   ```

### **Metode 4: Membuat systemd Service Custom**
1. Buat file service baru:
   ```bash
   sudo nano /etc/systemd/system/restart-smbd.service
   ```
2. Isi dengan konfigurasi berikut:
   ```ini
   [Unit]
   Description=Restart SMB Daemon
   After=network.target

   [Service]
   Type=oneshot
   ExecStart=/bin/systemctl restart smbd

   [Install]
   WantedBy=multi-user.target
   ```
3. Simpan file dan reload systemd:
   ```bash
   sudo systemctl daemon-reload
   ```
4. Aktifkan service agar berjalan saat boot:
   ```bash
   sudo systemctl enable restart-smbd.service
   ```

### **Metode yang Direkomendasikan:**
Metode 4 adalah yang paling disarankan karena membuat service khusus yang lebih fleksibel dan mudah dikelola dengan systemd.
