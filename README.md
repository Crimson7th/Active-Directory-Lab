# Active-Directory-Lab
Active Directory Home Lab With Bulk User Creation
Description
This project is demonstration of creating an active directory home lab on Virtualbox. I will be creating a Domain Controller (DC) using Microsoft Server 2022 and a domain using Microsoft Windows 11 Enterprise. To simulate a large business environment I will create over 1000 users in Active Directory and proceed to log into those newly created accounts on the domain via internet. In this lab I'll need a Microsoft Server 2022 ISO, A Windows 11 Enterprise ISO, Virtualbox and a Powershell script

Software Requirement
Environment Used
Oracle Virtualbox Manager (windows) 
Microsoft Server 2022 21H2
Microsoft Windows 11 Enterprise

Language and Utilities Used
Active Directory
PowerShell

The topology of my active direcotory lab for this project -

![Act](https://github.com/user-attachments/assets/049aa671-34c0-4f11-9141-f3d0133c67ca)


Created the domain controller and named it MARVEL.local

Details used-
Root domain name: MARVEL.local
NetBIOS doamin name: MARVEL
After restart the logon portal will look like this (MARVEL/ in front of our user)-

![Act3](https://github.com/user-attachments/assets/5100585f-abeb-4888-ab35-52a22a2d126a)



Now lets setup Users on our server. 

<br>
<br>

![Act2](https://github.com/user-attachments/assets/31da5d8e-20d3-4e4a-a058-5d5f841191fc)


Now lets login to domain specific Tony Stark account instead of Administrator in Server 2022 with credential.
<br>
<br>

![Act4](https://github.com/user-attachments/assets/c446dd94-d3b4-4169-92c0-9f0414cb55a2)


![Act5](https://github.com/user-attachments/assets/8b4c79f6-ea31-421b-b2e5-dcf444892600)
<br>
<br>
<br>
<br>
![Act8](https://github.com/user-attachments/assets/85203b37-8a4e-4540-984f-5a09de550c24)



lets begin bulk user addition with our script. I have also added an additional script to add users using a name.txt file. Note that I pasted the code from main machine to server as its advised now to use Browser on the server machine-

 bulk-user-script.mp4 
Now that we are finished setting up our server machine, we can now install windows 11 (Client11)

Note: When we setup Windows 11 on VMWare it asks for encryption on the vm, which is requirement for updated windows so just put a simple password like Password and tick to remember it. We won't be needing this password in our ActiveDirectoryAttacks project.

Details used in windows 11 enterprise installation-
Enter your name : Client11
Password : Password12345
Security Questions : All answers were "bob"
Privacy settings : off to everything
First thing to do after login is to install VMWare tools and take snapshot then change computer name to THEPUNISHER and set network adapter to vnet0 and restart -

image

I have set both the machines this way with custom background to easily go back and forth -

image

Take a snapshot of this client machine so if anythings goes wront we can turn back.

image

Remember at this point it is absolutly important to have both machines running. Lets go to our client11 (THEPUNISHER) machine and make it a member of the domain "MARVEL.local" -

 joinig-client-to-server.mp4 
As you can see we got the MARVEL\fcastle on our logon portal -

image

As you can see we can ping domain and access internet -

image

To check the accounts we created via script lets logon to one of them after signing out of fcastle user-

 user-confirmation.mp4 
Credits
I made this project to revise the Active Directory stuff I learned from PEH Course by @hmaverickadams over 2 years ago.
