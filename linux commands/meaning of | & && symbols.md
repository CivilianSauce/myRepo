Tanda seperti `|`, `&`, dan `&&` dalam shell Linux memiliki fungsi yang berbeda:  

1. `|` (Pipe)  
Digunakan untuk mengalirkan output dari satu perintah ke perintah lain sebagai input.  
Contoh:  
```bash
ls -l | grep ".txt"
```  
- `ls -l` menampilkan daftar file dalam mode panjang.  
- `grep ".txt"` hanya menampilkan baris yang mengandung ".txt".  
- Jadi, command ini hanya menampilkan file dengan ekstensi .txt.  

Contoh lain:  
```bash
cat file.txt | wc -l
```  
- `cat file.txt` membaca isi file.  
- `wc -l` menghitung jumlah baris.  
- Jadi, perintah ini menampilkan jumlah baris dalam file.txt.  

2. `&` (Background Process)  
Digunakan untuk menjalankan perintah di background sehingga terminal tetap bisa digunakan.  
Contoh:  
```bash
firefox &
```  
Ini akan membuka Firefox di background, sehingga terminal tetap bisa digunakan tanpa menunggu Firefox ditutup.  

Contoh lain:  
```bash
./script.sh &
```  
Ini akan menjalankan script.sh di background.  

Untuk melihat daftar proses yang berjalan di background, gunakan:  
```bash
jobs
```  

Jika ingin membawa proses kembali ke foreground, gunakan:  
```bash
fg %1  # %1 adalah nomor job yang muncul di 'jobs'
```

3. `&&` (Logical AND)  
Digunakan untuk menjalankan perintah kedua hanya jika perintah pertama berhasil (exit code 0).  
Contoh:  
```bash
mkdir new_folder && cd new_folder
```  
- Jika `mkdir new_folder` berhasil, maka `cd new_folder` dieksekusi.  
- Jika gagal (misalnya folder sudah ada), `cd new_folder` tidak akan dijalankan.  

Contoh lain:  
```bash
sudo apt update && sudo apt upgrade -y
```  
- Jika `apt update` berhasil, maka `apt upgrade -y` akan dieksekusi.  
- Jika `apt update` gagal, `apt upgrade -y` tidak akan berjalan.  

4. `||` (Logical OR)  
Kebalikan dari `&&`, perintah kedua akan dijalankan jika perintah pertama gagal (exit code ≠ 0).  
Contoh:  
```bash
mkdir new_folder || echo "Folder sudah ada"
```  
Jika `mkdir new_folder gagal`, maka `echo "Folder sudah ada"` akan dijalankan.  

Perbedaan `;` dengan `&&`  
    `;` menjalankan semua perintah, terlepas dari keberhasilan atau kegagalan.  
    `&&` hanya menjalankan perintah kedua jika perintah pertama sukses.  

Contoh `;`:  
```bash
mkdir test; cd test
```  
`cd test` akan tetap dieksekusi, meskipun `mkdir test` gagal.  

Contoh `&&`:  
```bash
mkdir test && cd test
```  
`cd test` hanya akan berjalan jika `mkdir test` berhasil.  
