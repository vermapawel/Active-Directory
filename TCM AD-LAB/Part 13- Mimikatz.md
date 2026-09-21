**Mimikatz**

On the Kali mahine, google Mimikatz

```
https://github.com/gentilkiwi/mimikatz/releases?source=post_page-----73129bc58db8-----------------------------------------
```

<img width="720" height="319" alt="image" src="https://github.com/user-attachments/assets/7d781697-9326-4753-9bc0-2e435535efab" />

Lets download the latest version available

<img width="720" height="255" alt="image" src="https://github.com/user-attachments/assets/31677e8d-b329-4fd3-95db-4735738a0e3b" />

Extract it in a folder.

<img width="720" height="194" alt="image" src="https://github.com/user-attachments/assets/85fe4396-5ddb-45ac-87a9-6be5b6da1811" />

Now, we need to move these four files to the Spiderman machine

Lets go to the folder where we have extracted the files and start a python server

<img width="720" height="183" alt="image" src="https://github.com/user-attachments/assets/d1f56af0-25fa-4c19-a7bf-1b342c8207f0" />

Lets login at Spiderman machine as a normal user

.\peterparker || Password123

Go to any browser and put kali machine IP with port

<img width="662" height="265" alt="image" src="https://github.com/user-attachments/assets/27860051-4d6a-4f26-9d11-8a4f4b0e83b5" />

Lets download all 4 files. It will throw warning and windows will delete the files. Turn off ‘Real Time Protection’ setting in Windows Defender.

Now lets open the CMD as administrator. Go to download and run mimikatz.exe

<img width="720" height="486" alt="image" src="https://github.com/user-attachments/assets/65bc1e24-6b42-447d-91e6-247958b86a83" />

We need to set the privilege mode of mimikatz to debugg

<img width="720" height="263" alt="image" src="https://github.com/user-attachments/assets/9d598c92-c1a9-4e4a-a456-70a32cc70d75" />

***sekurlsa::logonPasswords***

<img width="720" height="500" alt="image" src="https://github.com/user-attachments/assets/e906b3cf-c1b2-46f8-88f2-9ae6b9d9cd4e" />

We got local Administrator Password here.

This is becase there is a file share in the Spiderman machine and when we try to access it, it ask for Admin username and password. Those password got stored.

<img width="720" height="260" alt="image" src="https://github.com/user-attachments/assets/a41940b8-8853-4f8b-a882-c3f586f72429" />

Also we can see all types of Hashes available

<img width="720" height="515" alt="image" src="https://github.com/user-attachments/assets/f4c86c84-9dc7-4357-96a2-836dab95c7fb" />

Lets scroll down and see what else we have

<img width="720" height="274" alt="image" src="https://github.com/user-attachments/assets/454dc974-3bd7-4c2c-9dfb-ea93ca7c9d89" />

We got a password which is encrypted. We can try to break it.


