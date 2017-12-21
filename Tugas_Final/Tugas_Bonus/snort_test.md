# SNORT TESTING


-----

### After Snort was installed and configured, now we will test the Snort by read pcap file from SECREPO (Security Data Samples Repository)


In the field of computer network administration, pcap (packet capture) consists of an application programming interface (API) for capturing network traffic. Unix-like systems implement pcap in the libpcap library; Windows uses a port of libpcap known as WinPcap.

Monitoring software may use libpcap and/or WinPcap to capture packets travelling over a network and, in newer versions, to transmit packets on a network at the link layer, as well as to get a list of network interfaces for possible use with libpcap or WinPcap.

The pcap API is written in C, so other languages such as Java, .NET languages, and scripting languages generally use a wrapper; no such wrappers are provided by libpcap or WinPcap itself. C++ programs may link directly to the C API or use an object-oriented wrapper.

-----


## SNORT TESTING


### Step 1 : 
Downlad the pcap file from SECREPO, you can follow this link

```
http://www.secrepo.com/

or 


https://www.dropbox.com/sh/kk24ewnqi9qjdvt/AACj7AHJrDHQeyJTuo1oBqeQa
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_test/snort_test_1.png)

### Step 2 : 
After file was successfully downladed extract the file by doing this command below

```
unzip shadowbroker.zip
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_test/snort_test_4.png)


### Step 3 :
Scan the pcap file with Snort by doing this command below

```
sudo snort -r pcaps/doublesar-backdoor-connect-win7.pcap -c /etc/snort/snort.conf
```

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_test/snort_test_5.png)

If the scanning was successfully the display will be like this

![N|Solid](https://raw.githubusercontent.com/sani9050/PKSJ/master/Tugas_Final/Tugas_Bonus/img_snort_test/snort_test_6.png)


## Refference

* https://en.wikipedia.org/wiki/Pcap
* http://searchsecurity.techtarget.com/tip/Scapy-tutorial-How-to-use-Scapy-to-test-Snort-rules







