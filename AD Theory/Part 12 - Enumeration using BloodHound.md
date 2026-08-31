Bloodhound is a tool that is used for harvesting and analyzing the data in order to find miss configurations, attack vectors etc.

***bloodhound-python -u leo -p 'Hexdump123!' -ns 192.168.1.12 -d hexdump.lab -c All - zip***

<img width="851" height="372" alt="image" src="https://github.com/user-attachments/assets/fef4bf3d-4f1d-4639-a3c1-239e17c472e4" />

***bloodhound-python -u administrator -p 'Password123' -ns 192.168.1.12 -d hexdump.lab -c All - zip***

<img width="858" height="365" alt="image" src="https://github.com/user-attachments/assets/46a7552a-78fc-4f20-a8cc-5da9a207568b" />

<img width="842" height="192" alt="image" src="https://github.com/user-attachments/assets/5dc511bf-c318-4b47-a0a5-9165096fdab7" />

We have two zip files.

Now, lets download the BloodHound GUI

wget https://github.com/SpecterOps/bloodhound-cli/releases/latest/download/bloodhound-cli-linux-amd64.tar.gz

<img width="798" height="125" alt="image" src="https://github.com/user-attachments/assets/efedf24e-7e1b-41a4-a08a-c5b31794e909" />

admin || AYxlJddo90eGQyMp7ZzpE3EeyJvQFgSd

***./bloodhound-cli containers start***

<img width="800" height="170" alt="image" src="https://github.com/user-attachments/assets/cb57d8c3-c7b2-4639-b6f9-31165874599a" />

BloodHound UI at: http://127.0.0.1:8080/ui/login

<img width="900" height="544" alt="image" src="https://github.com/user-attachments/assets/3f067e24-3f26-4dd0-88ce-cf7bf5222c7d" />

<img width="900" height="612" alt="image" src="https://github.com/user-attachments/assets/568b93fc-ddc3-4b24-8dde-43328df39a75" />

We have to upload the ZIP file

<img width="900" height="412" alt="image" src="https://github.com/user-attachments/assets/1c8fb0d2-37c8-40ca-be88-c6e006f9d389" />

<img width="780" height="687" alt="image" src="https://github.com/user-attachments/assets/e6cc806e-93a1-429c-9713-00e96a7e948c" />

<img width="900" height="499" alt="image" src="https://github.com/user-attachments/assets/ecc7289c-c25a-4d6e-a620-4d301b43b1a3" />

There are three groups having respective permissions over the Domain.

So if we have these permissions, Generic All, AllExtendedRights we can perform DCSync attack.

<img width="900" height="229" alt="image" src="https://github.com/user-attachments/assets/22d5646e-5fd4-424c-b5e5-bdc9257a4041" />

Following is the query running:-

```
MATCH p=(:Base)-[:DCSync|AllExtendedRights|GenericAll]->(:Domain)
RETURN p
LIMIT 1000
```

<img width="896" height="616" alt="image" src="https://github.com/user-attachments/assets/9baa39c7-a8b7-4be0-9bcb-b5e8f3e6731d" />

Now, there is no leo user here because leo user dont have these permissions. 

leo user has GetChangesAll permission. Lets add this permission in the query

<img width="900" height="538" alt="image" src="https://github.com/user-attachments/assets/ade14d97-b540-431d-a094-cdd4255bf38f" />

So, leo user can also perform DCSync attack.

There are much more queries we can use. We can find All Kerberoastable users

<img width="900" height="428" alt="image" src="https://github.com/user-attachments/assets/e592f7e3-1c49-4e9e-9b4c-1de87fc9c214" />
