# PKSJ
Repo untuk laporan tugas 1 PKSJ

**Anggota Kelompok**

| NRP         | Nama                     |
|-------------|--------------------------|
| 5113100050  | Freddy Hermawan Y        |
| 5113100109  | Daniel Fablius           |
| 5113100113  | Muhamad Luthfie La Roeha |

## Laporan Tugas 1

**Uji Penetrasi 1 :**
* Install sebuah virtual OS dengan Ubuntu Server
* Install SSH server dengan konfigurasi default
* Install satu lagi virtual OS dengan OS bebas
* Pastikan tools untuk SSH brute force attack sudah terinstall
* Lakukan uji penetrasi 1: dengan THC-Hydra / Ncrack dan catat hasil uji penetrasi 1

**Uji Penetrasi 2 :**
* Install fail2ban pada Ubuntu server yang telah diinstall SSH servernya
* Konfigurasilah SSH server agar tidak menggunakan setting default lagi
* Lakukan uji penetrasi 2 dengan tools yang sama dan catat hasilnya

### Pendahuluan

SSH(Secure Shell) adalah  sebuah protokol jaringan kriptografi untuk komunikasi data yang aman, login antarmuka baris perintah, perintah eksekusi jarak jauh, dan layanan jaringan lainnya antara dua jaringan komputer. Ini terkoneksi, melalui saluran aman atau melalui jaringan tidak aman, server dan klien menjalankan server SSH dan SSH program klien secara masing-masing.
Terdapat 2 versi SSH yaitu SSH 1 dan SSH 2. bedanya terletak pada mencakup kedua fitur keamanan dan peningkatan perbaikan tingkat keamanan yang disediakan.
Sebagai contoh, applikasi menggunakan ssh adalah openssh.(https://id.wikipedia.org/wiki/SSH)

SSH brute force attack adalah saat seorang di luar sistem ingin masuk ke dalam sistem yang memiliki username dan password dengan menggunakan 1 list file yang isinya adalah kumpulan dari kemungkinan password untuk username tersebut. Sehingga diperlukan waktu yang cukup lama untuk melakukan proses brute force dan itu juga terdapat kemungkinan password tidak cocok dengan password sebenarnya. (https://en.wikipedia.org/wiki/Brute-force_attack)

### Dasar Teori

**1. OS yang Digunakan**
* **Ubuntu** adalah sistem operasi lengkap berbasis Linux, tersedia secara bebas dan mempunyai dukungan baik yang berasal dari komunitas maupun tenaga ahli profesional. (https://balajarlinux.wordpress.com/2008/02/04/pengenalan-apa-itu-ubuntu-serta-sejarah/)

* **Ubuntu Server** adalah ubuntu yang didesain untuk diinstall di server. Perbedaan mendasar, di Ubuntu Server tidak tersedia GUI. Jika ingin menggunakan ubuntu server artinya user harus bekerja dengan perintah-perintah di layar hitam yang sering disebut konsole. (http://www.candra.web.id/mengenal-ubuntu-server/)

**2. Tools yang Digunakan**

*Cracking Tools*
* **Hydra** * adalah sebuah proyek software yang dikembangkan oleh sebuah organisasi bernama "The Hacker's Choice" (THC) yang menggunakan brute force dan dictionary attack untuk menguji untuk password yang lemah atau password sederhana pada satu atau banyak host remote menjalankan berbagai layanan yang berbeda. Ia dirancang sebagai bukti untuk menunjukkan kemudahan cracking password karena password yang dipilih buruk. (http://informatika.stei.itb.ac.id/~rinaldi.munir/Stmik/2010-2011/Makalah2010/MakalahStima2010-062.pdf)

* **Ncrack** * adalah alat berkecepatan tinggi scaning jaringan retak .Ncrack dibuat untuk membantu perusahaan dan untuk mengamankan jaringan mereka secara proaktif menguji semua host dan perangkat jaringan dengan password yang buruk. (http://mr-nyepik.blogspot.co.id/2014/04/download-ncrack-network-cracking-tools.html)

*Defending Tool*
* **Fail2Ban** adalah aplikasi log-parsing yang memonitor log sistem untuk mengindentifikasi serangan yang terjadi di server. Saat terjadi serangan, berdasarkan parameter yang sudah diatur sebelumnya, Fail2ban akan menambahkan rule baru ke iptables sehingga memblok IP address dari penyerang, baik untuk periode tertentu maupun secara permanen. (http://www.biznetgiocloud.com/konfigurasi-fail2ban-untuk-mengamankan-server/)

### Persiapan

#### 1. Langkah Instalasi Ubuntu dan Ubuntu Server
#### 2. Penambahan User
#### 3. Konfigurasi Server

### Penetrasi

#### Penetrasi 1

##### Penetrasi dengan Hydra
##### Penetrasi dengan Ncrack

#### Penetrasi 2

##### Konfigurasi Fail2Ban
##### Penetrasi dengan Hydra
##### Penetrasi dengan Ncrack

### Kesimpulan dan Saran





