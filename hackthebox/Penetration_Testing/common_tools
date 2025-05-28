🔐 Secure Shell (SSH)

## Overview
Secure Shell (SSH) is a cryptographic network protocol designed for secure remote access, file transfers, and tunneling. By default, SSH operates on **port 22**, providing system administrators and security professionals a reliable way to connect to remote systems.

## Authentication Methods
SSH supports two primary authentication mechanisms:
- **Password Authentication** – Requires user credentials for access.
- **Public-Key Authentication** – Uses an SSH key pair (private & public) for passwordless login, improving security.

## Practical Applications
SSH is commonly used for:
- **Remote System Administration** – Secure management of servers.
- **Secure File Transfers** – Uploading and downloading files (SCP/SFTP).
- **Port Forwarding & Proxying** – Facilitating connections to restricted resources.
- **Accessing Remote Machines** – Enabling secure connections across networks.

## SSH Client-Server Model
SSH operates on a client-server model:
- The **client** (e.g., OpenSSH) initiates the connection.
- The **server** receives and processes authentication requests, allowing secure access.

## SSH in Penetration Testing
Penetration testers use SSH for secure remote access when credentials or private keys are obtained during security assessments. SSH provides a **stable, reliable** alternative to reverse shells, allowing enumeration, exploitation, and persistence.

### Example SSH Connection
```bash
ssh username@remote-server-ip



# 🔐 NETCAT
# 🔗 Netcat (nc) – The Swiss Army Knife of Networking  

## **Overview**  
Netcat (nc) is a versatile network utility used for interacting with **TCP/UDP** ports. It is widely utilized in penetration testing for tasks such as **banner grabbing, port scanning, reverse shells, and file transfers**. As a lightweight and powerful tool, Netcat provides direct communication with network services and can establish raw connections between hosts.

## **Primary Uses of Netcat in Penetration Testing**
Netcat is invaluable for security assessments and network debugging, including:
- **Port Scanning & Service Enumeration** – Identifying open ports and running services.
- **Banner Grabbing** – Gathering information about services on a target system.
- **Shell Access** – Connecting to reverse shells or interacting with system processes.
- **File Transfers** – Sending and receiving files across networks.
- **Port Forwarding & Proxying** – Facilitating connections to internal resources.

## **Banner Grabbing Example**
Using Netcat, we can interact with a listening service on **port 22** (SSH) to extract its banner:

**nc 10.10.10.10 22**

This reveals that an OpenSSH server is running on the target system, a valuable reconnaissance method for penetration testers.

SSH-2.0-OpenSSH_8.4p1 Debian-3

Using Nmap to Discover Open Ports
──(damil㉿H4CKTIVIST)-[~]
└─$ nmap 162.144.53.131                                                                 
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-02-05 19:04 WAT
Nmap scan report for server.uniosun.edu.ng (162.144.53.131)
Host is up (0.51s latency).
Not shown: 986 closed tcp ports (reset)
PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
25/tcp   filtered smtp
26/tcp   open     rsftp
53/tcp   open     domain
80/tcp   open     http
110/tcp  open     pop3
143/tcp  open     imap
443/tcp  open     https
465/tcp  open     smtps
587/tcp  open     submission
993/tcp  open     imaps
995/tcp  open     pop3s
3306/tcp open     mysql
Nmap done: 1 IP address (1 host up) scanned in 49.58 seconds

┌──(damil㉿H4CKTIVIST)-[~]
└─$ netcat 162.144.53.131 21
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 19:13. Server port: 21.
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.


nc -help – This command will print a list of all of the available commands you can use in Netcat. It will come in handy if you run into any errors while writing a script or are unsure of how to proceed.

nc -z -v site.com – This will run a basic port scan of the specified website or server. Netcat will return verbose results with lists of ports and statuses. Keep in mind that you can use an IP address in place of the site domain.

nc -l – This command will instruct the local system to begin listening for TCP connections and UDP activity on a specific port number.

nc site.com 1234 (less than) file_name – This command will initiate the transfer of a file based on the specified port number.

