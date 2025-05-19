zsteg adalah tool untuk steganalisis file gambar, terutama format PNG dan BMP. Sayangnya, zsteg tidak tersedia langsung di repositori Termux secara default, karena:

1. zsteg ditulis dalam Ruby.


2. Ruby dan dependensi native-nya kadang rumit dipasang di Termux.



Namun, kamu tetap bisa mencoba menginstalnya secara manual di Termux dengan beberapa langkah:

Langkah install zsteg di Termux (coba manual):

1. Install Ruby & dependencies:

pkg update
pkg install ruby libjpeg-turbo libpng zlib git


2. Install zsteg:

gem install zsteg

Jika ada error soal native extension (misalnya fastimage), kamu mungkin perlu tambahkan:

gem install zsteg -- --use-system-libraries


3. Cek apakah berhasil:

zsteg --help



Jika tetap gagal karena arsitektur atau dependensi, alternatifnya adalah:

Alternatif:

Gunakan di Linux lewat VM atau chroot.

Gunakan via Docker di komputer.

Coba Termux proot-distro dan install distribusi seperti Ubuntu, lalu install zsteg di sana seperti biasa.
