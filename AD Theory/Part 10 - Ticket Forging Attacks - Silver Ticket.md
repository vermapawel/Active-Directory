**Silver Ticket Attacks**

This attack is about creating a custom TGS

<img width="672" height="227" alt="image" src="https://github.com/user-attachments/assets/cc5a48d2-9dda-4807-bf07-78ffaf0baca1" />

The Silver Ticket Attack is based on the forging of custom TGS/ST without interaction with the KDC. These tickets can be used to gain access to new services and to maintain persistence on a compromised system.

So, we can forge this ticket and interact directly with the service (We can skip 1,2,3, and 4 messages and directly interact with the service (message 5).

Requirements:

-Domain name
-Domain SID
-SPN of the service to attack
-NTLM hash of the service account to attack
-Privileged Account Certificate (PAC) validation is disabled

<img width="900" height="171" alt="image" src="https://github.com/user-attachments/assets/ba472b43-778a-4e47-bce8-87cb4cdd4e77" />

<img width="900" height="606" alt="image" src="https://github.com/user-attachments/assets/df159674-daf7-48a4-86cd-8f531035df88" />

Lets use a silver ticket to gain unauthorized access to the Common Internet File System Service (CIFS) which basically is SMB

To do this we can use the NTLM hash of the machine account rather than the NTLM hash of a specific service.

**Step 1: Leak NTLM hash of the machine account we want to compromise, Domain Controller DC01$**

Lets assume we have access to Domain controller.

Open mimikartz

<img width="698" height="437" alt="image" src="https://github.com/user-attachments/assets/a67c77d4-e6e3-4a2b-b6c0-95f21c45c11b" />

***sekurlsa::logonpasswords*** >> It will dump all the hash, username etc.

<img width="842" height="425" alt="image" src="https://github.com/user-attachments/assets/2aa0818d-6313-4d4b-81dd-2f4b912828f5" />

We got the NTLM hash 32d323e49ca4a711d597ddee1af1a745

**Step 2: Obtain Domain SID**

***whoami /user***

<img width="627" height="218" alt="image" src="https://github.com/user-attachments/assets/2499c386-ec63-4e64-aade-958619f674c3" />

SID: S-1–5–21–3881124567–2707306243–2324751439

**Step 3: Forging the Silver Ticket**

Now, lets assume we have a low privilege user access in DC

<img width="891" height="601" alt="image" src="https://github.com/user-attachments/assets/d58429fb-a9c7-49d4-85a2-78f4d6400d13" />

So currently this leo user is a Domain user and not a Admin user.

<img width="887" height="652" alt="image" src="https://github.com/user-attachments/assets/c56e46c8-9b2d-4c28-823d-b4675e6fddc8" />

Also there are 3 tickets as of now.

There is a file in DC which is not accessiable

<img width="900" height="333" alt="image" src="https://github.com/user-attachments/assets/e42b3686-a438-4b03-8fb1-39e3dad24f07" />

Now, we have installed mimikatz installed in leo user machine

<img width="720" height="241" alt="image" src="https://github.com/user-attachments/assets/45f3cdc2-f512-492a-b088-2d7db8c26f34" />

Command to generate silver ticket from mimikatze

***kerberos::golden /sid:S-1–5–21–3881124567–2707306243–2324751439 /domain:hexdump.lab /target:dc01.hexdump.lab /service:cifs /rc4:32d323e49ca4a711d597ddee1af1a745 /user:administrator /id:1234 /ptt***

<img width="900" height="346" alt="image" src="https://github.com/user-attachments/assets/306f9ca2-78e1-4e59-a432-53b5cd1389ee" />

A golden ticket has been created for administrator.

<img width="741" height="375" alt="image" src="https://github.com/user-attachments/assets/d3411f74-5637-4b05-b65b-75c17852b0c7" />

Now, there is only one ticket, that is for administrator for CIFS service.

And now we are able to access the file.

<img width="776" height="225" alt="image" src="https://github.com/user-attachments/assets/d3711484-438f-4393-9e98-cab8959ce677" />

So, the user is still leo, but with the help of this ticket the user is acting like an administrator.





