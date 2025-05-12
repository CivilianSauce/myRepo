### SMB

How to mount it
```bash
sudo mkdir /mnt/smb
sudo chmod 775 /mnt/smb
sudo mount -t cifs //server_address/share_name /mnt/smb -o username=your_username,password=your_password
cd /mnt/smb
ls
```

How to unmount it
```bash
sudo umount /mnt/smb
```
---

### FTP

How to mount it
```bash
sudo mkdir /mnt/ftp
sudo chmod 775 /mnt/ftp
curlftpfs ftp://username:password@ftp_server /mnt/ftp
cd /mnt/ftp
ls
```

How to unmount it
```bash
sudo umount /mnt/ftp
```
