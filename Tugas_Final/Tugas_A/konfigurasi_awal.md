## Konfigurasi Awal

### Langkah-langkah

**A. Disable SELinux**
1. Disable SELinux dengan cara

```
gedit /etc/selinux/config 2>/dev/null &
SELINUX=disabled
```

```
setenforce 0
sestatus
```

2. Disable firewall

```
service iptables stop
chkconfig iptables off
```

**B. Install Apache httpd server**
1. Download httpd

```
yum install httpd.i686
```

**C. Install dan start mysql dan mysql-server**
1. Install mysql

```
yum install mysql.i686
```

2. Install mysql-server

```
yum install mysql-server
```

3. Start mysqld

```
service mysqld start
chkconfig --level 2345 mysqld on
mysqladmin -u root password sanisani
```

4. Buat database dvwa

```
mysqladmin -u root -p
sanisani
create database dvwa;
quit
```

**D. Install PHP**

1. Install PHP
```
yum install php.i686
yum install php-mysql
yum install php-pear php-pear-DB
```

**E. Install wget**

```
yum install wget
```

**F. Install Damn Vulnerable Web App (DVWA)**

1. Download DVWA
```
cd /var/www/html
wget http://www.computersecuritystudent.com/SECURITY_TOOLS/DVWA/DVWAv107/lesson1/DVWA-1.0.7.zip
ls -l | grep DVWA
```

2. Extract DVWA
```
unzip DVWA-1.0.7.zip
```

3. Config config.inc.php

```
cd /var/www/html/dvwa/config
cp config.inc.php config.inc.php.BKP
chmod 000 config.inc.php.BKP
nano config.inc.php
```

ubah password database sesuai dengan passwordnya

4. Restart Apache

```
service httpd restart
ps -eaf | grep -v grep | grep httpd
```
