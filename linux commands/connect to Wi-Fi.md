### 1. Pindai SSID yang tersedia
```bash
nmcli device wifi list
```

### 2. Sambungkan ke SSID yang dituju
```bash
nmcli device wifi connect "SSID" password "password_wifi"
```

### 3. Cek statusnya
```bash
nmcli connection show --active  #status
```

### 4. Untuk memutus koneksi 
```bash
nmcli device disconnect wlan0
```
atau
```bash
nmcli connection down "SSID"
```
