# SNORT CONFIGURATION
-----

### After we do step 11, 12, and 13 in SNORT INSTALLATION, we can configure the SNORT with following steps.


-----
**
IF YOU HAVE DONE THE STEPS BELOW, THEN JUST GO TO THE CONFIGURATION STEPS
**


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

### Step 14 : 
Then copy over the configuration files from the download folder.

```
sudo cp ~/snort_src/snort-2.9.9.0/etc/*.conf* /etc/snort
sudo cp ~/snort_src/snort-2.9.9.0/etc/*.map /etc/snort
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_install/snort_install_20.png)

-----

## SNORT CONFIGURATION


### Step 1 : 

Open your SNORT temporary directory and open terminal in there.
Copy dynamicpreprocessor file

```
sudo cp -avr src/dynamic-preprocessors/build/usr/local/lib/snort_dynamicpreprocessor/* /usr/local/lib/snort_dynamicpreprocessor/
```

### Step 2 : 
Comment semua rules

```
sudo sed -i "s/include \$RULE\_PATH/#include \$RULE\_PATH/" /etc/snort/snort.conf
```


### Step 3 : 
Edit file konfigurasi snort

sudo subl /etc/snort/snort.conf


### Step 4 : 
Validasi setting
snort -T -i enp0s3 -c /etc/snort/snort.conf


Menambahkan rules
Download rule

https://www.snort.org/downloads#rules


extract
tar -xf community-rules.tar
Buka file tersebut lalu copy file rules ke /etc/snort


Copy file konfigurasi snort














## Refference

* https://almaspens.wordpress.com/2016/04/03/snort/
* https://www.upcloud.com/support/installing-snort-on-ubuntu/