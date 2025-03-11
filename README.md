<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="![image](https://github.com/user-attachments/assets/8d95625a-f9a8-4688-a85a-78becc6edd2f)
"/>
</p>
<p>
Installing Active Directory.  
  Login to your Domain Controller (For this example mine was named 'DC-1') and install Active Directory Domain Services
Promote as a DC: Setup a new forest as mydomain.com (can be anything, just remember what it is)
Restart and then log back into DC-1 as the user 

</p>
<br />

<p>
<img src="![image](https://github.com/user-attachments/assets/75a20024-a4a2-46d5-a8a9-8aaa23724f08)
"/>
</p>
<p>
Create a Domain Admin user within the domain
—
In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES”
Create a new OU named “_ADMINS”
Create a new employee named “Jane Doe” (same password) with the username of “jane_admin” / Cyberlab123!
Add jane_admin to the “Domain Admins” Security Group
Log out / close the connection to DC-1 and log back in as “mydomain.com\jane_admin”
User jane_admin as your admin account from now on

</p>
<br />

<p>
<img src="![image](https://github.com/user-attachments/assets/648974fb-c746-4f71-a50b-8d56e89b4c76)
"/>
</p>
<p>
From the Azure Portal, set Client-1 (The other virtual machine created)'s private IP address to match DC-1'S, then restart Client-1 
  Login to Client-1 as the original local admin (labuser) and join it to the domain (computer will restart)
Login to the Domain Controller and verify Client-1 shows up in ADUC
Create a new OU named “_CLIENTS” and drag Client-1 into there

</p>
<br />

<p>
<img src="![image](https://github.com/user-attachments/assets/648974fb-c746-4f71-a50b-8d56e89b4c76)
"/>
</p>
<p>
Setup Remote Desktop for non-administrative users on Client-1
—
Log into Client-1 as mydomain.com\jane_admin
Open system properties
Click “Remote Desktop”
Allow “domain users” access to remote desktop
You can now log into Client-1 as a normal, non-administrative user now


</p>
<br />


<p>
<img src="![image](https://github.com/user-attachments/assets/648974fb-c746-4f71-a50b-8d56e89b4c76)
"/>
</p>
<p>
Create a bunch of additional users and attempt to log into client-1 with one of the users
—
I had a pre-written script to execute code in order to create 10000 users the script was not written by me
  Login to DC-1 as jane_admin
Open PowerShell_ise as an administrator
Create a new File and paste the contents of the script into it
Run the script and observe the accounts being created
When finished, open ADUC and observe the accounts in the appropriate OU　(_EMPLOYEES)
attempt to log into Client-1 with one of the accounts 

The password for all the users created from the script were all the same 


</p>
<br />


