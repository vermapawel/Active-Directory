Lets run a nmap scan on Domain controller

***nmap -sC -sV -Pn 192.168.1.10 -o nmap.txt***

-sC → It will execute the common scripts in nmap

-sV → It try to detects version banners 

-Pn → By default in windows drops the ICMP packets. It will treats the host as up and and skips host discovery (ping)

-o <filename> → Save the output in a file.

<img width="900" height="621" alt="image" src="https://github.com/user-attachments/assets/7d353cb4-83b0-4ac0-baa4-39b0e34ed05b" />

Lets understand each and every port that are open

**#) Port 53/tcp - DNS** → DNS is responsible to translate Hostname to IP address.

**#) Port 80/tcp - HTTP**

Windows server is accessible via HTTP at Port 80

curl -v http://192.168.1.10

<img width="900" height="347" alt="image" src="https://github.com/user-attachments/assets/f2a90442-a7c8-4672-96a5-fda80032544a" />

<img width="900" height="483" alt="image" src="https://github.com/user-attachments/assets/81e57be1-2028-4d40-bdbe-65d1430e6cb9" />

**#) Port 88/tcp - Kerberos**

Its a protocol provides secure authentication between client and server. 

Client and server communicate with a Key Distribution Center (KDC) on port 88. It has two components

1.The Authentication Service (AS)

2.The Ticket Granting Service (TGS) 

The KDC issue tickets that allows clients to authenticate to service without repeatedly sending passwords. This port is crucial for handling the authentication process of users, machine, and service within a network.

**#) Port 135/tcp - Microsoft Windows RPC**

Remote Procedure Call (RPC) is a protocol that allows application on a Windows machine to communicate with application on other machine, regardless of whether they are on a same network or not.

***rpcclient -U leo 192.168.1.10***

We have put the lep password Hexdump123!

<img width="547" height="242" alt="image" src="https://github.com/user-attachments/assets/90cdf4c7-7efb-4cdf-a8a2-95fcffdff5ce" />

***enudomusers*** >> It will show all the users of the Domains

**#) Port 139/tcp - NetBIOS**

NetBIOS (Network Basic Input/Output System) is a protocol originally developed for communication over LAN. When TCP/IP became the standard networking protocol, NetBIOS was adopted to run over TCP/IP. 

***nbtscan 192.168.1.10***

<img width="846" height="212" alt="image" src="https://github.com/user-attachments/assets/8f0c4ebf-dcc9-4316-aa99-5fc368d32605" />

It a legacy protocol and provides services for name resolution, session management, and simple data transport, but is largely outdated today.

**#) Port 389/tcp - LDAP**

Lightweight Directory Access Protocol is used to query and interact with the directory service that store information about the AD (users, group, computers, printers etc)

**#) Port 445/tcp - SMB**

Server Message Block (SMB) is a network protocol that was developed for File sharing. It enables computers to share files, printers and other resources over a network.

<img width="900" height="442" alt="image" src="https://github.com/user-attachments/assets/5f2a72e0-5d48-401e-b0af-6b23fb39187c" />

In the Domain Controller we have created a .txt file in folder ShareFile in C drive.

Lets share this file

Right click on the Folder (ShareFile) > Properties > Sharing

<img width="900" height="457" alt="image" src="https://github.com/user-attachments/assets/0c84f01f-5110-42b9-b98f-960be95f0404" />

<img width="842" height="591" alt="image" src="https://github.com/user-attachments/assets/03761f6a-b854-4d53-8314-22426438713b" />

<img width="696" height="567" alt="image" src="https://github.com/user-attachments/assets/b6124161-33ce-46d1-94de-4ae94cfe189d" />

Now, we have to enable some features in DC

***Win + R > gpmc.msc***

<img width="900" height="388" alt="image" src="https://github.com/user-attachments/assets/df1916b0-9352-438e-9fed-d618d962acd5" />

Right click Default Domain Controller > Edit

<img width="900" height="484" alt="image" src="https://github.com/user-attachments/assets/78df979a-4c6b-4b23-83d9-41fec877d7fb" />

***Win + R > dsa.msc***

<img width="900" height="540" alt="image" src="https://github.com/user-attachments/assets/261378dd-ac62-403d-a528-cc22c8e2e64e" />

Need to add ANONYMOUS LOGON

***#) Port 464/tcp - kpasswd5***

Port 464/tcp is used by Kerberos protocol for password change. It is used by Active Directory domain controllers and Kerberos Key Distribution Centers (KDCs) to handle password changes and resets securely. In short, whenever a user changes their password in a Kerberos or Active Directory environment, the request flows through this port.

<img width="900" height="490" alt="image" src="https://github.com/user-attachments/assets/6f98740c-3feb-4a67-88b7-bdde65db90c4" />

**#) Port 593/tcp - ncacn_http**

Port 593 is used for Windows RPC over HTTP. It allows Remote Procedure Call (RPC) communication to be encapsuled within HTTP, enabling access through firewall and proxies.

<img width="900" height="464" alt="image" src="https://github.com/user-attachments/assets/b3261e35-b230-4f4d-94e2-37b87e3752d8" />

**#) Port 636/tcp - LDAPS**

Port 636 is used for LDAPS (LDAP over SSL/TSL) which is a secure, encrypted version of LDAP used in Active Directory and other directory services. 

In the nmap output, port 636 is tcpwrapped which means nmap is not able to recognized the services running on this port. But by design LDAPS is running on port 636.

**#) Port 3268/tcp - GC over LDAP**

Port 3268 is used for LDAP queries to the Global Catalog (GC) in Microsoft AD environment. 

Global Catalog (GC) is a partial read-only replica of all objects from all domains in the forest, optimized for search and authentication.

**#) Port 3269/tcp - GC over SSL/TSL**

Port 3269 is used for LDAP queries to the Global Catalog (GC) in Microsoft AD environment. Unlike port 3268, port 3269 encrypts communication using SSL/TSL.

**#) Port 5357/tcp** - Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)

Port 5357 is used by Microsoft HTTPAPI 2 to offer following network services

1. SSDP (Simple Service Discovery Protocol)

SSDP is used for the discovery of devices and services on a local network. For example, it allows devices like printers, cameras, or smart TVs to be discovered by a Windows PC. This is part of the UPnP protocol suite

2. UPnP (Universal Plug and Play)
   
UPnP is a set of networking protocols that allow devices like routers, printers, and other networked devices to automatically discover and configure each other without needing manual configuration.


