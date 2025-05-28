Let us start with the most basic scan. Suppose that we want to perform a basic scan against a target residing at 10.129.42.253. To do this we should type 
nmap 10.129.42.253 
and hit return. We see that the Nmap scan was completed very quickly. This is because if we don't specify any additional options, Nmap will only scan the 1,000 most common ports by default.

 The scan output reveals that ports 21, 22, 80, 139, and 445 are available.
 
 ```DamiL@htb[/htb]$ nmap 10.129.42.253

Starting Nmap 7.80 ( https://nmap.org ) at 2021-02-25 16:07 EST
Nmap scan report for 10.129.42.253
Host is up (0.11s latency).
Not shown: 995 closed ports
PORT    STATE SERVICE
21/tcp  open  ftp
22/tcp  open  ssh
80/tcp  open  http
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 2.19 seconds
```



Under the PORT heading, it also tells us that these are TCP ports. By default, Nmap will conduct a TCP scan unless specifically requested to perform a UDP scan.
The STATE heading confirms that these ports are open. Sometimes we will see other ports listed that have a different state, such as filtered. This can happen if a firewall is only allowing access to the ports from specific addresses.
The SERVICE heading tells us the service's name is typically mapped to the specific port number. However, the default scan will not tell us what is listening on that port. Until we instruct Nmap to interact with the service and attempt to tease out identifying information, it could be another service altogether.


As we gain familiarity, we will notice that several ports are commonly associated with Windows or Linux. For example, port 3389 is the default port for Remote Desktop Services and is an excellent indication that the target is a Windows machine.
 In our current scenario, port 22 (SSH) being available indicates that the target is running Linux/Unix,
 but this service can also be configured on Windows. 
 Let us run a more advanced Nmap scan and gather more information about the target device.



We can use the 
-sC parameter to specify that Nmap scripts should be used to try and obtain more detailed information. 

-sV parameter instructs Nmap to perform a version scan. In this scan, 

Nmap will fingerprint services on the target system and identify the service protocol, application name, and version. The version scan is underpinned by a comprehensive database of over 1,000 service signatures. Finally, 

-p- tells Nmap that we want to scan all 65,535 TCP ports.

```DamiL@htb[/htb]$ nmap -sV -sC -p- 10.129.42.253```


This returns a lot more information. We see that it took a lot longer to scan 65,535 ports than 1,000 ports. 
The -sC and -sV  options also increase the duration of a scan, as instead of performing a  simple TCP handshake, they perform a lot more checks. We notice that  this time there is a VERSION heading, which reports the service version  and the operating system if this is possible to identify.
So far, we know that the operating system is Ubuntu Linux.  Application versions can also help reveal the target OS version. 
Take  OpenSSH, for example. 
We see the reported version is OpenSSH 8.2p1 Ubuntu 4ubuntu0.1. 
From inspection of other Ubuntu SSH package changelogs, 
we see the release version takes the format 1:7.3p1-1ubuntu0.1. 
Updating our version to fit this format, we get 1:8.2p1-4ubuntu0.1.
A quick search for this version online reveals that it is included in Ubuntu Linux Focal Fossa 20.04.
![image](https://github.com/user-attachments/assets/157e38fd-9c55-4955-abea-eba89a2ec436)

Another quick search reveals that the release date of this OS is April 23rd, 2020.
![image](https://github.com/user-attachments/assets/8b6c877e-b309-4052-ba89-3519ab118694)

However, it is worth noting that this cross-referencing technique is  not entirely reliable, as it is possible to install more recent  application packages on an older OS version. 

The script scan -sC flag causes Nmap to report the server headers http-server-header page and the page title http-title for any web page hosted on the webserver. 
the output is ===
The web page title PHP 7.4.3 - phpinfo()  indicates that this is a PHPInfo file, which is often manually created  to confirm that PHP has been successfully installed. The title (and  PHPInfo page) also reveals the PHP version, which is worth noting if it  is vulnerable.
                                                                   
                      NOTE
SSH 
devices version
server headers
                                                                                                                                                
        ![image](https://github.com/user-attachments/assets/73f7ae81-c9fd-47fb-97c6-7dc11d4a7b07)


