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



























https://www.upcloud.com/support/installing-snort-on-ubuntu/


> The overriding design goal for Markdown's
> formatting syntax is to make it as readable
> as possible. The idea is that a
> Markdown-formatted document should be
> publishable as-is, as plain text, without
> looking like it's been marked up with tags
> or formatting instructions.

This text you see here is *actually* written in Markdown! To get a feel for Markdown's syntax, type some text into the left window and watch the results in the right.

### Tech

Dillinger uses a number of open source projects to work properly:

* [AngularJS] - HTML enhanced for web apps!
* [Ace Editor] - awesome web-based text editor
* [markdown-it] - Markdown parser done right. Fast and easy to extend.
* [Twitter Bootstrap] - great UI boilerplate for modern web apps
* [node.js] - evented I/O for the backend
* [Express] - fast node.js network app framework [@tjholowaychuk]
* [Gulp] - the streaming build system
* [Breakdance](http://breakdance.io) - HTML to Markdown converter
* [jQuery] - duh

And of course Dillinger itself is open source with a [public repository][dill]
 on GitHub.

### Installation

Dillinger requires [Node.js](https://nodejs.org/) v4+ to run.

Install the dependencies and devDependencies and start the server.

```sh
$ cd dillinger
$ npm install -d
$ node app
```

For production environments...

```sh
$ npm install --production
$ NODE_ENV=production node app
```

### Plugins

Dillinger is currently extended with the following plugins. Instructions on how to use them in your own application are linked below.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md] [PlDb] |
| Github | [plugins/github/README.md] [PlGh] |
| Google Drive | [plugins/googledrive/README.md] [PlGd] |
| OneDrive | [plugins/onedrive/README.md] [PlOd] |
| Medium | [plugins/medium/README.md] [PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md] [PlGa] |


### Development

Want to contribute? Great!

Dillinger uses Gulp + Webpack for fast developing.
Make a change in your file and instantanously see your updates!

Open your favorite Terminal and run these commands.

First Tab:
```sh
$ node app
```

Second Tab:
```sh
$ gulp watch
```

(optional) Third:
```sh
$ karma test
```
#### Building for source
For production release:
```sh
$ gulp build --prod
```
Generating pre-built zip archives for distribution:
```sh
$ gulp build dist --prod
```
### Docker
Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 8080, so change this within the Dockerfile if necessary. When ready, simply use the Dockerfile to build the image.

```sh
cd dillinger
docker build -t joemccann/dillinger:${package.json.version}
```
This will create the dillinger image and pull in the necessary dependencies. Be sure to swap out `${package.json.version}` with the actual version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on your host. In this example, we simply map port 8000 of the host to port 8080 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart="always" <youruser>/dillinger:${package.json.version}
```

Verify the deployment by navigating to your server address in your preferred browser.

```sh
127.0.0.1:8000
```

#### Kubernetes + Google Cloud

See [KUBERNETES.md](https://github.com/joemccann/dillinger/blob/master/KUBERNETES.md)


### Todos

 - Write MORE Tests
 - Add Night Mode

License
----

MIT


**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)


   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
