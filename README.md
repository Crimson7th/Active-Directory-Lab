# Active-Directory-Lab
Active Directory Home Lab With Bulk User Creation
Description
This project is demonstration of creating an active directory home lab on Virtualbox. I will be creating a Domain Controller (DC) using Microsoft Server 2022 and a domain using Microsoft Windows 11 Enterprise. To simulate a large business environment I will create over 1000 users in Active Directory and proceed to log into those newly created accounts on the domain via internet. In this lab I'll need a Microsoft Server 2022 ISO, A Windows 11 Enterprise ISO, VMWare and a Powershell script

Software Requirement
Environment Used
Oracle Virtualbox Manager (windows) 
Microsoft Server 2022 21H2
Microsoft Windows 11 Enterprise

Language and Utilities Used
Active Directory
PowerShell
Command Prompt (cmd.exe)

The topology of my active direcotory lab for this project -

![Act](https://github.com/user-attachments/assets/049aa671-34c0-4f11-9141-f3d0133c67ca)


Created the domain controller and named it MARVEL.local

Details used-
Root domain name: MARVEL.local
NetBIOS doamin name: MARVEL
After restart the logon portal will look like this (MARVEL/ in front of our user)-

--HERE--

image

Now lets setup Users on our server. If you are ever getting confused about the user and password just follow the topology. Also in this video we create a share so we enable the port 139 for SMB service as most organisation have to share files and they do it via SMB share on port 139 and we are trying to simulate that.

Details used-
username : password = fcastle:Password1, mmurdock:Password2, tstark:Morgan@2022, sqlservice:MYpassword!@#2023
file share profile = SMB Share - Quick
file share name = Micro
 adding-user-share.mp4 
I forgot to record the part where i put the SQLService user password in its description which you can see is shown after I was finished creating users. I did this because many admins thinks that description can't be read by others which we'll show that its not true in our ActiveDirectoryAttacks.

Lets change few policies and permissions so that when we do ActiveDirectoryAttacks, we have several attack vectors to practice on.

 adding-policies.mp4 
Lets take a snapshot here as we have done steps followed by TCM so if anything goes wrong we can turn back.

Now lets login to domain specific Tony Stark account instead of Administrator in Server 2022 with credential (MARVEL\tstark : Morgan@2022)-

image

Now lets install Remote Access with RAS and Routing server roles so our client computers can acess the internet via our DC and configure it with NAT service on our vnet0 network-

 setting-RAS-with-NAT-config.mp4 
After config It started showing error & asking to restart so I did and it fixed the problem. Next step is to setup DHCP roles to our AD environment-

 installing-DHCP.mp4 
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
