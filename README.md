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
Start by finding a random username generated from the previous lab, i.e. Bah Dop, and login to Client-1 VM using Remote Desktop. Remember the password is 'Password1'. Back on DC-1, create 4 folders on the C:\ drive and label each: 'Read-access', "Write-access', 'No-access', 'Accounting'. Open up 'Active Directory Users and Computers' from the Start menu. Set the following permissions for each folder by right-clicking the folder > 'Permissions' > 'Sharing' tab > 'Share' button > type in 'Domain Users' > 'Add' button > set permission level to 'Read' > 'Share' button. We'll do the dame for the "Write- access' folder except the permission level will be for 'Read/Write'. Next, we'll follow the same steps for the 'No-access' folder, except we'll type in 'Domain Admins' for share access and allow 'Read/Write' permissions.
</p>
<br />

<p>
IMAGE
</p>
<p>
TEXT
</p>
<br />

<p>
IMAGE
</p>
<p>
TEXT
</p>
<br />

<p>
IMAGE
</p>
<p>
TEXT
</p>
<br />

<p>
IMAGE
</p>
<p>
TEXT
</p>
<br />
