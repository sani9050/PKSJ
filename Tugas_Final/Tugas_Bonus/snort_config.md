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

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_config/snort_config_2.png)

If the copying proccess was finished, the display will be like this

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_config/snort_config_3.png)

### Step 2 : 
Comment all rules that exist in /etc/snort/snort.conf by doing the command below

```
sudo sed -i "s/include \$RULE\_PATH/#include \$RULE\_PATH/" /etc/snort/snort.conf
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_config/snort_config_4.png)

### Step 3 : 
* Edit snort configuration file, first open the file by doing the command below.
> you can use another text editor like gedit, vim, vi, etc by changing command subl with your text editor command.

```
sudo subl /etc/snort/snort.conf
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_config/snort_config_5.png)


Edit the Snort configuration file

```
# Path to your rules files (this can be a relative path)
# Note for Windows users:  You are advised to make this an absolute path,
# such as:  c:\snort\rules
var RULE_PATH rules
var SO_RULE_PATH so_rules
var PREPROC_RULE_PATH preproc_rules

# If you are using reputation preprocessor set these
# Currently there is a bug with relative paths, they are relative to where snort is
# not relative to snort.conf like the above variables
# This is completely inconsistent with how other vars work, BUG 89986
# Set the absolute path appropriately
var WHITE_LIST_PATH rules
var BLACK_LIST_PATH rules

```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_config/snort_config_6.png)


### Step 4 : 
Validate your snort configuration by doing the command below

```
snort -T -i enp0s3 -c /etc/snort/snort.conf
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_config/snort_config_7.png)

If your configuration was successfully configured, the display will be like this

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_config/snort_config_8.png)



## Add the Community Rules to Your Snort


### Step 5 :
First, you must download the community rules at Snort official website, you can follow this link

```
https://www.snort.org/downloads#rules
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_config/snort_config_9.png)


### Step 6 :
After community rules file was successfully downloaded, extract the file by doing the command below

```
tar -xf community-rules.   
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_config/snort_config_11.png)


### Step 7 :
1. After the rules was successfully extracted open the directory file, copy the the rules file "community.rules" to /etc/snort/rules by doing this command below.

```
sudo cp community.rules /etc/snort/rules
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_config/snort_config_10.png)

2. Copy the snort configuratiom file "snort.conf" to /etc/snort by doing this comman below

```
sudo cp snort.conf /etc/snort/
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_config/snort_config_12.png)


## DONE
Your snort was successfully configured and added the rules by Communty Rules.


## Refference

* https://www.snort.org/downloads/community/opensource.gz