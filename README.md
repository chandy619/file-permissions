<p align="center">
<img width="357" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/3c6d72a8-0fcb-4f2b-9c64-3264164bfa75">
</p>

<h1>Understanding File Shares and Permissions</h1>
This lab focuses on file shares and permissions in the context of an Active Directory domain. File shares and permissions are key in business settings to make sure users have the appropriate access and permission to files within the organization's network. Continuing from the last lab, I will be logged in as Jane Doe (Admin User) on  Domain Controller (DC-1) VM and Leveke Basij (User) on Client-1 VM. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (21H2)

<h2>High-Level Steps</h2>

- Create Sample Files with Various Permissions
- Attempt Accessing File Shares
- Create Security Group, Assign Permissions, Test Access
  
<h2>File Shares and Permissions Configuration Steps</h2>

<p>
<img width="960" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/5dba91df-b52b-42a7-9363-0af7e1815f0a">
<img width="960" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/d1f670f6-b983-4abb-be07-f3ded29ffd7f">
<img width="960" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/5b45b6d5-2bf1-4419-97d8-10e983bc61f4">
</p>
<p>
Beginning on DC-1, create 4 folders on the C:\ drive and label each: 'read-access', "write-access', 'no-access', 'accounting'. To set the permissions for each folder, begin by right-clicking on a folder. We'll start with 'read-access' > 'Properties' > 'Sharing' tab > 'Share' button > type in 'Domain Users' > 'Add' button > set permission level to 'Read' > 'Share' button. We'll do the same for the "write- access' folder except the permission level will be for 'Read/Write'. Next, we'll follow the same steps for the 'no-access' folder, except we'll type in 'Domain Admins' instead and allow 'Read/Write' permissions. We'll come back to the 'accounting' folder later.
</p>
<br />

<p>
<img width="960" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/06e69ed3-a1c4-4d73-8834-8dbc01647325">
<img width="960" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/57da8031-88b6-4862-9f99-449a6f74b324">
<img width="960" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/ce95933b-e610-42ef-b592-5a49ae3aa960">
</p>
<p>
Switch to Client'1's VM and open File Explorer. Enter '\\dc-1' into the 'Quick Access' bar to locate the network shared folders. Since you are logged in as a normal 'Domain User', you will notice you won't have access to the 'no-access' folder. You will also find you will not be able to add new files to the 'read-access' folder, but you will be able to in the 'write-access' folder. This is because we've set specific permissions for each folder.
</p>
<br />

<p>
<img width="960" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/73821a17-1366-43ff-84fd-1aefcfdf2135">
<img width="960" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/ac0f2b80-8087-4bfd-8be0-5adcac88edf1">
<img width="960" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/f2972b86-aaea-4eb5-8939-668027201d3f">
</p>
<p>
Next, go back to DC-1, in Active Directory (AD), we will create a new Organizational Unit (OU) named '_SECURITY_GROUPS'. Within the new OU, create a new group called 'ACCOUNTANTS'. Then, open up File Explorer to set permissions to the 'accounting' folder. Right-click folder > 'Sharing' tab > type in 'ACCOUNTANTS' > 'Add' button > set permission level to 'Read/Write' > 'Share' button. We have essentially allowed members of the 'ACCOUNTANTS' group access to the 'accounting' folder.
</p>
<br />

<p>
<img width="960" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/5933d025-466e-4a3b-9039-b06964ebcbf4">
<img width="960" alt="image" src="https://github.com/chandy619/file-permissions/assets/144288806/471ccb85-1502-4930-b765-a6d7d052a81e">
</p>
<p>
From AD, double-click on the 'ACCOUNTANTS' group name, click on the 'Members' tab. To add Client-1's user to the group, click on the 'Add' button and type in the username, i.e 'leveke.basij'. Remember to click 'Check Names' so that it populates correctly before clicking 'OK' and 'Apply'. Return to Client-1 and logoff. You'll have to log back in once more so that the new files permissions can apply. In File Explorer, you will be able to open the 'accounting' folder with read and write access.
</p>
<br />
