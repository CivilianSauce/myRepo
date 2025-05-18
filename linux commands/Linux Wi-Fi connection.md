```
# Pindai SSID yang tersedia
└─$ nmcli device wifi list

# Sambungkan ke SSID yang dituju
└─$ nmcli device wifi connect "SSID" password "password_wifi"

# Cek statusnya
└─$ nmcli connection show --active  #status

# Untuk memutus koneksi 
└─$ nmcli device disconnect wlan0
   atau
└─$ nmcli connection down "SSID"
```
