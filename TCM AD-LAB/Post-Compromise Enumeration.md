***ldapdomaindump ldap://192.168.1.100 -u ‘MARVEL\fcastle’ -p ‘Password1’***

<img width="720" height="199" alt="image" src="https://github.com/user-attachments/assets/19fd0a7d-695f-4d2f-8f1b-f0a800375ced" />

***firefox domain_users_by_group.html***

<img width="720" height="280" alt="image" src="https://github.com/user-attachments/assets/68cc23af-1512-4651-880d-a479d706f1e3" />

We get all the information regarding the Domain and all other informations that can be useful.

**Domain Enumeration with Bloodhound**

***bloodhound-python -d MARVEL.local -u fcastle -p Password1 -ns 192.168.1.100 -c all***

<img width="720" height="238" alt="image" src="https://github.com/user-attachments/assets/d0f3ffc0-c972-4a8f-88b4-a80d4335077a" />

<img width="720" height="356" alt="image" src="https://github.com/user-attachments/assets/ccfc60d9-0c84-4f6b-b4fe-c65669407454" />

We have collected all these data. Now we will upload all these data to BloodHound GUI

<img width="720" height="330" alt="image" src="https://github.com/user-attachments/assets/040aca92-1d3c-4e35-a707-906b23617a27" />

<img width="720" height="560" alt="image" src="https://github.com/user-attachments/assets/e617fa71-ffb2-44b7-9e71-b248258f756e" />

Now we can run multiple commands to get information about the domain.

<img width="720" height="407" alt="image" src="https://github.com/user-attachments/assets/4b791490-e845-4c2a-8369-2286ff8b94a5" />
