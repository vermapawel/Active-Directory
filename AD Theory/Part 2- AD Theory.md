**Active Directory (AD)** is a service developed by Microsoft for managing and organizing the resources within a network, such as users, computers, and other devices. It provides a centralized way to manage and secure large-scale IT environments.

The core services provided by Active Directory are:

1. Authentication → It verify user identity through various means like username and password. Through AD we are able to authenticate a user in AD network and assign a specific roles to the user.
   
2. Authorization → AD helps to ensure users have right permissions to access resources. So when a user is authenticated and he is able to access the domain however the user will access the domain with a specific role and specific set of permissions.

3. Directory services → AD allows to organize and manage network resources (users, computer, groups) and access policies in a centralized directories.

**Components of Active Directory**

**1. Domain Controllers (DC)**

Domain Controllers are a fundamental part of active directory.

They are used for many different tasks, including: 

- User Authentication
  
- Storing Active Directory data
  
- Managing and enforcing security policies
  
- Processing of directory queries.
  
In a big network, there could be multiple Domain Controller. They can be used in providing redundancy and load balancing. These DCs replicate data among themselves so that if one DC fails, the AD information is not lost.

**2. Domain Admins**

Members of the ~Domain Admins~ group have administrative privileges within a specific domain. They can add or remove accounts, change security rules, manage computers, and basically control everything inside that domain.

***net user*** >> to check user on a local machine

<img width="747" height="337" alt="image" src="https://github.com/user-attachments/assets/4f49fdca-8ee8-464c-a264-66eda392b8b4" />

Here there are two uses, Administrator and leo.

***net user /domain*** >> command to check users on Domain Controller

<img width="795" height="272" alt="image" src="https://github.com/user-attachments/assets/e65242a8-fd31-46e7-b54c-630cc28f0e0e" />

***net group*** >> to check user on a local machine

<img width="747" height="442" alt="image" src="https://github.com/user-attachments/assets/3b56cfdb-d58c-4a53-a8a9-3a26ab9f14af" />

***net group /domain*** >> It will show all the groups of AD.

<img width="707" height="427" alt="image" src="https://github.com/user-attachments/assets/8e2484b1-34a4-44bd-a62a-f547fc23fdc8" />

***whoami /groups*** >> It will show the groups a user belongs to

<img width="900" height="377" alt="image" src="https://github.com/user-attachments/assets/043266e8-5bd0-487c-84d7-b6125fe5bdac" />

The administrator belongs to Domain Admins group. So this user can manage the Domain Controller. Also in this case, this user is a Builtin Administrator of the Domain Controller. 

Any general user of the Domain can also be a Domain Admin. It is not required to be a local administrator to be in Domain Admin group. 

***net user <username>*** >> It will also show in which group a user is

<img width="790" height="510" alt="image" src="https://github.com/user-attachments/assets/43c15276-a7f8-45d5-a24a-533108afa4db" />

Local Group belongs to the local machine, and Global Group belongs to Domain controller. 

Now, there is a group who is more powerful than the Domain Admin and its called Enterprise Admins. The users in this groups have control over an entire forest.

**3. Group Policy Objects (GPOs)**

Group Policy is a feature that allows Administrator to define settings and enforce polices across users and computers in an AD domain. Instead of configuring each machine one by one, you set rules once and they apply across the domain

Examples:

-Force strong passwords.

-Disable USB storage.

-Set a company desktop wallpaper.

-Control software installation.

Group Policy Object (GPO) is the actual "package" of settings. Think of it as a container that holds all the rules we want to enforce.

<img width="890" height="251" alt="image" src="https://github.com/user-attachments/assets/2b4230c3-e684-4b3b-bed8-6978d5b833dd" />

To edit GPO, we use Group Management Feature and GPMC console which allow to create managed and apply GPOs to different parts of the AD structure.

***Win + R >> gpmc.msc***

<img width="900" height="376" alt="image" src="https://github.com/user-attachments/assets/59d68a65-1f93-4acb-bb7a-450cb3b069fe" />

We can see there are two Policies, Default Domain Policy and Hexdump lab policy.

GPOs are applied during the regular policy refresh interval (around every 90 mins), however we can force the new update by using following command

***gpupdagte /force***

GPOs are applied at different levels.

Local :- A single system 

Site :- A geographical location or network segment.

Domain :- All system within a domain

Organizational Unit (OU) :- Specific group or collection of system and users within the AD structure.

<img width="900" height="506" alt="image" src="https://github.com/user-attachments/assets/95af712c-b6cd-471d-9694-acdb935e6c9d" />

Here we can see that Hexdump policy is applied to Authenticated Users using Security Filtering. We can add another Group as well.

**4. Organizational Unit (OU)**

OUs are like folders within a domain used to organize AD objects. They help organize users, computers, and groups in a way that matches your company's structure (e.g., HR, IT, Finance).

To create a new OU, we can use Active Directory Users and Computers (ADUC) tool

**Win + R >> dsa.msc**

<img width="900" height="414" alt="image" src="https://github.com/user-attachments/assets/fad4d33f-b45c-4d64-b0ca-8679327d59d9" />

<img width="900" height="379" alt="image" src="https://github.com/user-attachments/assets/a616b161-598e-44db-9f68-5737bb80092b" />

Here we can see under hexdump.lab there are many folders. Lets create an OU

Right Clink hexdump.lab >> New >> Organizational Unit

<img width="821" height="592" alt="image" src="https://github.com/user-attachments/assets/7778a25f-38e2-4f87-9db9-43036eaed22c" />

<img width="835" height="372" alt="image" src="https://github.com/user-attachments/assets/b1bfdaed-b76b-4c9b-b20d-13e7862e9cf0" />

Lets create a new user.

Right click on blank space >> New >> User

<img width="727" height="312" alt="image" src="https://github.com/user-attachments/assets/d58b0e6d-329f-4dcc-aca2-7b1e928a3c17" />

User is created. matt || Password123

<img width="900" height="488" alt="image" src="https://github.com/user-attachments/assets/5ffc73fc-e987-41e4-9f30-314afe8a865d" />

Its a domain user. Lets verify

<img width="667" height="637" alt="image" src="https://github.com/user-attachments/assets/63fc135e-93c9-4bb1-89a2-cf9524d8b207" />

<img width="900" height="392" alt="image" src="https://github.com/user-attachments/assets/e14bad4f-c9bd-4d92-ba00-a833016e54c9" />

**5. Lightweight Directory Access Protocol (LDAP)**
   
Its a protocol used to query and interact with the directory service that store information about the AD (users, group, computers, printers etc)

<img width="900" height="268" alt="image" src="https://github.com/user-attachments/assets/682f6bba-7e81-49bd-936e-f8416a35cef4" />

Syntax for LDAP commands :- 

***Import-Module ActiveDirectory***

***Get-ADUser -LDAPFilter "(&(objectClass=user)(sAMAccountName=leo))"***

<img width="900" height="569" alt="image" src="https://github.com/user-attachments/assets/3485e008-1bd6-4dfe-8c62-3bcb9da1472f" />

**6. Kerberos**

Its a network authentication protocol. Its provides a secure method for authentication using centralized server (Domain Controller). 

Kerberos is a ticket based authentication system that uses a third party known as Key Distribution Center (KDC) to verify the identity of uses and services in the network. 

In context of AD, the KDC is implemented as part of the Domain Controller. It is built in. It is a service that Domain Controller puts on the users and machines in the AD.

KDC is responsible to authenticate the user and issuing tickets that are used to access the resource of the Domain.

<img width="686" height="337" alt="image" src="https://github.com/user-attachments/assets/5e7b0586-c47f-49f9-bcff-7cf10f14ae91" />

A user initiate an Authentication request to the KDC to obtain a ticket. 

This ticket is then issue to Kerberos to obtain a different ticket.

Then the user gives this 2nd ticket (issued by Kerberos) to the service (lets say printer) to access it.

**7. NTDS.dit**
   
The NTDS.dit file represents the core database where all the information about the AD is stored.

<img width="892" height="707" alt="image" src="https://github.com/user-attachments/assets/bf657030-9537-4905-baa1-4dd457aea73b" />

**8. SYSVOL (System Volume)**

Its a shared folder on Domain Controllers in AD that stores and replicates important system data across all Domain Controllers in a Domain.

Specifically SYSVOL contains GPO files and Scripts

<img width="900" height="704" alt="image" src="https://github.com/user-attachments/assets/15a97836-6125-40e6-920f-0708432b4fdf" />

So, any changes made in this directory are replicated across domain controller using File Replication Service (FRS) or Distributed File Replication Service (DFRS)

**9. Global Catalog**
    
It is a distributed data storage in AD that contains a partial replica of every object in AD forest. It helps in fast searching accross all domains in the forest.

<img width="900" height="750" alt="image" src="https://github.com/user-attachments/assets/154d59de-6157-41ff-9606-dc3838cba82b" />

**Domain, Forest and Trust**

**Domain** :- It is a logical grouping of objects (users, computers, groups) and is the core administrative unit in AD. The least we can have a Active Directory domain.

Each domain has its own SAM database, and within a domain authorization, policies and groups and centralized. 

If we have more than one domain, we can connect with each other. Depending on the connection we can have a Tree or Forest. 

**Tree** :- Tree is a collection of Domains that are connected in a hierarchical structure using a contiguous namespace. Here the domains share the common root domain. All domain within a tree are linked together using a trust relationship and share a common namespace. 

This means, all domains within a Tree are part of the same DNS domain structure.

-hexdump.lab

-domain1.hexdump.lab

-domain2.hexdump.lab

<img width="670" height="472" alt="image" src="https://github.com/user-attachments/assets/c3370475-1134-4c11-b073-4fe50ac07b84" />

**Forest** :- A Forest is the highest level of the AD hierarchy and represents the entire directory structure. 

It can contain one or more domain, but all domain within a Forest share a common schema and Global Catalog (GC)

Each Forest has at least on Domain and Domains within a Forest can be part of Trust Relationship, allowing users from one domain to access resources in another.

<img width="892" height="472" alt="image" src="https://github.com/user-attachments/assets/f79813a1-fce5-49c5-813f-30afb12267cb" />

**Trust Relationship:-** Trusts are ways to establish relationships between different AD domains and AD Forest.

Trusts allow users in one domain to access resources in another domain, simplifying cross-domain authentication and resource sharing.

There are various types of trusts:

-two-way trusts

-one-way trusts

-external trusts

-forest trusts

<img width="900" height="323" alt="image" src="https://github.com/user-attachments/assets/3a1d3222-3c3f-4b08-8aea-9afbbd34387b" />

