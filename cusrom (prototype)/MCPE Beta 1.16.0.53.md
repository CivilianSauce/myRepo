Bagus, aku rangkum ya, biar jelas dan rapi.

Dari semua obrolan kita, ini daftar lengkap path tempat Minecraft (khusus Beta 1.16.0.53 Bedrock) mungkin menyimpan dunia (save world):


---

1. Penyimpanan eksternal biasa (SDCard/Internal Storage)

Path standar sebelum Android 11:

/games/com.mojang/minecraftWorlds/

Path alternatif di Scoped Storage (jika Minecraft sudah semi-adaptasi Android 10):

/Android/data/com.mojang.minecraftpe/files/games/com.mojang/minecraftWorlds/

(Ini masih di storage biasa, tapi lebih tersembunyi.)



---

2. Penyimpanan internal aplikasi (privat, perlu root)

Path internal full protected (hanya bisa diakses Minecraft sendiri atau root):

/data/data/com.mojang.minecraftpe/files/games/com.mojang/minecraftWorlds/

atau

/data/user/0/com.mojang.minecraftpe/files/games/com.mojang/minecraftWorlds/

(/data/user/0/ ini kadang muncul di beberapa Android 10 custom.)



---

3. Penyimpanan cache atau sandbox custom (jarang, tapi mungkin)

Beberapa versi modded Minecraft atau build eksperimen bisa menyimpan di lokasi internal tersendiri dalam struktur aneh, misal:

/data/data/com.mojang.minecraftpe/cache/

atau

/data/data/com.mojang.minecraftpe/app_sandbox/games/com.mojang/minecraftWorlds/

Tapi ini jarang banget, lebih ke modded APK.



---

Kesimpulan cepat:


---

Sedikit tambahan

Kalau Minecraft PE-mu dari Play Store BETA resminya, kemungkinan besar simpan di internal privat.

Kalau Minecraft PE-mu dari APK download bebas (MCPEDL, misalnya), penyimpanan bisa aneh dan berbeda.



---

Kalau kamu mau, aku bisa bantu buatkan checklist kecil:

> "Kalau mau backup, langkah apa yang masih mungkin?"



Mau sekalian aku buatin? Biar kamu tau opsi apa saja yang masih bisa kamu ambil hari ini.
(Soalnya backup dunia ini penting banget buat jangka panjang.) Mau?

