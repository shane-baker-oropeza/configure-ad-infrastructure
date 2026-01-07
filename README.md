<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create Domain controller and separate workstation in Azure
- Login into Domain controller and Install Active Directory
- Create a Domain Admin User within the Domain
- Join client-1 to the domain name (mydomain.com as example)
- Setup Remote Desktop for non-administrative users on client-1
- Create additional users in Powershell

<h2>Deployment and Configuration Steps</h2>

<p>
<h3>Step 1: Network Infrastructure: </h3>
  
Create a Resource Group to contain all your lab assets.
Create a Virtual Network (VNet) and a Subnet to allow communication between your machines.
</p>
<br />

<p>
<img width="611" height="617" alt="Screenshot 2026-01-04 183833" src="https://github.com/user-attachments/assets/418cd945-7982-4edb-ad31-947ebdc66e1c" />

</p>

<p>
<img width="950" height="544" alt="Screenshot 2026-01-04 183850" src="https://github.com/user-attachments/assets/d3094c0e-1da3-46d9-9c91-31547418b7d8" />

</p>

<p>
<img width="767" height="868" alt="Screenshot 2026-01-04 183948" src="https://github.com/user-attachments/assets/5e3686c9-f6a8-46cb-9435-f12bfe2368e9" />

</p>

<p>
<img width="757" height="811" alt="Screenshot 2026-01-04 184054" src="https://github.com/user-attachments/assets/0753413e-c7e1-421f-b62a-e6cdce3b126c" />

</p>

<p>
<img width="1214" height="653" alt="Screenshot 2026-01-04 184127" src="https://github.com/user-attachments/assets/0c2004b2-da49-4e2e-b79d-ed70e26127f3" />

</p>

<p>
<img width="840" height="872" alt="Screenshot 2026-01-04 184204" src="https://github.com/user-attachments/assets/cded3f90-2412-42b9-b1bf-3a931165ab28" />

</p>

<p>
<img width="839" height="853" alt="Screenshot 2026-01-04 184222" src="https://github.com/user-attachments/assets/5aad9448-4c71-4caf-8dd5-6f34cff81d75" />

</p>

<p>
<img width="641" height="860" alt="Screenshot 2026-01-04 184249" src="https://github.com/user-attachments/assets/7e72df22-abae-4cc1-a154-21b56867eaf6" />

</p>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<h3>Step 2: Domain Controller (DC-1) Setup: </h3>
  
Create a Virtual Machine named DC-1 running Windows Server 2022.
Once created, navigate to the Azure Portal and set the Network Interface (NIC) Private IP address to Static.
Remote Desktop (RDP) into DC-1 and disable the Windows Firewall to ensure it can respond to connectivity tests.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  
<h3>Step 3: Client Machine (Client-1) Setup: </h3>
  
Create a Virtual Machine named Client-1 running Windows 10.  Ensure Client-1 is placed in the same region and Virtual Network as DC-1.
In the Azure Portal, update Client-1’s DNS settings to point directly to DC-1’s Private IP address.  Restart Client-1 from the portal to apply the DNS changes.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<h3>Step 4: Connectivity Verification: </h3> 
  
Log into Client-1.  Open a command prompt and ping DC-1’s private IP address to ensure the connection is successful.
Open PowerShell and run ipconfig /all to confirm that the DNS Server list accurately displays DC-1’s private IP address.
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

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
