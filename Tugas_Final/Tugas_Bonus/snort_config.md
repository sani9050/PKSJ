# SNORT
-----

[![N|Solid](https://www.upcloud.com/support/wp-content/uploads/2015/12/snort_logo-300x164.png)](https://www.snort.org/)



**Snort adalah sebuah software yang berguna untuk mengamati aktivitas dalam suatu jaringan komputer. Snort dapat digunakan sebagai suatu Network Intrusion Detection System (NIDS) yang berskala ringan (lightweight).**

-----

## Cara Kerja SNORT

![N|Solid](https://almaspens.files.wordpress.com/2016/04/capture.png)


## Komponen – komponen Snort IDS (Intrusion Detection System) meliputi :

* **Rule Snort** : database yang berisi pola – pola serangan berupa signature jenis -jenis serangan. Rule snort harus selalu terupdate secara rutin agar ketika ada suatu teknik serangan yang baru, serangan tersebut dapat terdeteksi.

* **Snort Engine** : program yang berjalan sebagai daemon proses yang selalu bekerja untuk membaca paket data dan kemudian membadingkan dengan Rule Snort.

* **Alert** : catatan serangan pada deteksi penyusupan. Jika Snort engine mendeteksi paket data yang lewat sebagai sebuah serangan, maka snort engine akam mengirimkan alert berupa log file. Kemudian alert tersebut akan tersimpan di dalam database.


## Persiapan Sebelum Install Snort :

> Pertama-tama Anda perlu menginstal prerequired software sebelum menginstal Snort.
Jalankan perintah berikut.

```
sudo apt install -y gcc libpcre3-dev zlib1g-dev libpcap-dev openssl libssl-dev libnghttp2-dev libdumbnet-dev bison flex libdnet
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_1.png)

> Jika sudah terinstall akan seperti gambar dibawah ini. 


![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_2.png)

> Setelah prerequired software berhasil di install, anda dapat melanjutkan untuk mendownload dan menginstall Snort secara manual dari sumber yang ada.

## Installasi Snort :

> **Installasi Snort di Ubuntu terdiri dari beberapa langkah**:
   * mendownload kode
   * mengonfigurasinya
   * mengkompilasi kode
   * menginstalnya ke direktori yang sesuai
   * mengkonfigurasi aturan deteksi


### Step 1 : 
Mulailah dengan membuat folder download sementara ke direktori home atau direktori sesuka Anda dan masuklah kedalam folder tersebut dengan perintah di bawah ini.

```
mkdir ~/snort_src && cd ~/snort_src
```

### Step 2 : 
Snort itself uses something called Data Acquisition library (DAQ) to make abstract calls to packet capture libraries. Download the latest DAQ source package from the Snort website with the wget command underneath. 

```
wget https://www.snort.org/downloads/snort/daq-2.0.6.tar.gz
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_3.png)

If the download process was finished, the display will be like this.

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_4.png)

### Step 3 : 
Then extract the source code and jump into the new directory with the following commands.

```
tar -xvzf daq-2.0.6.tar.gz
cd daq-2.0.6
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_5.png)

If the process was finished, the display will be like this.

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_6.png)

### Step 4 : 
Run the configuration script using its default values, then compile the program with make and finally install DAQ.

```
./configure && make && sudo make install

```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_7.png)

If the process was finished, the display will be like this.

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_8.png)

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_9.png)

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_10.png)

With the DAQ installed you can get started with Snort, change back to the download folder.

```
cd ~/snort_src
```

### Step 5 : 
Next, download the Snort source code with wget. 

```
wget https://www.snort.org/downloads/snort/snort-2.9.9.0.tar.gz
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_11.png)

if the download process wes finished, the display will be like this.

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_12.png)

### Step 6 : 
And then, extract the source and change into the new directory with these commands.

```
tar -xvzf snort-2.9.9.0.tar.gz
cd snort-2.9.9.0
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_13.png)

If the process was finished, the display will be like this.

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_13.png)

### Step 7 : 
Then configure the installation with sourcefire enabled, run make and make install.

```
./configure --enable-sourcefire && make && sudo make install
```

> With that done, continue below on how to setup the configuration files.

### Step 8 : 
Next, you will need to configure Snort for your system. This includes editing some configuration files, downloading the rules that Snort will follow, and taking Snort for a test run.

Start with updating the shared libraries using the command underneath.

```
sudo ldconfig
```

### Step 9 : 
Snort on Ubuntu gets installed to /usr/local/bin/snort directory, it is good practice to create a symbolic link to /usr/sbin/snort.

```
sudo ln -s /usr/local/bin/snort /usr/sbin/snort
```


### Step 10 : 
Setting up username and folder structure
To run Snort on Ubuntu safely without root access, you should create a new unprivileged user and a new user group for the daemon to run under.

```
sudo groupadd snort
sudo useradd snort -r -s /sbin/nologin -c SNORT_IDS -g snort
```
![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_16.png)

### Step 11 : 
Then create the folder structure to house the Snort configuration, just copy over the commands below.

```
sudo mkdir -p /etc/snort/rules
sudo mkdir /var/log/snort
sudo mkdir /usr/local/lib/snort_dynamicrules
```
![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_17.png)

### Step 12 : 
Set the permissions for the new directories accordingly.

```
sudo chmod -R 5775 /etc/snort
sudo chmod -R 5775 /var/log/snort
sudo chmod -R 5775 /usr/local/lib/snort_dynamicrules
sudo chown -R snort:snort /etc/snort
sudo chown -R snort:snort /var/log/snort
sudo chown -R snort:snort /usr/local/lib/snort_dynamicrules
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_18.png)


### Step 13 : 
Create new files for the white and black lists as well as the local rules.

```
sudo touch /etc/snort/rules/white_list.rules
sudo touch /etc/snort/rules/black_list.rules
sudo touch /etc/snort/rules/local.rules
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_19.png)


### Step 14 : 
Then copy over the configuration files from the download folder.

```
sudo cp ~/snort_src/snort-2.9.9.0/etc/*.conf* /etc/snort
sudo cp ~/snort_src/snort-2.9.9.0/etc/*.map /etc/snort
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_20.png)


### Step 15 : 
Check whether the installation is successful or not by doing the command below.

```
snort -V
```

If successful it will appear as in the picture


![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_21.png)

-----

## Refference

* https://almaspens.wordpress.com/2016/04/03/snort/
* https://www.upcloud.com/support/installing-snort-on-ubuntu/