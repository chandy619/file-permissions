<p align="center">
<img width="357" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/3c6d72a8-0fcb-4f2b-9c64-3264164bfa75">
</p>

<h1>Understanding File Shares and Permissions</h1>
This lab focuses on file shares and permissions in the context of an Active Directory domain. File shares and permissions are key in a business setting to make sure users have the appropriate access and permission to files within the organization's network. Continuing from the last tutorial, I will be logged in as Jane Doe (Admin User) on  Domain Controller (DC-1) VM. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (21H2)

<h2>High-Level Steps Steps</h2>

- Create Sample Files with Various Permissions
- Attempt Accessing File Shares
- Create Security Group, Assign Permissions, Test Access
  
<h2>File Permissions Configuration Steps</h2>

<p>
<img width="796" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/bf091233-1d7b-4f14-8aa0-8a2361cdd2b5">
</p>
<p>
Start by opening 'Active Directory Users and Computers' from the Start menu. Find a random username generated from the previous lab, i.e. Bah Dop, and login to Client-1 VM using Remote Desktop. Remember the password is 'Password1'. Back on DC-1, create 4 folders on the C:\ drive and label each: 'read-access', "write-access', 'no-access', 'accounting'. To set the permissions for each folder, begin by right-clicking on a folder. We'll start with 'read-access' > 'Permissions' > 'Sharing' tab > 'Share' button > type in 'Domain Users' > 'Add' button > set permission level to 'Read' > 'Share' button. We'll do the same for the "write- access' folder except the permission level will be for 'Read/Write'. Next, we'll follow the same steps for the 'no-access' folder, except we'll type in 'Domain Admins' instead and allow 'Read/Write' permissions. We'll come back to the 'accounting' folder later.
</p>
<br />

<p>
<img width="372" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/d22bd818-e4af-4132-9531-a06b87ba28f0">
<img width="358" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/6b754c53-ae87-4f53-a7a7-d3108723d304">
</p>
<p>
Switch to Client'1's VM and open File Explorer. Enter '\\dc-1' to locate the network shared folders. Since you are logged in as a normal 'Domain User', you will notice you won't have access to the 'no-access' folder and you will not be able to add new files to the 'read-access' folder, but you will be able to in the 'write-access' folder. This is because we've set specific permissions for each folder.
</p>
<br />

<p>
<img width="267" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/99fa91df-f6f0-411e-805a-80b1832498be">
<img width="217" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/c39f1d47-8f58-43fb-9717-8c10d597730f">
<img width="285" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/46c8f441-e9df-49f1-b9a5-4b8d16329b6b">
</p>
<p>
Next, go back to DC-1, in Active Directory (AD), we will create a new Organizational Unit (OU) named '_SECURITY_GROUPS'. Within the new OU, create a new group called 'ACCOUNTANTS'. Then, open up File Explorer to set permissions to the 'accounting' folder. Right-click folder > 'Sharing' tab > type in 'ACCOUNTANTS' > 'Add' button > set permission level to 'Read/Write' > 'Share' button. We have essentially allowed members of the 'ACCOUNTANTS' group access to the 'accounting' folder.
</p>
<br />

<p>
<img width="350" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/cc46345d-fbc6-4b12-967d-b86d94a01bed">
<img width="360" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/10ef2024-c5b0-466e-a53f-32e3b826391a">
</p>
<p>
From AD, double-click on the 'ACCOUNTANTS' group name, click on the 'Members' tab. To add Client-1's user to the group, click on the 'Add' button and type in the username. Remember to click 'Check Names' so that it populates correctly before clicking 'OK' and 'Apply'. Return to Client-1 and logoff so that when you log back in, the new permissions will apply. In File Explorer, you will be able to open the 'accounting' folder.
</p>
<br />
