**ACTIVE DIRECTORY**

In a company network, there are many workstations from different departments. If we want to configure common policies on those computers, without Active Directory we have to do it manually on each computers. Its very time consuming, needs lots of efforts and can have errors.

So we need to have a centralized way to manage policies, configuration and access to resources. This is where Active Directory comes in. 

We have configured Windows Server 2022 in vmware.

**Administrator | Password123**

<img width="900" height="636" alt="image" src="https://github.com/user-attachments/assets/6fee63a8-969a-4f1b-b74b-428c77a172db" />

Lets change the Server name to DC01.

<img width="900" height="592" alt="image" src="https://github.com/user-attachments/assets/0aa62f31-157b-4992-9c39-33308a82b2d2" />

We have to restart the Server once.

<img width="900" height="454" alt="image" src="https://github.com/user-attachments/assets/d9d93fe7-f578-442e-8158-c540c3e98f35" />

Name is changed.

Now, we will enable Active Directory Services on the Server

<img width="900" height="459" alt="image" src="https://github.com/user-attachments/assets/68d0902f-3baa-485b-a774-a6218fc6477a" />

<img width="782" height="556" alt="image" src="https://github.com/user-attachments/assets/915071de-8eab-4640-abfb-10c17d014f57" />

<img width="782" height="552" alt="image" src="https://github.com/user-attachments/assets/d2dc1a96-602d-4c84-b1b3-635bc87753b2" />

<img width="792" height="562" alt="image" src="https://github.com/user-attachments/assets/8e1bf5d3-d882-4b95-81bb-cf9b5ca592cc" />

<img width="797" height="562" alt="image" src="https://github.com/user-attachments/assets/9bd484ea-7020-4f70-9445-45116a69e1d9" />

<img width="752" height="512" alt="image" src="https://github.com/user-attachments/assets/63f4f344-37f2-457e-ba17-05099f177f5b" />

<img width="796" height="571" alt="image" src="https://github.com/user-attachments/assets/102c1184-653c-4460-bed9-d89b243d9cce" />

<img width="777" height="557" alt="image" src="https://github.com/user-attachments/assets/0e91e1c9-3274-4823-8db2-38a35db0024a" />

<img width="782" height="560" alt="image" src="https://github.com/user-attachments/assets/525a7f25-ec2b-4cba-a650-d3e059769f4b" />

<img width="797" height="567" alt="image" src="https://github.com/user-attachments/assets/26be3a8d-d9fc-4b12-8967-fc1f1c96d555" />

Installation is completed. Now we have to promote the server to a Domain Controller.

This server will be our Domain Controller.

Go to Server Manager > Click on Flag > Promote this server to a domain controller

<img width="900" height="623" alt="image" src="https://github.com/user-attachments/assets/fcdc9b80-5328-4b54-9189-01f188451c54" />

<img width="797" height="587" alt="image" src="https://github.com/user-attachments/assets/5729a214-a6e1-47db-9221-1b64917b1bc4" />

<img width="762" height="560" alt="image" src="https://github.com/user-attachments/assets/6d9d47b7-6ff0-40bc-bdc3-eb6318f27b6e" />

We set the Recovery Password as Password123

<img width="742" height="555" alt="image" src="https://github.com/user-attachments/assets/a1fcc354-a54a-417d-8fb7-a48f519a0b9d" />

<img width="757" height="557" alt="image" src="https://github.com/user-attachments/assets/4d239175-2e68-4370-8f95-b2ab8c3a66e9" />

<img width="760" height="562" alt="image" src="https://github.com/user-attachments/assets/fe82c934-e5e2-4167-a683-3dfea1731779" />

<img width="761" height="561" alt="image" src="https://github.com/user-attachments/assets/0713a538-4a0b-4024-a870-38e57627a266" />

<img width="771" height="566" alt="image" src="https://github.com/user-attachments/assets/50c20bab-a067-4a33-80e5-948c7fb4da47" />

<img width="762" height="562" alt="image" src="https://github.com/user-attachments/assets/44e75289-5fdc-42b5-9565-210c964e2a03" />

We have to wait till Installing complete. Server will reboot by itself.

<img width="900" height="597" alt="image" src="https://github.com/user-attachments/assets/c8865bca-f75b-4976-a6a8-f612835e67a0" />

The server has become the Domain Controller. Lets login

Now, we need to create a Group Policy. It will be applied to all the machine inside this Domain Controller.

**Windows+R > gpmc.msc**

<img width="900" height="461" alt="image" src="https://github.com/user-attachments/assets/4e7bd439-648c-4333-82ff-0241f11f02de" />

It will open the Group Management Policy Editor

<img width="692" height="587" alt="image" src="https://github.com/user-attachments/assets/9751821a-db89-4018-ab69-78535e13ad3b" />

<img width="602" height="297" alt="image" src="https://github.com/user-attachments/assets/d5899a05-7085-4794-a333-f2a165245e0a" />

We have a policy created. Right click and edit

<img width="900" height="478" alt="image" src="https://github.com/user-attachments/assets/66a27651-c54c-4e37-a2e9-de8b6b3fdcbd" />

Now we will disable automatic updates.

<img width="872" height="521" alt="image" src="https://github.com/user-attachments/assets/2865c2c1-fcf6-43e6-989b-d3bfc521ed1a" />

Windows Component > Windows Updates

<img width="816" height="547" alt="image" src="https://github.com/user-attachments/assets/653d9ea7-6838-402c-a97a-3057ff491105" />

Right Click > Edit

<img width="682" height="635" alt="image" src="https://github.com/user-attachments/assets/f4b6db0e-7729-4b36-b7b3-40742d9a284f" />

We will also disable Real time Protection

<img width="787" height="567" alt="image" src="https://github.com/user-attachments/assets/88d09923-8023-456c-b847-f8c083df23a8" />

Right Click > Edit

<img width="677" height="632" alt="image" src="https://github.com/user-attachments/assets/f74b5f3e-0475-4fe1-8df5-0e6bd4e0041f" />

Now, to make sure GPO changes take effect,

In the CMD we will type command ***gpupdate /force***

<img width="742" height="316" alt="image" src="https://github.com/user-attachments/assets/a67013bb-770b-469e-b023-e74d1c647f6a" />

Now, we will create a user in AD. In the Powershell we will give following commands.

***New-ADUser -Name "leo" -SamAccountName "leo" -UserPrincipalName "leo@hexdump.lab" -AccountPassword (ConvertTo-SecureString -AsPlainText "Hexdump123!" -Force) -Enabled $true***

<img width="900" height="315" alt="image" src="https://github.com/user-attachments/assets/b9a620a7-aa02-4816-9e85-68a2f6ce9f86" />

A new user leo is created. Now we have to enable this account. By default the account is disabled

***Enable-ADAccount -Identity "leo"***

<img width="900" height="147" alt="image" src="https://github.com/user-attachments/assets/b1a127f1-6af9-4df2-a1b1-04d896cb5da9" />

Use is enabled. Now we will make this account as a service account. 

A service account in Active Directory is a special type of account created to run applications, services, or scheduled tasks - not for human logins.

***Set-ADUser -Identity "leo" -ServicePrincipalNames @{Add="HTTP/webserver.hexdump.lab"}***

<img width="900" height="234" alt="image" src="https://github.com/user-attachments/assets/c5170855-46f0-47f4-81e2-ba336b97b86a" />

Now, lets verify

***Get-ADUser -Identity "leo" -Properties ServicePrincipalNames***

<img width="900" height="382" alt="image" src="https://github.com/user-attachments/assets/9364eb71-9624-4f04-a0bd-5cad950d6376" />

This is all set. Now, if we want user leo to login locally in Domain controller, we need to allow it. Generally normal users are blocked by the "Allow log on locally" policy on domain controllers.

**Win + R > gpmc.msc**

Default Domain Controllers Policy > Right click > Edit

<img width="900" height="483" alt="image" src="https://github.com/user-attachments/assets/b688642d-49ec-46c1-85d6-66cf2d2b168b" />

<img width="877" height="297" alt="image" src="https://github.com/user-attachments/assets/c212e790-c034-48f7-af2d-88c9444909da" />

=======================================================================================

Now we need to have a setup a windows 10  machine

<img width="900" height="478" alt="image" src="https://github.com/user-attachments/assets/d9804e0a-06f1-42db-ae87-f8def25ea467" />

We have installed a windows 10. Username is windows password is windows

Now, we need to connect this machine to Active Directory

Lets check if we are able to resolve the Domain controller

***nslookup -type=SRV dc01.hexdump.lab***

<img width="900" height="306" alt="image" src="https://github.com/user-attachments/assets/f379322b-84c7-4d82-bfb4-eb83b7f495e0" />

We are not able to resolve this Domain. 

We have to put the IP address of the Domain Controller (Windows server 2022) in the DNS of this Windows 10.

Lets check the IP address of Domain Controller

<img width="767" height="302" alt="image" src="https://github.com/user-attachments/assets/b82f69b0-9451-4b6f-a0b6-633d2b392bed" />

We will put this IP address in the DNS of Windows 10.

<img width="900" height="609" alt="image" src="https://github.com/user-attachments/assets/a067ea13-21bf-462d-a5b8-b5bc84c1868d" />

Now, lets test again if we can resolve the DNS

<img width="785" height="272" alt="image" src="https://github.com/user-attachments/assets/57102964-5c62-4866-b692-047a662fcdb8" />

This time we can. Now we will join this workstation to the Domain Controller

Go to Control Panel

<img width="900" height="379" alt="image" src="https://github.com/user-attachments/assets/2a6c65df-d0a6-4350-b942-f61a73a821a7" />

Advanced system settings

<img width="900" height="443" alt="image" src="https://github.com/user-attachments/assets/5ceb9bd0-c9b3-4efc-bb00-730d9d2f77fd" />

<img width="900" height="613" alt="image" src="https://github.com/user-attachments/assets/f844de17-be03-49a8-a251-81e75c813e50" />

In the domain we will out hexdump.lab

It will ask for Administrator credentials and then it will be added to the Domain Controller. We have to restart this Windows one

Lets verify on the Windows Server

<img width="816" height="352" alt="image" src="https://github.com/user-attachments/assets/c9fa5e79-5165-4459-8ac4-e388d0915cfb" />

<img width="900" height="452" alt="image" src="https://github.com/user-attachments/assets/23386289-5f6f-46e9-9ca0-4204388d114e" />

And we can see that Windows 10 machine has been added. 

Also we can see that leo user is created as well. This is a user of the domain

<img width="900" height="600" alt="image" src="https://github.com/user-attachments/assets/31e4fb43-2c36-43bb-8fcd-ba5109dc020b" />

Lets verify on CLI

net user /domain >> It will show all the users in DC

<img width="787" height="297" alt="image" src="https://github.com/user-attachments/assets/96a1411c-76ee-4623-9076-e75080ec1678" />

Now, lets login as leo user in Domain controller

**leo || Hexdump123!**

<img width="900" height="421" alt="image" src="https://github.com/user-attachments/assets/3b520df8-1788-424b-bb68-780cf0a55b93" />

<img width="900" height="408" alt="image" src="https://github.com/user-attachments/assets/7425af5c-60e1-4ab7-88d9-095b4cd5d57c" />

However we are not able to login as leo user.

<img width="900" height="462" alt="image" src="https://github.com/user-attachments/assets/e0ffa24f-c8b7-4d61-ab57-9f6a1c589216" />

<img width="830" height="642" alt="image" src="https://github.com/user-attachments/assets/268410a6-9a7b-48d5-9214-1e58b40c1a83" />

We will add Administrators group as well

<img width="557" height="636" alt="image" src="https://github.com/user-attachments/assets/21bae896-9a31-4366-9400-52c0cd8e1bcd" />

Lets update the changes in the DC

<img width="675" height="221" alt="image" src="https://github.com/user-attachments/assets/3339cf72-8360-43f7-ac40-1376aa9ea002" />

