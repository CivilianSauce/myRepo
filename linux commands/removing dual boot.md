### 1. Jalankan gparted
```bash
sudo apt install gparted                                                                        
sudo gparted
### Hapus partisi OS yang ingin dihapus
```

### 2. Masuk ke direktori EFI
```bash
cd /boot/efi/EFI 
```

### 3. Hapus direktori EFI OS yang ingin dihapus
```bash
rm -rf /boot/efi/EFI/ubuntu
```

### 4. Update GRUB
```bash
sudo update-grub
```

### 5. Ketik command ini untuk melihat semua boot yang ada
```bash
efibootmgr                                                                                               
```
output:
```bash
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0004,0001,0000
Boot0000* Ubuntu        HD(1,GPT,718b0465-9c28-4f6f-9b0a-bbd8688b5886,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Hard Drive    BBS(HD,,0x0)0000474f00004e4fad000000010000006f005700440043002000570044003500300030003000410041004a0053002d00300030004c0041003700300000000501090002000000007fff040002010c00d041030a0000000001010600001703120a000000ffff00007fff040001043e00ef47642dc93ba041ac194d51d01b4ce64400570057002d00430043004d0034004c004a004e0059003000590020005400200020002000200000007fff04000000424f
Boot0004* kali  HD(1,GPT,718b0465-9c28-4f6f-9b0a-bbd8688b5886,0x800,0x100000)/File(\EFI\KALI\GRUBX64.EFI)
```

### 6. Karena di sini yang kita ingin hapus adalah Ubuntu, maka ketik angka yang sesuai dengan angka pada Ubuntu
```bash
sudo efibootmgr -b 0000 -B     
```

### 7. Keluar dan restart PC
```bash
sudo reboot                                                                                      
```
