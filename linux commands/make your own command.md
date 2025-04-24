Untuk membuat symlink dan script yang dipanggil dari mana pun dengan kita membuat perintah bash sendiri, ini adalah caranya.

---

### 🔧 Berikut Langkahnya:

1. **Script** (misal `/home/kamu/bin/ida`):

   ```bash
   #!/bin/bash
   wine /home/kamu/Downloads/Apps/IDA_8.3/83readytorelease/ida64.exe
   ```

2. **Permission:**

   ```bash
   chmod +x /home/kamu/bin/ida
   ```

3. **Symlink:**

   ```bash
   sudo ln -s /home/kamu/bin/ida /usr/local/bin/ida
   ```

Setelah itu, `ida` bisa dipanggil dari mana pun tanpa masalah.

---

Kalau kamu pengen setup ini jadi template untuk command-command lain kayak `ghidra`, `ollydbg`, atau bahkan tools custom kamu sendiri, tinggal ganti path-nya aja.
Butuh template-nya? Aku bisa bantuin juga 😄
