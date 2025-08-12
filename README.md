<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup up Azure Infrastucture: Create a resource group,virtual network, and subnet in Azure
- Deploy Virtual Machines: Deploy a Windows Server VM (will become the domain controller)
- Install Active Directory Domain services: One the windows Server VM install and promote it to a Domain Controller, creating a new Domain
- Join Windows 10 VM to the Domain: Connect the Windows 10 VM to the newly created Active Directory domain
- Create User Accounts: Use Powershell on the domain controller to bulk create user accounts
- Test Domain Login:Log into the Windows 10 VM using the domain user accounts to verify everything is working

<h2>Deployment and Configuration Steps</h2>

1. Setup Azure infrastructure.
   A. Create Resource groups
      •Go to Azure Portal → Create
      •Name it (e.g "Active DirectoryLab) select region and state and create
   <img width="1913" height="904" alt="Screenshot 2025-08-11 at 5 43 13 PM" src="https://github.com/user-attachments/assets/8a2b1c0a-b745-411e-9241-68af7b2bfa2b" />

   

    B. Create a Virtual Network and Subnet
      •Go to virtual network → Create
      •Name it (e.g, "AD-vnet) select the resource group and region
      •Accept default address space/subnet
   
   <img width="1910" height="618" alt="Screenshot 2025-08-11 at 6 22 06 PM" src="https://github.com/user-attachments/assets/690b198d-2697-461d-891f-2871b1c281b5" />


2. Deploy Virtual Machines
   A. Deploy Windows Server VM (Domain Controller)
     •Go to Virtual Machine → Create
     •Fill in:
              ◦Name: "DC1"
              ◦Resource group: ActiveDirectoryLab
              ◦Image: Windows Server 2022/2019
              ◦Region: Same as vnet
              ◦Size: Standard (2vCPU recommended)
              ◦Username/Password
              ◦Virtual Network: Select your "AD-vnet"
    •Set private IP to static after VM is created (in VM's network interface settings)
    <img width="1920" height="903" alt="Screenshot 2025-08-11 at 6 38 24 PM" src="https://github.com/user-attachments/assets/368a51af-47d2-4378-84bb-f7adf6b9e3c5" />
    <img width="1488" height="844" alt="Screenshot 2025-08-11 at 6 41 24 PM" src="https://github.com/user-attachments/assets/0c53aa2c-20d3-42b7-82f0-9803964c2433" />

    B.Deploy Windows 10 Client VM
     •Similiar steps as above but:
             ◦Name: Client 1
             ◦Image: Windows 10 pro
             ◦Network: "AD-vnet"
     •After deployment, change Client1's DNS settings (in NIC) to use DC1's static private IP address
   <img width="1458" height="833" alt="Screenshot 2025-08-11 at 6 52 42 PM" src="https://github.com/user-attachments/assets/50312388-970e-47d4-a5b4-8fccbed57d64" />
   <img width="1479" height="824" alt="Screenshot 2025-08-11 at 6 55 15 PM" src="https://github.com/user-attachments/assets/385aa3d7-ac36-4ca8-be65-cdf97491ab50" />


3. Install Active Directory Domain Services (AD DS)
   A. On DC1:
      •Connect using Remote Desktop
      •Open Server Manager → Add Roles and Features
      •Select "Active Directory Domain Services → Install
      •After installation, Click Promote to a domain controller → Create new forest
      •Confirmation screen of successful promotion/restart

4. Join Windows 10 VM to the Domain
      •RDP to Client1
      •Go to settings → System → About → Join Domain
      •Enter Domain (e.g "lab.local") and credentials of a domain admin.
      •Restart Client1.


5. Create User Accounts via Powershell
      •RDP to DC1
      •Open Powershell as Adminstrator
      •Use a script to bulk-create users

6. Test Domain Login
      •RDP to Client1
      •At login choose "Other user" enter "lab\User1 " and password
      •Confirm successful login
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
