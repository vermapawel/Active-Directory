**Joining Our Machines to the Domain**

We need to set IP address of DC as DNS of these machines

<img width="720" height="269" alt="image" src="https://github.com/user-attachments/assets/0f3c8ad3-a3bd-4a3e-a2f5-e133842bd2e8" />

Now, we need to join the Domain

<img width="720" height="421" alt="image" src="https://github.com/user-attachments/assets/c2b940f8-23db-4801-86b7-b89a61838cc2" />

<img width="661" height="611" alt="image" src="https://github.com/user-attachments/assets/26192610-6bd0-440f-8e34-5e281ff8bddc" />

<img width="720" height="341" alt="image" src="https://github.com/user-attachments/assets/1d454ca0-4611-43ff-8fd3-186e0ed27637" />

Hit Enter !!!

<img width="720" height="433" alt="image" src="https://github.com/user-attachments/assets/6c1ed56a-c6dc-4505-ac0f-f63e5978cdec" />

<img width="720" height="427" alt="image" src="https://github.com/user-attachments/assets/14291153-7d7b-4c77-880e-903f1fddb443" />

<img width="720" height="353" alt="image" src="https://github.com/user-attachments/assets/eeba4138-42d9-47e4-aa78-626f955feb3c" />

Similarly we will do for othe machine.

Lets verify on the DC

<img width="720" height="273" alt="image" src="https://github.com/user-attachments/assets/f87abf2f-c6b2-4bf5-9c55-ca8b717db7dd" />

<img width="720" height="291" alt="image" src="https://github.com/user-attachments/assets/5bfc71cc-cfdd-4937-8322-432759080f4e" />

We can see both machines joined the DC

Once Reboot is now, we will login as MARVEL\Administrator on PUNISHER machine

<img width="720" height="373" alt="image" src="https://github.com/user-attachments/assets/220cf795-6bdb-4fde-818d-f4f222d99ece" />

<img width="720" height="670" alt="image" src="https://github.com/user-attachments/assets/c29fb1b9-99a5-479f-9b7e-16d815c11c26" />

<img width="720" height="321" alt="image" src="https://github.com/user-attachments/assets/5effa905-5fee-4d24-9175-58b95de274ec" />

There are two users, frankcastel and Administrator.

Administrator user is disabled, lets enable it.

<img width="720" height="301" alt="image" src="https://github.com/user-attachments/assets/c15f0fb9-5f5b-48b8-ae64-1c445b50948d" />

<img width="720" height="465" alt="image" src="https://github.com/user-attachments/assets/21b97067-5b2e-4827-9f68-92b537201daa" />

Password is Password1!

<img width="720" height="580" alt="image" src="https://github.com/user-attachments/assets/f2e673e8-08d9-4658-87e7-eefb19043d65" />

Lets check Groups

<img width="720" height="510" alt="image" src="https://github.com/user-attachments/assets/7a6f011b-e474-44a9-a26e-ea75989647f8" />

Under Administrator Groups these are the users. Lets add one more

<img width="720" height="385" alt="image" src="https://github.com/user-attachments/assets/68fb2e22-a35b-42cf-a429-3a980fabaebd" />

<img width="720" height="486" alt="image" src="https://github.com/user-attachments/assets/4966602e-618b-4152-a764-fc3dc2fe77ec" />

Now, lets go to Network

<img width="720" height="307" alt="image" src="https://github.com/user-attachments/assets/630b9043-5104-4482-9286-1bbd79ea9169" />

Network discovery is off. Turn it on

<img width="720" height="263" alt="image" src="https://github.com/user-attachments/assets/a8b0f2c5-315c-4b7a-a53f-6e4d4f850c29" />

Win + R > \\192.168.1.100 or \\MARVEL.local

<img width="720" height="282" alt="image" src="https://github.com/user-attachments/assets/75c2f90e-1cb2-40b3-be15-93016f568a71" />

And we can see the hackme folder.

========================================================================================================================

Now, let configure the other machine SPIDERMAN

We will login as MARVEL\Administrator

<img width="720" height="533" alt="image" src="https://github.com/user-attachments/assets/16956ed1-583b-4721-b6f3-cc625c1a20fc" />

<img width="720" height="343" alt="image" src="https://github.com/user-attachments/assets/5b29ad50-a525-49c0-83d2-ef3d581286b5" />

Lets set password for Administrator

<img width="720" height="468" alt="image" src="https://github.com/user-attachments/assets/1e4b21ef-4270-4f5d-92a1-6b7b28ae9ad1" />

We are setting the same password i.e Password1!

<img width="720" height="584" alt="image" src="https://github.com/user-attachments/assets/d86b1e5d-88b4-4220-bb6e-f5ace1e8180a" />

Lets go to Groups, We will add two Administrators

<img width="720" height="480" alt="image" src="https://github.com/user-attachments/assets/28331d9a-4402-4732-a370-502156bb6b78" />

<img width="720" height="336" alt="image" src="https://github.com/user-attachments/assets/aa59ae58-89ad-42f6-aeca-a57155ef2c26" />

<img width="720" height="332" alt="image" src="https://github.com/user-attachments/assets/d6306c7f-16bf-441c-8819-a726bece74b3" />

<img width="596" height="585" alt="image" src="https://github.com/user-attachments/assets/ae43a957-7286-429e-ab8f-d5ee7f6301f2" />

Now, lets turn on the Network discovery as we did on last machine

<img width="720" height="430" alt="image" src="https://github.com/user-attachments/assets/226dc0b6-41d0-4936-82e9-29531bfa9468" />

<img width="720" height="315" alt="image" src="https://github.com/user-attachments/assets/b62a69a5-a76d-4b11-a442-3424548244dc" />

Now, lets logout and login as local user

.\peterparker || Password123

<img width="720" height="362" alt="image" src="https://github.com/user-attachments/assets/f2be7775-37ec-4382-8c5c-5126b10360eb" />

Once logged in This PC > Computer > Map network drive

<img width="720" height="283" alt="image" src="https://github.com/user-attachments/assets/e6224975-81aa-4a49-9157-a5901bd3c97d" />

<img width="720" height="396" alt="image" src="https://github.com/user-attachments/assets/33d7b05c-936a-4e9a-9418-0f09dd3c0a7e" />

<img width="720" height="396" alt="image" src="https://github.com/user-attachments/assets/9814a152-5541-474e-b2fd-5c98aa0791af" />

It will ask for credentials. Administrator | Password123

<img width="720" height="390" alt="image" src="https://github.com/user-attachments/assets/35d9e48e-d691-4dd9-876f-dfffb02875c3" />

And we have a shared drive available in this machine.

