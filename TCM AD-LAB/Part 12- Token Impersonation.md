**Token Impersonation Overview**

Tokens are the temporary key that allow us to access a system/network without having to provide credentials each time we access a file.

There are two types of Tokens

Delegate :- Created when we logging to a machine or using Remote Desktop

Impersonate :- Non Interactive such as attaching a network drive

<img width="720" height="355" alt="image" src="https://github.com/user-attachments/assets/8f07e09c-4875-41f0-9388-e5822c1e4cfb" />

Lets opne Metasploit

<img width="720" height="293" alt="image" src="https://github.com/user-attachments/assets/2f41e8ca-5533-44e0-9987-310489ea21e0" />

We will use this module

Lets set all the options and run the exploit.

<img width="720" height="283" alt="image" src="https://github.com/user-attachments/assets/00cd1c0d-41e1-46c1-8b2a-d6b7aafd879f" />

And we got a shell

<img width="720" height="264" alt="image" src="https://github.com/user-attachments/assets/a8bc4020-0b19-41f2-abce-e130eb46b0ff" />

We are NT Authority

<img width="705" height="325" alt="image" src="https://github.com/user-attachments/assets/81cec287-681b-4c71-9789-389fe539bd6e" />

At the bottom we can see Incognito commands

<img width="720" height="212" alt="image" src="https://github.com/user-attachments/assets/ded57e72-c2ca-447b-8663-eea81567c6ed" />

<img width="687" height="542" alt="image" src="https://github.com/user-attachments/assets/55a4c8cb-ac54-4faa-9cb2-2ba479d1a4d7" />

Lets impersonate the token

<img width="720" height="289" alt="image" src="https://github.com/user-attachments/assets/e326c449-10aa-47ea-8512-94cfa27cc35c" />

Now we are facstle.

If we want to become NT Authority

<img width="720" height="128" alt="image" src="https://github.com/user-attachments/assets/6553be30-921c-4cd7-aa4b-7e7ae98e2647" />

And now we are NT Authority

Now, we will login at Administrator on PUNISHER machine

<img width="720" height="347" alt="image" src="https://github.com/user-attachments/assets/2dda1550-94e5-46f6-98b9-5a68bd052d3d" />

Now, Delegate token should be generated, Lets check

<img width="700" height="335" alt="image" src="https://github.com/user-attachments/assets/a73f4ff8-aaab-469a-a998-df8efad088ee" />

And we have Administrator token available

Lets Impersonate the Administrator user

<img width="720" height="286" alt="image" src="https://github.com/user-attachments/assets/7361b06c-f03d-49ce-a9a6-65a4c414f4d5" />

For proof of concept, lets add a new user

<img width="720" height="131" alt="image" src="https://github.com/user-attachments/assets/fe81eb38-7e02-4563-9a21-8694cb01d830" />

We have added a new domain user

hawkeye || Password1@

<img width="720" height="141" alt="image" src="https://github.com/user-attachments/assets/4dab7869-f0ef-4e45-816e-8d8e9f5a9c7c" />

We have added hawkeye in domain admin group

Lets validate

***secretsdump.py MARVEL.local/hawkeye:’Password1@’@192.168.1.100***

<img width="720" height="485" alt="image" src="https://github.com/user-attachments/assets/48e72baa-c941-4a7a-98b0-d8502b5104b5" />

We are able to dump hashes of all the users
