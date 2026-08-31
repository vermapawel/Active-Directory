**DCSync Attack**

In Active Directory, there are multiple Domain Controllers. The data of these DC are synchronized with each other and to confirm this synchronization, AD replication data is used. 

AD replication feature determines how DC synchronize data between themselves. 

The DCSync attack tricks the DC into thinking the attacker is another legitimate DC that needs replication data.

This is a post-exploitation attack and its not an entry point of the domain. Onc  we have an access to the domain, then we can perform this attack.

<img width="872" height="498" alt="image" src="https://github.com/user-attachments/assets/e80b134d-0785-4b3b-9584-17a8a9477920" />

How to configure a user with DCSync privileges

As a pre-requisite, the attack needs to have compromised a Domain Admin or a general account with following permissions

1.Replicating Directory Changes

2.Replicating Directory Changes All

Lets assign these permissions to user leo

<img width="640" height="237" alt="image" src="https://github.com/user-attachments/assets/f5266ceb-ae9d-4598-8f9b-69b566adbe2f" />

<img width="535" height="473" alt="image" src="https://github.com/user-attachments/assets/54456526-b4a9-4a95-a16e-7670b77568fb" />

So, leo is a domain user.

Lets give Replicating Directory permissions to

<img width="772" height="768" alt="image" src="https://github.com/user-attachments/assets/e20c2063-935f-4708-a5eb-a91dd04af33b" />

<img width="900" height="470" alt="image" src="https://github.com/user-attachments/assets/eddd3f05-dcb0-4ed8-a50f-346c7e857ef1" />

<img width="900" height="353" alt="image" src="https://github.com/user-attachments/assets/5c8c55fe-dd1b-4a70-807a-bff4472d2e67" />

<img width="900" height="353" alt="image" src="https://github.com/user-attachments/assets/fbed1bc0-e2ef-4506-80b6-e5bb58e30c3d" />

Right click on hexdump.lab > Properties > Security

<img width="597" height="612" alt="image" src="https://github.com/user-attachments/assets/7ccfdebf-c367-45b3-9edd-d0a95ff49079" />

<img width="590" height="316" alt="image" src="https://github.com/user-attachments/assets/fb9f87d7-11b5-45a8-b4c7-9d7697820bba" />

<img width="510" height="571" alt="image" src="https://github.com/user-attachments/assets/e26e4a29-93ea-4f6f-ab78-d235bcb48cae" />

We will enable following options for leo user

Now, lets login as leo user and start mimikatz

<img width="730" height="237" alt="image" src="https://github.com/user-attachments/assets/74face89-6e19-450e-8109-3a8e946f6b6a" />

***lsadump::dcsync /domain:hexdump.lab /user:krbtgt***

<img width="843" height="577" alt="image" src="https://github.com/user-attachments/assets/d43fc04e-fcce-4483-80f0-e3193aa2d891" />

We got the NTLM hash of the krbtgt account d32a101d774f6e22de48af810bab8ccf

Now, we get NTLM hash of krbtgt account because user leo has specific permissions in order to replicate Active Directory data. In this replication, the DC exchange the hashes of the users including the krbtgt user.

Now, lets remove these permissions and try the exploit again

<img width="900" height="637" alt="image" src="https://github.com/user-attachments/assets/30e0e730-c450-45b9-ab1a-f5402f5d6423" />

<img width="687" height="183" alt="image" src="https://github.com/user-attachments/assets/e277325a-2415-450f-90d6-8ad724495b49" />

This exploit does not worked because the user don't have those privileges
