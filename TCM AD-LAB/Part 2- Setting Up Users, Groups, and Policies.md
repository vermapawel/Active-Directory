**Setting Up Users, Groups, and Policies**

<img width="720" height="322" alt="image" src="https://github.com/user-attachments/assets/da374a88-5c0f-4d75-940b-dccfb247cbee" />

<img width="720" height="511" alt="image" src="https://github.com/user-attachments/assets/9396ad81-ecf4-4f54-a55b-9236a3b62d0a" />

Currently there is only one user Administrator and multiple Groups like Domian Admin, Domain Users etc.

Lets separate them

<img width="720" height="488" alt="image" src="https://github.com/user-attachments/assets/47cc2d25-0728-4559-9953-a5b02a9e1983" />

<img width="720" height="421" alt="image" src="https://github.com/user-attachments/assets/868300ee-a67a-4b97-8f7d-0fb7b681d72a" />

Copy and drag all the Groups in the Groups folder.

<img width="720" height="396" alt="image" src="https://github.com/user-attachments/assets/4eb48e60-d92e-4239-82e0-50e54e397f5d" />

So, now we have only Administrator and Guest account in Users Group.

Lets create one more Administrator (Domain Admin)

<img width="720" height="451" alt="image" src="https://github.com/user-attachments/assets/d41e4c06-a8e0-44bf-ac9c-dd56e29194a2" />

We can copy and paste any user. By doing this, the new user will have same properties and permissions.

<img width="590" height="501" alt="image" src="https://github.com/user-attachments/assets/c0718f16-827a-46a1-ab1e-020e36362dc2" />

Lets set the password: Password123

<img width="692" height="487" alt="image" src="https://github.com/user-attachments/assets/c1cb56da-52bc-492b-91f6-181ffb2a2f97" />

<img width="577" height="501" alt="image" src="https://github.com/user-attachments/assets/69cdbad0-ce7a-4f2b-a6e5-0f5435114ae8" />

<img width="720" height="308" alt="image" src="https://github.com/user-attachments/assets/75fa1c12-be69-46f3-a8c6-24e697fecf20" />

One Domain Admin is created.

Now, we will create a Service Account that is also a Domain Admin. They are use to run a service.

<img width="720" height="330" alt="image" src="https://github.com/user-attachments/assets/0c332cc0-cbde-45fd-92e8-8e1f208ecebd" />

<img width="547" height="476" alt="image" src="https://github.com/user-attachments/assets/63b97d0c-8277-4b9a-81fb-93d0efee4828" />

We are creating a SQL service that will help to run SQL server.

<img width="570" height="492" alt="image" src="https://github.com/user-attachments/assets/cae1997c-7d28-406b-ae9d-bb63c822e69d" />

Password is :- MYpassword123#

<img width="567" height="497" alt="image" src="https://github.com/user-attachments/assets/14e05889-e5af-42f7-9531-b92b8add8e0d" />

Now, for this account, we will add a note in description

<img width="720" height="558" alt="image" src="https://github.com/user-attachments/assets/7c4a3d01-daf4-48ec-9bec-bee904f00a4d" />

Now, we will create two low level users

<img width="720" height="476" alt="image" src="https://github.com/user-attachments/assets/69af3084-c74f-4cb6-ace8-13feb5a0ee02" />

<img width="552" height="471" alt="image" src="https://github.com/user-attachments/assets/fb437207-2e6e-4b91-a3a7-0379f60cc649" />

<img width="542" height="471" alt="image" src="https://github.com/user-attachments/assets/b9a3a2a1-2e30-45fb-ae7b-4d46d7ad6384" />

Password : Password1

<img width="551" height="472" alt="image" src="https://github.com/user-attachments/assets/50384a8b-a5e8-423c-b263-bfb6e11bfd24" />

Lets create one more user

<img width="552" height="472" alt="image" src="https://github.com/user-attachments/assets/7dfc8c00-2a64-4628-a82b-6868f95e3d0d" />

<img width="542" height="467" alt="image" src="https://github.com/user-attachments/assets/2ab14a50-d467-4743-a0ca-a106f82f082b" />

Password: Password2

<img width="545" height="472" alt="image" src="https://github.com/user-attachments/assets/80f9e552-af22-4ed7-b0f6-6144ed4a3967" />

<img width="720" height="353" alt="image" src="https://github.com/user-attachments/assets/fee36503-7f82-4b36-9a9b-2e36de7ca341" />

Users have been created.

Lets create a File share

<img width="720" height="349" alt="image" src="https://github.com/user-attachments/assets/afd2d8c9-8aad-4b47-a667-335284d6295c" />

<img width="720" height="282" alt="image" src="https://github.com/user-attachments/assets/d56aaa94-23d1-4183-b87b-bfca0615e286" />

<img width="720" height="354" alt="image" src="https://github.com/user-attachments/assets/a14fd639-621f-4787-b381-a72b8506a35a" />

<img width="720" height="524" alt="image" src="https://github.com/user-attachments/assets/a2db4314-51dc-4354-b830-b656fd4efc72" />

<img width="720" height="530" alt="image" src="https://github.com/user-attachments/assets/c8e109f1-c12e-4c2c-9f5e-e85a6271f8de" />

<img width="720" height="530" alt="image" src="https://github.com/user-attachments/assets/933ec981-54df-4e05-a03a-4e1a7dec360d" />

<img width="720" height="524" alt="image" src="https://github.com/user-attachments/assets/8a6fa018-00eb-4ec5-9dd3-cd073dae9b07" />

<img width="720" height="526" alt="image" src="https://github.com/user-attachments/assets/40535150-8b97-456b-ab49-b0e76efe6222" />

<img width="720" height="530" alt="image" src="https://github.com/user-attachments/assets/02deb1b2-1158-4495-8036-2d10114a1911" />

Share has been created

Now we need to setup the service Account.

***setspn -a HYDRA-DC/SQLService.MARVEL.local:60111 MARVEL\SQLService***

<img width="720" height="204" alt="image" src="https://github.com/user-attachments/assets/2ea61c77-45fd-41e9-82df-4cb5a82c3e71" />

Lets verity

setspn -T MARVEL.local -Q */*

<img width="720" height="453" alt="image" src="https://github.com/user-attachments/assets/9c21278b-921f-4609-8e72-f8d7acb05e38" />

Now, we will set up a Group Policy. This policy will be setup for entire domain

<img width="720" height="580" alt="image" src="https://github.com/user-attachments/assets/73aa5075-67a1-4bf9-a111-042d583a56b6" />

<img width="720" height="500" alt="image" src="https://github.com/user-attachments/assets/2c1e182a-6f31-4e54-b080-5500a3956219" />

<img width="720" height="396" alt="image" src="https://github.com/user-attachments/assets/db861254-fb9c-4dd3-8610-8a52864bc2bc" />

Group Policy is created. Now we need to edit it

<img width="720" height="430" alt="image" src="https://github.com/user-attachments/assets/dccdcc7e-9dcf-477f-9de2-00ca81bbcb6d" />

<img width="720" height="511" alt="image" src="https://github.com/user-attachments/assets/ed905ee1-3d52-46cb-90ef-b8deb9ad48cc" />

Here we will search Windows Anti Virus

<img width="720" height="404" alt="image" src="https://github.com/user-attachments/assets/62ccf2ac-886d-462e-b83f-15a59c208330" />

<img width="720" height="471" alt="image" src="https://github.com/user-attachments/assets/7412df20-4021-41cc-b686-44b8991a6981" />

<img width="720" height="486" alt="image" src="https://github.com/user-attachments/assets/8761b555-2b48-42a3-99bb-cb3fed0681be" />

<img width="720" height="327" alt="image" src="https://github.com/user-attachments/assets/d2be653c-b35a-484f-9ed7-673b5e534f81" />
