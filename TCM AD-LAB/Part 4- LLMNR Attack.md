**LLMNR Poisoning Attack**

<img width="720" height="360" alt="image" src="https://github.com/user-attachments/assets/995f1b1a-ebc7-4499-aae7-fa20b2aba8e7" />

Lets understand how it works

<img width="680" height="637" alt="image" src="https://github.com/user-attachments/assets/3edf57e9-45f4-4ffe-b4f5-0fa41c5cedd9" />

Lets say the victim is trying to access the share folder hackme By mistake victim typed hackm instead of hackme.

As this share did not exists, the victim will get a negative response from the server.

Now, the victim will send a broadcast message in the network asking how to connect with share hackm.

Now, the hacker can capture the broadcast message (Man in the middle), pretend to know the hackm share and ask for the hash. Victim trust and sends the hash to the attacker.

We will take help of a tool call Responder

***responder -I eth0 -dPv***

<img width="720" height="119" alt="image" src="https://github.com/user-attachments/assets/95f2dcdd-8f5b-45fd-be92-a28a5a0c5c1c" />

<img width="720" height="441" alt="image" src="https://github.com/user-attachments/assets/e27d9b17-d378-4f5c-a929-eae38437b8f8" />

Now we will login Punisher machine

<img width="720" height="417" alt="image" src="https://github.com/user-attachments/assets/dab4f27c-4575-486c-a749-cadcf88d80d5" />

fcastle || Password1

Lets try to access hackm instead of hackme

<img width="720" height="317" alt="image" src="https://github.com/user-attachments/assets/a9997f2a-213a-4940-93eb-5791c3b9ac4f" />

And we have captured the NTLM hash.

<img width="720" height="198" alt="image" src="https://github.com/user-attachments/assets/9587a6fb-ff9a-47fa-adb1-6eb27e2b01aa" />

Similarly lets capture Spiderman machine hash

<img width="720" height="341" alt="image" src="https://github.com/user-attachments/assets/54f82128-4fb9-4bb8-b8c0-fda160ea936b" />

<img width="720" height="269" alt="image" src="https://github.com/user-attachments/assets/ca139b62-f588-4981-ac26-9ecafc6d08c6" />

<img width="720" height="211" alt="image" src="https://github.com/user-attachments/assets/fb7547d0-2bd4-4f8d-adee-a68999bcd066" />

We got SPIDEMAN NTLM hash as well.

Lets save the hashes in txt files.

<img width="500" height="135" alt="image" src="https://github.com/user-attachments/assets/60f5dc64-9dcf-4c9a-b295-c421c89df9c2" />

***hashcat -m 5600 fcHash.txt /usr/share/wordlists/rockyou.txt***

<img width="720" height="421" alt="image" src="https://github.com/user-attachments/assets/80902b37-914b-4e97-9b7b-a7e44b329ca7" />

We have found the password i.e Password1

***hashcat -m 5600 ppHash.txt /usr/share/wordlists/rockyou.txt***

We have found the password i.e Password2





