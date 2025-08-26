Untuk melihat ukuran storage dan sisa ruang kosong di Linux, kamu bisa menggunakan beberapa perintah berikut:

### 1. **`df` (disk free)**

Menampilkan penggunaan disk dari filesystem.

```bash
df -h
```

**Penjelasan opsi:**

* `-h` : Menampilkan ukuran dalam format yang mudah dibaca manusia (KB, MB, GB)

Contoh output:

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   20G   28G  42% /
tmpfs           2.0G     0  2.0G   0% /dev/shm
```

---

### 2. **`lsblk` (list block devices)**

Menampilkan daftar perangkat penyimpanan (disk dan partisi), termasuk ukurannya.

```bash
lsblk
```

Contoh output:

```
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda      8:0    0   50G  0 disk 
├─sda1   8:1    0   50G  0 part /
```

Jika ingin dengan ukuran yang terbaca manusia:

```bash
lsblk -h
```

---

### 3. **`du` (disk usage)** – *opsional, untuk lihat penggunaan per direktori*

Menampilkan penggunaan ruang disk oleh file/direktori.

Contoh:

```bash
du -sh /home
```

Menampilkan total penggunaan ruang di `/home`.

---

### 4. **`ncdu`** (jika tersedia)

Alat interaktif berbasis terminal untuk melihat penggunaan disk.

Install dulu (jika belum ada):

```bash
sudo apt install ncdu      # Untuk Debian/Ubuntu
sudo yum install ncdu      # Untuk CentOS/RHEL
```

Jalankan:

```bash
ncdu /
```

---

Kalau hanya ingin tahu total kapasitas dan sisa space, `df -h` sudah paling umum digunakan.



apakah command itu bisa dijalankan otomatis misalnya seminggu sekali sebagai laporan?



Ya, sangat bisa! Kamu bisa menjadwalkan command seperti `df -h` agar berjalan otomatis seminggu sekali dan hasilnya dikirimkan ke file log atau dikirim lewat email. Di Linux, ini bisa dilakukan menggunakan **cron** (scheduler bawaan Linux).

Berikut langkah-langkahnya:

---

## ✅ **Langkah 1: Buat script-nya**

Buat file script, misalnya `disk_report.sh`.

```bash
#!/bin/bash
DATE=$(date +%Y-%m-%d)
LOGFILE="/var/log/disk_report_$DATE.log"

echo "Disk Usage Report - $DATE" > "$LOGFILE"
df -h >> "$LOGFILE"
```

**Pastikan file-nya executable:**

```bash
chmod +x disk_report.sh
```

---

## ✅ **Langkah 2: Tambahkan ke Cron**

Edit crontab:

```bash
crontab -e
```

Lalu tambahkan baris ini untuk menjalankannya seminggu sekali, misalnya setiap Senin jam 07:00:

```cron
0 7 * * 1 /path/to/disk_report.sh
```

Penjelasan:

* `0 7 * * 1` = setiap hari Senin jam 07:00
* Ganti `/path/to/disk_report.sh` dengan path asli file kamu

---

## ✅ (Opsional) Kirim Laporan via Email

Kalau ingin dikirim via email, kamu bisa tambahkan di script-nya:

```bash
mail -s "Laporan Disk Mingguan" you@example.com < "$LOGFILE"
```

**Pastikan `mailutils` atau `mailx` sudah terinstal:**

```bash
sudo apt install mailutils
```

---

Kalau **tanpa pengiriman email**, kamu bisa **menyimpan laporan-laporan otomatis itu ke file** (misalnya di `/var/log/` atau direktori khusus), lalu melihatnya kapan saja dengan command seperti `cat`, `less`, atau `tail`.

---

## ✅ Lokasi Laporan

Misalnya dalam script kamu buat seperti ini:

```bash
LOGFILE="/var/log/disk_report_$(date +%Y-%m-%d).log"
```

Setiap laporan akan tersimpan sebagai file harian, contoh:

```
/var/log/disk_report_2025-07-22.log
/var/log/disk_report_2025-07-15.log
```

Kalau kamu ingin menyimpan di direktori lain (yang tidak butuh sudo untuk akses), bisa pakai misalnya:

```bash
LOGFILE="$HOME/disk_reports/disk_report_$(date +%Y-%m-%d).log"
```

---

## ✅ Cara Melihat Laporan

Misalnya kamu simpan di `~/disk_reports/`:

```bash
cat ~/disk_reports/disk_report_2025-07-22.log
```

Atau untuk melihat daftar semua laporan:

```bash
ls ~/disk_reports/
```

Atau melihat isi terbaru:

```bash
tail -n 20 ~/disk_reports/disk_report_2025-07-22.log
```

---

## ✅ Contoh Script Lengkap Tanpa Email

```bash
#!/bin/bash

# Buat folder laporan jika belum ada
mkdir -p ~/disk_reports

# Nama file berdasarkan tanggal
DATE=$(date +%Y-%m-%d)
LOGFILE="$HOME/disk_reports/disk_report_$DATE.log"

# Tulis laporan
{
    echo "Laporan Disk Usage - $DATE"
    echo "============================="
    df -h
    echo ""
    echo "Penggunaan Disk per Mount Point"
    echo "------------------------------"
    du -sh /home /var /tmp 2>/dev/null
} > "$LOGFILE"
```

Simpan misalnya sebagai `~/disk_report.sh`, beri permission:

```bash
chmod +x ~/disk_report.sh
```

Lalu tambahkan ke `crontab -e`:

```cron
0 7 * * 1 ~/disk_report.sh
```
