# Laporan Tugas 2

**Anggota Kelompok**

| NRP         | Nama                        |
|-------------|-----------------------------|
| 5114100024  | Setyassida Novian Putra D   |
| 5114100097  | Abdul Majid Hasani          |
| 5114100122  | Bayu Sektiaji               |


### Pendahuluan

Pada Tugas 2 PKSJ ini, penulis diminta untuk melakukan uji coba vulnerability plug-in Wordpress.

Berikut beberapa Plug-in yang akan penulis uji:
* Wordpress Video Player
* League Manager
* Wordpress Event Calendar
* Simple Photo Gallery

Berikut beberapa Tools yang kami gunakan dalam tugas ini:
*WPScan
*SQLMap
*Nikto
*The Mole

### Dasar Teori

**1. OS yang Digunakan**
* **Ubuntu** adalah sistem operasi lengkap berbasis Linux, tersedia secara bebas dan mempunyai dukungan baik yang berasal dari komunitas maupun tenaga ahli profesional. (https://balajarlinux.wordpress.com/2008/02/04/pengenalan-apa-itu-ubuntu-serta-sejarah/)

* **Ubuntu Server** adalah ubuntu yang didesain untuk diinstall di server. Perbedaan mendasar, di Ubuntu Server tidak tersedia GUI. Jika ingin menggunakan ubuntu server artinya user harus bekerja dengan perintah-perintah di layar hitam yang sering disebut konsole. (http://www.candra.web.id/mengenal-ubuntu-server/)

**2. Tools yang Digunakan**

* **Wordpress** adalah sebuah aplikasi sumber terbuka (open source) yang sangat populer digunakan sebagai mesin blog (blog engine). WordPress dibangun dengan bahasa pemrograman PHP dan basis data (database) MySQL. PHP dan MySQL, keduanya merupakan perangkat lunak sumber terbuka (open source software)
(https://id.wordpress.org) 

* **Plug-in : Wordpress Video Player** adalah plugin Wordpress untuk menambahkan, mengatur dan menampilkan video. Ternyata plugin ini dapat dieksploitasi menggunakan blind SQL Injection. Pada referensi disebutkan bahwa dengan menggunakan multiple blind SQL Injenction, user yang dapat login ke dashboard Wordpress dapat mengekstrak informasi dari user lainnya, seperti panjang password bahkan seluruh hash password dari user tersebut.
(https://wordpress.org/plugins/player/)

* **Plug-in : League Manager** adalah plugin wordpress untuk management liga sepakbola di halaman wordpress.Ternyata plugin ini dapat dieksploitasi menggunakan blind SQL Injection. Pada referensi disebutkan bahwa dengan menggunakan multiple blind SQL Injenction, user yang dapat login ke dashboard Wordpress dapat mengekstrak informasi dari user lainnya, seperti panjang password bahkan seluruh hash password dari user tersebut.
(https://wordpress.org/plugins/leaguemanager/)

* **Plug-in : Wordpress Event Calendar** adalah plugin Wordpress yang memungkinkan kita untuk membuat kalender kegiatan dengan mudah. Plugin ini dilengkapi dengan banyak fitur seperti mengubah tema kalender, dll. Plugin ini dipublikasikan secara gratis.
(https://wordpress.org/plugins/the-events-calendar/)

* **Plug-in : Simple Photo Gallery** adalah plugin Wordpress yang memungkinkan kita untuk membuat gallery photo dengan mudah dan cepat. Plugin ini dipublikasikan secara gratis.
(https://wordpress.org/plugins/simple-photo-gallery/)

* **WPScan** merupakan tools vulnerability scanner untuk CMS Wordpress yang ditulis dengan menggunakan bahasa pemrograman ruby, WPScan mampu mendeteksi kerentanan umum serta daftar semua plugin dan themes yang digunakan oleh sebuah website yang menggunakan CMS Wordpress.
(http://anher323.blogspot.co.id/2016/01/cek-celah-vulnerability-cms-wordpress.html)

* **SQLMap** adalah tools opensource yang mendeteksi dan melakukan exploit pada bug SQL injection secara otomatis. dengan melakukan serangan SQL injection seorang attacker dapat mengambil alih serta memanipulasi sebuah database di dalam sebuah server.
(https://rixzaldi.wordpress.com/2016/12/28/tutorial-sql-injection-menggunakan-sql-map/)

* **Nikto** adalah web scanner Open Source (GPL), yang melakukan tes komprehensif terhadap web server. Nikto memiliki kemampuan mendeteksi 3500 file yang berpotensi mendatangkan bahaya / CGIS. Nikto dapat menguji web server dengan cepat, tetapi mudah dilihat pada log. Tapi sangat berguna untuk menguji suatu web server. Menurut saya nikto ini pembaca web server yang memiliki celah keamanan CVE maupun OSVDB (Open Source Vulnerability Data Base).
(https://rixzaldi.wordpress.com/2017/01/04/nikto-web-vulnerability-scanner/)

* **The Mole** adalah automatic SQL injection berbasis bahasa python. Fungsi kerjanya sama dengan sqlmap, menjadi tool alternatif dari sqlmap.


### Persiapan

#### 1. Langkah Instalasi Ubuntu dan Ubuntu Server
1. OS yang kami gunakan untuk tugas 1 ini adalah Ubuntu 15.04 dan Ubuntu Server 14.10.
2. Untuk image Ubuntu 15.04 dapat didownload di (https://virtualboxes.org/images/ubuntu/)
3. Untuk image Ubuntu  Server 14.10 dapat didownload di (https://virtualboxes.org/images/ubuntu-server/)
4. Untuk VirtualBox dapat didownload di (https://www.virtualbox.org/wiki/Downloads)
5. Untuk konfigurasi yang dilakukan di dalam VirtualBox adalah mengganti koneksi dari image ke Bridged  Adapter dan mengubah alokasi memori untuk per image sesuai dengan kebutuhan.
6. Lakukan update untuk kedua OS dengan command
```
sudo apt-get update
```
7. Install hydra pada **Ubuntu 15.04** dengan command
```
sudo apt-get install hydra
```
8. Install openssh (jika belum ada) pada **Ubuntu Server 14.10** dengan command
```
sudo apt-get install openssh
```
9. Install ncrack pada **Ubuntu 15.04** dengan command
```
wget http://nmap.org/ncrack/dist/ncrack-0.4ALPHA.tar.gz

sudo apt-get install build-essential checkinstall libssl-dev  libssh-dev
 
tar xvfz ncrack-0.4ALPHA.tar.gz
 
cd ncrack-0.4ALPHA/ ./configure
make
checkinstall
```
#### 2. Penambahan User
1. Tambahkan 2 user pada **Ubuntu Server 14.10** dengan password yang berbeda. Alasan mengapa kami menambahkan 2 user adalah 1 user akan memiliki password yang ada di file untuk dibrute force, untuk user satunya memiliki password yang tidak ada di file.
2. Untuk user pertama tambahkan dengan command, lalu ikuti langkah langkah selanjutnya, untuk user pertama akan ditambah dengan username **ovan** dengan password **ovanovan**. Password dari user pertama ada pada password yang dites pada file brute force
```
sudo adduser ovan
```
![Add User 1](Penambahan_User/adduser_ovan.png)


3. Untuk user kedua tambahkan dengan command, lalu ikuti langkah langkah selanjutnya, untuk user kedua akan ditambah dengan username **sekbay** dengan password **gandalf**. Password dari user kedua tidak ada di file brute force
```
sudo adduser sekbay
```
![Add User 2](Penambahan_User/adduser_sekbay.png)

#### 3. Konfigurasi Server
1. Untuk server mengikuti konfigurasi ip sesuai dengan user
2. Server dan host harus dalam 1 subnet

### Penetrasi
Untuk penetrasi, dibutuhkan 1 file yang berisi password testing.
![Password](Password/password.png)
#### Penetrasi 1
Untuk penetrasi 1, dilakukan 2 skenario pada setiap tools, yaitu
1. Lakukan brute force terhadap user 'ovan' menggunakan list password pada file password.txt
2. Lakukan brute force terhadap user 'sekbay' menggunakan list password pada file password.txt

##### Penetrasi dengan Hydra
1. Gunakan command **Hydra** untuk melakukan brute force dengan command
```
hydra -l ovan -P password.txt 192.168.1.10 ssh
```
Hasil yang akan didapat adalah:
![Penetrasi 1 Ovan](Penetrasi_1/penetrasi_1_ovan.png)


**NOTE**
* Command dimasukkan pada sisi host
* Username yang ditarget harus sama dengan username yang ada di server
* Pastikan command **Hydra** dijalankan di direktori yang terdapat file **password.txt**
* Untuk percobaan ini ip server adalah **192.168.1.10**

2. Gunakan command **Hydra** untuk melakukan brute force dengan command
```
hydra -l sekbay -P password.txt 192.168.1.20 ssh
```
Hasil yang akan didapat adalah:
![Penetrasi 1 Sekbay](Penetrasi_1/penetrasi_1_sekbay.png)


**NOTE**
* Command dimasukkan pada sisi host
* Username yang ditarget harus sama dengan username yang ada di server
* Pastikan command **Hydra** dijalankan di direktori yang terdapat file **password.txt**
* Untuk percobaan ini ip server adalah **192.168.1.20**

##### Penetrasi dengan Ncrack
1. Gunakan command **NCrack** untuk melakukan brute force dengan command
```
ncrack -p 22 --user sekbay -P password.txt 192.168.1.197
```
Hasil yang akan didapat adalah:
![NCrack Sekbay](ncrack/ncrack.png)


**NOTE**
* Command dimasukkan pada sisi host
* Username yang ditarget harus sama dengan username yang ada di server
* Pastikan command **NCrack** dijalankan di direktori yang terdapat file **password.txt**
* Untuk percobaan ini ip server adalah **192.168.1.97**

#### Penetrasi 2
Untuk penetrasi 2, dilakukan 4 skenario pada setiap tools, yaitu
1. Lakukan brute force terhadap user 'ovan' menggunakan list password pada file password.txt dan merubah konfigurasi server ssh
2. Lakukan brute force terhadap user 'ovan' menggunakan list password pada file password.txt dan menggunakan fail2ban
3. Lakukan brute force terhadap user 'sekbay' menggunakan list password pada file password.txt dan merubah konfigurasi server ssh
4. Lakukan brute force terhadap user 'sekbay' menggunakan list password pada file password.txt dan menggunakan fail2ban

##### Konfigurasi SSH Server
1. Lakukan perubahan dengan membuka file **sshd_config** yang ada di dalam folder **/etc/ssh/**
```
nano /etc/ssh/sshd_config
```
2. Ubah line **PasswordAuthentication** dari  **yes** menjadi **no**
![Config Server](Server/password_auth_no.png)

**NOTE**
* Konfigurasi di atas membuat semua user yang terdaftar pada ssh server tidak menggunakan password lagi

##### Konfigurasi Fail2Ban
1. Setelah instalasi dari fail2ban, lakukan konfigurasi pada file **jail.conf** yang ada di **/etc/fail2ban/jail.conf**
2. Ubah 2 line di dalam fail2ban menjadi
```
findtime = 60
maxretry = 3
```
3. Hasil yang akan didapat sebagai berikut
![Config Fail2Ban](Fail2Ban/fail2ban.png)

**NOTE**
* Konfigurasi Fail2Ban setelah selesai melakukan penetrasi dengan konfigurasi server
* Maksud dari findtime = 60 dan maxretry = 3 adalah user yang melebihi batas percobaan login 3 kali (max try 3) dalam 60 detik akan diban selama 600 detik

##### Penetrasi dengan Hydra
1. Gunakan command **Hydra** untuk melakukan brute force dengan command
```
hydra -l ovan -P password.txt 192.168.1.40 ssh
```
Hasil yang akan didapat adalah:
![Penetrasi 2 Ovan Server](Penetrasi_2/penetrasi_2_ovan_server.png)


**NOTE**
* Command dimasukkan pada sisi host
* Username yang ditarget harus sama dengan username yang ada di server
* Pastikan command **Hydra** dijalankan di direktori yang terdapat file **password.txt**
* Untuk percobaan ini ip server adalah **192.168.1.40**

2. Gunakan command **Hydra** untuk melakukan brute force dengan command
```
hydra -l ovan -P password.txt 192.168.1.60 ssh
```
Hasil yang akan didapat adalah:
![Penetrasi 2 Ovan Fail2Ban](Penetrasi_2/penetrasi_2_ovan_fail2ban_%232.png)


**NOTE**
* Command dimasukkan pada sisi host
* Username yang ditarget harus sama dengan username yang ada di server
* Pastikan command **Hydra** dijalankan di direktori yang terdapat file **password.txt**
* Untuk percobaan ini ip server adalah **192.168.1.60**
* Pastikan konfigurasi fail2ban telah diubah

3. Gunakan command **Hydra** untuk melakukan brute force dengan command
```
hydra -l sekbay -P password.txt 192.168.1.40 ssh
```
Hasil yang akan didapat adalah:
![Penetrasi 2 Sekbay Server](Penetrasi_2/penetrasi_2_sekbay_server.png)


**NOTE**
* Command dimasukkan pada sisi host
* Username yang ditarget harus sama dengan username yang ada di server
* Pastikan command **Hydra** dijalankan di direktori yang terdapat file **password.txt**
* Untuk percobaan ini ip server adalah **192.168.1.40**

4. Gunakan command **Hydra** untuk melakukan brute force dengan command
```
hydra -l sekbay -P password.txt 192.168.1.40 ssh
```
Hasil yang akan didapat adalah:
![Penetrasi 2 Sekbay Fail2Ban](Penetrasi_2/penetrasi_2_sekbay_fail2ban.png)


**NOTE**
* Command dimasukkan pada sisi host
* Username yang ditarget harus sama dengan username yang ada di server
* Pastikan command **Hydra** dijalankan di direktori yang terdapat file **password.txt**
* Untuk percobaan ini ip server adalah **192.168.1.40**
* Pastikan konfigurasi fail2ban telah diubah

### Kesimpulan dan Saran
* Terdapat Beberapa cara untuk pengamanan sebuah server dari serangan bruteforce. pertama memilih password server yang susah untuk ditebak, kedua melakukan config pada ssh bruteforce, ketiga menginstall tool yang dapat membantu keamanan salah satu contohnya adalah file2ban.
* Ketika penetrasi dilakukan dengan NCrack dimana service FILE 2 BAN di server side sedang running, host side dapat menemukan password yang dari user yang ingin kita cari, akan tetapi secara otomatis ip address dari host side akan di banned sehingga tidak dapat melakukan komunikasi dengan server side.


