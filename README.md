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
<br>
<br>


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

![Act8](https://github.com/user-attachments/assets/f7aacf2d-bf47-4e38-b198-75b085f5ed0b)


<br>

Now that we have successfully logged in lets begin the user creation with our script and also a name.txt file. 

![Act6](https://github.com/user-attachments/assets/5ccde1f4-b6de-472b-9d44-04b1d96d1492)
<br>
here is the .ps1 creation file creating the 1000 users all with the Password1.
<br>
<br>
![Act7](https://github.com/user-attachments/assets/56e68eaa-09de-4a97-8c52-35c8f4dd7632)

Here are the created users from the script.


Credits
I made this project to revise the Active Directory stuff I learned from PEH Course by @hmaverickadams.
