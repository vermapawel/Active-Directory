**Setting up Domain Controller**

DC name : HYDRA-DC (192.168.1.100 || Password123)

<img width="720" height="395" alt="image" src="https://github.com/user-attachments/assets/a17ac86f-21ae-4be7-a6d1-d41266246655" />

<img width="720" height="512" alt="image" src="https://github.com/user-attachments/assets/9e286a07-ca65-41f3-9996-4991ec4f23f7" />

<img width="720" height="507" alt="image" src="https://github.com/user-attachments/assets/37f8b9db-6eed-4866-b847-7c2868ec2c9a" />

<img width="720" height="513" alt="image" src="https://github.com/user-attachments/assets/83d672ad-4156-472b-92eb-1175fdd11e5a" />

<img width="720" height="509" alt="image" src="https://github.com/user-attachments/assets/f874a1c5-32fc-4f28-8644-07c54564538d" />

<img width="720" height="512" alt="image" src="https://github.com/user-attachments/assets/46e431e7-c64f-47e1-b065-02e35b73f6cf" />

<img width="720" height="512" alt="image" src="https://github.com/user-attachments/assets/a57e753f-afbb-4c67-8e34-6606a6af126e" />

<img width="720" height="512" alt="image" src="https://github.com/user-attachments/assets/c9fae388-3308-4afb-8eb7-02959453f1c0" />

<img width="720" height="511" alt="image" src="https://github.com/user-attachments/assets/3858ffd5-db7f-487a-9356-51bb5e29606b" />

<img width="720" height="525" alt="image" src="https://github.com/user-attachments/assets/a8f2a4b3-8d58-4886-a7c6-0b0c75dfe063" />

<img width="720" height="532" alt="image" src="https://github.com/user-attachments/assets/ebabd895-2d86-4bf0-8c7e-ba6003e1eee1" />

<img width="720" height="529" alt="image" src="https://github.com/user-attachments/assets/865c65da-5066-4952-8783-bc4a0e7c9880" />

<img width="720" height="530" alt="image" src="https://github.com/user-attachments/assets/41163c30-b54c-4ae1-85b0-142ab8475395" />

<img width="720" height="530" alt="image" src="https://github.com/user-attachments/assets/e6d5c195-f929-4999-8b76-0aed1c1d8299" />

<img width="720" height="527" alt="image" src="https://github.com/user-attachments/assets/0a937bd7-6ecd-4943-a899-9aae0ce3ed1e" />

<img width="720" height="530" alt="image" src="https://github.com/user-attachments/assets/2936b87b-c5b5-4aec-9122-f0a7014131f2" />

Lets set a Static IP and DNS

***New-NetIPAddress -InterfaceAlias “Ethernet0” -IPAddress 192.168.1.100 -PrefixLength 24 -DefaultGateway 192.168.1.1***

***Set-DnsClientServerAddress -InterfaceAlias “Ethernet0” -ServerAddresses 192.168.1.100***

<img width="720" height="371" alt="image" src="https://github.com/user-attachments/assets/43b5c58a-8c2b-4891-8a68-71b8a72c1ffa" />

Lets verify

<img width="720" height="434" alt="image" src="https://github.com/user-attachments/assets/80aa63b5-f96a-44cb-a714-75efd80c14dc" />

Lets resume the DC installation

<img width="720" height="535" alt="image" src="https://github.com/user-attachments/assets/d4ff5dd8-5052-43ac-b53a-e16e64d8bfd6" />

Again we got an error. We need to change the Administrator password

***net user Administrator Password123***

<img width="720" height="173" alt="image" src="https://github.com/user-attachments/assets/c73d27bc-216c-4aa2-8b5d-7c7adf1ed555" />

Lets resume the DC installation

<img width="720" height="523" alt="image" src="https://github.com/user-attachments/assets/a2216819-e678-4e81-93f4-7f4c6263c70e" />

Now, we don’t have any error. Lets install

<img width="720" height="415" alt="image" src="https://github.com/user-attachments/assets/f2dd3b85-a187-4055-96b7-d80d1e2e3240" />

The server will reboot

===============================================================================================================
===================================================================================================

Now we will setup certificate services.

<img width="720" height="394" alt="image" src="https://github.com/user-attachments/assets/32de836e-000f-43eb-811f-ed8986c0511c" />

<img width="720" height="506" alt="image" src="https://github.com/user-attachments/assets/f3fae5f0-a951-4b37-830f-93913348081c" />

<img width="720" height="513" alt="image" src="https://github.com/user-attachments/assets/4e703412-f430-4920-978c-8f0c189f0a76" />

<img width="720" height="513" alt="image" src="https://github.com/user-attachments/assets/9ed004b7-0a77-4821-b5c2-d1a4541f063a" />

<img width="720" height="513" alt="image" src="https://github.com/user-attachments/assets/c5897898-a5ff-41e9-998a-601cb2a48bd0" />

<img width="720" height="506" alt="image" src="https://github.com/user-attachments/assets/cee04bcf-d837-4830-a62e-d2b744528138" />

<img width="720" height="510" alt="image" src="https://github.com/user-attachments/assets/c4a131b4-7b48-4194-a73a-8e5640fabd50" />

<img width="720" height="512" alt="image" src="https://github.com/user-attachments/assets/a86659af-601b-4640-b686-d502d7362c1a" />

<img width="720" height="513" alt="image" src="https://github.com/user-attachments/assets/05940366-4fe7-4471-96a5-d64d0b296e2a" />

<img width="720" height="510" alt="image" src="https://github.com/user-attachments/assets/390411c7-5f5f-408d-b9de-327e3b764fb2" />

<img width="720" height="528" alt="image" src="https://github.com/user-attachments/assets/3becae12-a3b1-4ffa-ac31-9f6c520f77a6" />

<img width="720" height="531" alt="image" src="https://github.com/user-attachments/assets/beb6797a-d99e-4381-95dd-75cd1ab281f5" />





















