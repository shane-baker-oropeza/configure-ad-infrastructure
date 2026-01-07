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
<h3>Step 2: Domain Controller (DC-1) Setup: </h3>
  
Create a Virtual Machine named DC-1 running Windows Server 2022.
Once created, navigate to the Azure Portal and set the Network Interface (NIC) Private IP address to Static.
Remote Desktop (RDP) into DC-1 and disable the Windows Firewall to ensure it can respond to connectivity tests.
</p>
<br />

<p>
<img width="834" height="812" alt="Screenshot 2026-01-04 184332" src="https://github.com/user-attachments/assets/36a2f91d-948b-4355-b855-b98dabb0ce87" />

</p>
<p>

<p>
<img width="1200" height="834" alt="Screenshot 2026-01-04 184407" src="https://github.com/user-attachments/assets/a6411367-a5f0-42f7-b78e-eb3d2449a8d8" />

</p>
<p>

<p>
<img width="1115" height="841" alt="Screenshot 2026-01-04 184438" src="https://github.com/user-attachments/assets/47700a25-2da4-411e-8631-a896b22d1ee6" />

</p>
<p>

<p>
<img width="923" height="851" alt="Screenshot 2026-01-04 184755" src="https://github.com/user-attachments/assets/7bfc93af-da64-45b7-bd71-d970cca4b05b" />

</p>
<p>

<p>
<img width="855" height="703" alt="Screenshot 2026-01-04 184822" src="https://github.com/user-attachments/assets/ac521881-fdef-41ec-bac0-397b4cead842" />

</p>
<p>

<p>
<img width="955" height="851" alt="Screenshot 2026-01-04 185120" src="https://github.com/user-attachments/assets/91135471-06b8-421b-9eda-ee4a414c1845" />

</p>
<p>

<p>
<img width="984" height="861" alt="Screenshot 2026-01-04 185144" src="https://github.com/user-attachments/assets/d1727322-12e4-44de-a27d-dfe703b4d605" />

</p>
<p>

<p>
<img width="1276" height="612" alt="Screenshot 2026-01-04 185845" src="https://github.com/user-attachments/assets/005e92ae-ea7a-479a-acdf-c9e433168eef" />

</p>
<p>

<p>
<img width="1267" height="855" alt="Screenshot 2026-01-04 185859" src="https://github.com/user-attachments/assets/d72a9eef-ab13-4bdd-9f4d-16f1e67f412d" />

</p>
<p>

<p>
<img width="1122" height="830" alt="Screenshot 2026-01-04 185922" src="https://github.com/user-attachments/assets/fe310f06-e65f-46d4-8b24-00e8cbb43abd" />

</p>
<p>

<p>
<img width="1260" height="838" alt="Screenshot 2026-01-04 185935" src="https://github.com/user-attachments/assets/364e63db-11a3-4159-8087-fcd3269ecbfc" />

</p>
<p>

<p>
<img width="1008" height="771" alt="Screenshot 2026-01-04 190014" src="https://github.com/user-attachments/assets/b9b594c9-61cd-46ee-b5ed-acd3b1d72370" />

</p>
<p>

<p>
<img width="1179" height="816" alt="Screenshot 2026-01-04 190026" src="https://github.com/user-attachments/assets/2954a268-aa3c-4d1f-a6d4-75c55e928a40" />

</p>
<p>

<p>
<img width="1274" height="853" alt="Screenshot 2026-01-04 190057" src="https://github.com/user-attachments/assets/0f0365a6-230f-45ab-b812-7d1b744c4ca5" />

</p>
<p>

<p>
<img width="1215" height="841" alt="Screenshot 2026-01-04 190138" src="https://github.com/user-attachments/assets/5f5e76f8-1480-4284-b405-626f50d67fcd" />

</p>
<p>

<p>
<img width="474" height="284" alt="Screenshot 2026-01-04 190157" src="https://github.com/user-attachments/assets/5c827c9e-1efa-4ea8-91d8-d5ceb6adb2ab" />

</p>
<p>

<p>
<img width="485" height="419" alt="Screenshot 2026-01-04 190223" src="https://github.com/user-attachments/assets/8602ebf7-6f25-484e-b415-7ee837d2e930" />

</p>
<p>

<p>
<img width="417" height="416" alt="Screenshot 2026-01-04 190234" src="https://github.com/user-attachments/assets/8a7e996b-cc1e-4c7e-81e4-d6a349745519" />

</p>
<p>

<p>
<img width="341" height="644" alt="Screenshot 2026-01-04 190414" src="https://github.com/user-attachments/assets/2cfa21f0-d55e-422f-ab43-42413f3c2072" />

</p>
<p>

<p>
<img width="456" height="283" alt="Screenshot 2026-01-04 190442" src="https://github.com/user-attachments/assets/f26eda4e-a14e-4d61-8b11-c1f958935a1f" />

</p>
<p>

<p>
<img width="1003" height="623" alt="Screenshot 2026-01-04 190458" src="https://github.com/user-attachments/assets/1a69437e-4111-429e-b9da-44245f71e4df" />

</p>
<p>

<p>
<img width="458" height="481" alt="Screenshot 2026-01-04 190508" src="https://github.com/user-attachments/assets/20076c6a-d7f0-466b-8cf8-0fa752d6a09b" />

</p>
<p>

<p>
<img width="462" height="467" alt="Screenshot 2026-01-04 190526" src="https://github.com/user-attachments/assets/3dc1f58a-32ff-4a8c-bdfb-21addb88da48" />

</p>
<p>

<p>
<img width="426" height="462" alt="Screenshot 2026-01-04 190534" src="https://github.com/user-attachments/assets/07fc01d9-47b5-4c2b-aad4-483cd42bcaeb" />

</p>
<p>

<p>
<img width="432" height="469" alt="Screenshot 2026-01-04 190545" src="https://github.com/user-attachments/assets/88135c16-a3c4-4931-b20e-a05f14a3872b" />

</p>

<p>
<img width="444" height="607" alt="Screenshot 2026-01-04 190610" src="https://github.com/user-attachments/assets/e775b832-25ae-4586-99d6-31c3a1359318" />

</p>
<p>

<p>
<img width="444" height="601" alt="Screenshot 2026-01-04 190618" src="https://github.com/user-attachments/assets/20a0714a-a8af-4cd5-9309-8650159e4552" />

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
