<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Preparing Active Directory Infrastructure in Azure</h1>
This tutorial outlines the implementation of pre-installation of Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create a Resource Group that will contain the 2 virtual machines
- Create Domain controller and separate workstation in Azure

<h2>Deployment and Configuration Steps</h2>

<p>
<h3>Step 1: Network Infrastructure: </h3>
  
We will configure and interconnect two virtual machines, each with distinct roles. The first virtual machine will be a designated Domain Controller and the second virtual machine will be configured as the Client.
</p>
<br />

<p>
<img width="1173" height="837" alt="Screenshot 2026-01-04 183509" src="https://github.com/user-attachments/assets/6371fbe8-8e9c-4ca0-9e97-f05b8f0e2c2d" />

</p>

<p>
<h3>Step 2: Create a Resource Group: </h3>

  
•	Create a Resource Group in Microsoft Azure

•	Name it Active-Directory-Lab

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

<p>
<h3>Step 3: Create a Virtual Network: </h3>
  
**Create a Virtual Network (VNet) and a Subnet to allow communication between your machines**

•	Create a Virtual Network

•	Name it Active-Directory-Vnet


</p>
<br />

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
<h3>Step 4: Domain Controller (DC-1) Setup: </h3>
  
**Create two VMs (Azure) in the same VNET. One will be a Domain Controller, the other will be a Client machine**

•	Create a VM for the Domain Controller on Azure.

•	Select Resource Group (Active-Drectory-Lab)

•	Name it DC-1

•	Select Windows Server 2022 Datacenter: Azure Edition -x64 Gen2 as the Image

•	Size (Standard D2s v3 - 2 vcpus, 8 GiB memory)

•	Create a username and password for your VM DC-1

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
  
<h3> Create a VM for the client machine</h3>
  
• Create a new VM

•	Name it Client-1

•	Select the same resource group and Virtual network from the DC-1 VM (Active-Directory-Lab)

•	Select Windows 10 Enterprise as the image

•	Select at least 2 vcpus and 8 GiB memory

•	Create a username and password for your VM Client-1

•	Make sure to select box confirming eligible Windows 10/11 license

</p>
<br />

<p>
<img width="834" height="812" alt="Screenshot 2026-01-04 184332" src="https://github.com/user-attachments/assets/9b5cffba-0f52-4467-ae07-70db3d2cc478" />


</p>
<p>

<p>
<img width="1200" height="834" alt="Screenshot 2026-01-04 184407" src="https://github.com/user-attachments/assets/82583699-f3b2-4cc2-a4d4-5efeb23b6d80" />


</p>
<p>

<p>
<img width="924" height="853" alt="Screenshot 2026-01-04 185256" src="https://github.com/user-attachments/assets/9e5035d4-b859-4202-b634-a35331b811ba" />


</p>
<p>

<p>
<img width="941" height="855" alt="Screenshot 2026-01-04 185338" src="https://github.com/user-attachments/assets/dbf27f11-a9a0-4ab9-806f-59d784f2ab0f" />


</p>
<p>

<p>
<img width="871" height="830" alt="Screenshot 2026-01-04 185413" src="https://github.com/user-attachments/assets/a420037c-6cc6-4411-b23a-21ffc1cf7554" />


</p>
<p>

<p>
<img width="799" height="791" alt="Screenshot 2026-01-04 185430" src="https://github.com/user-attachments/assets/7e289c88-060c-4690-9093-e4b9f07f7541" />


</p>
<p>

<p>
<img width="994" height="854" alt="Screenshot 2026-01-04 185452" src="https://github.com/user-attachments/assets/63c2f7c7-6d5a-4257-b683-16756213aa05" />


</p>
<p>
  
<h3>Step 5: Set the Domain Controller's Private IP to static: </h3>

**We want the Client-1 machine to join the Domain, so we don't want the IP to change**

  
• Once the VM has been deployed, proceed to the VM overview page and select "Networking" > network settings on the left side.

•	Select Network Interface Card > IP configurations > ipconfig1 and set Private IP addess allocation to static.


</p>

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

<h3>Step 6: Login to DC-1 and configure the firewall settings </h3>

**We're going to configure the firewall settings inside our Domain Controller virtual machine**


•	Find DC-1's public IP address

•	From your personal computer, remote desktop into DC-1

•	Enter user name and password you created for DC-1

•	Right click the start menu and click Run

•	Type in wf.msc

•	This will open Windows Defender Firewall with Advanced Security

•	Disable the Firewall settings by going to "Windows Defender Firewall Properties"

•	Turn the Domain Profile firewall off

•	Turn the Private Profile firewall off

•	Turn the Public Profile firewall off

•	You should be left with these settings











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
<img width="426" height="462" alt="Screenshot 2026-01-04 190534" src="https://github.com/user-attachments/assets/07fc01d9-47b5-4c2b-aad4-483cd42bcaeb" />

</p>
<p>

<p>
<img width="432" height="469" alt="Screenshot 2026-01-04 190545" src="https://github.com/user-attachments/assets/88135c16-a3c4-4931-b20e-a05f14a3872b" />

</p>

<p>
<img width="444" height="601" alt="Screenshot 2026-01-04 190618" src="https://github.com/user-attachments/assets/20a0714a-a8af-4cd5-9309-8650159e4552" />

</p>
<p>
  
<h3>Step 7: Login to Client-1 and ping the Domain Controller (DC-1) </h3>
  
•	Login to Client-1

•	Look up Powershell in the search bar

•	Ping the Domain controller's private IP address (10.0.0.4)

</p>
<br />

<p>
<img width="1525" height="630" alt="Screenshot 2026-01-04 191027" src="https://github.com/user-attachments/assets/2d4de608-30f9-4c6a-b190-4d1aed8d21c5" />

</p>
<p>

 <p>
<img width="952" height="853" alt="Screenshot 2026-01-04 191118" src="https://github.com/user-attachments/assets/6c348323-02a5-456f-aa90-4636b47cab6e" />

</p>
<p>

 <p>
<img width="425" height="264" alt="Screenshot 2026-01-04 191209" src="https://github.com/user-attachments/assets/b396d5c9-f5f0-47de-8fe7-aa66f15d66a8" />

</p>
<p>

<p>
<img width="477" height="413" alt="Screenshot 2026-01-04 191246" src="https://github.com/user-attachments/assets/5a45f875-a14c-4a6f-92b7-34e9619ed4fc" />

</p>
<p>

<p>
<img width="1130" height="839" alt="Screenshot 2026-01-04 191441" src="https://github.com/user-attachments/assets/546a4f6a-7e78-4e24-8d15-e96059a3e523" />

</p>
<p>

 <p>
<img width="836" height="685" alt="Screenshot 2026-01-04 191527" src="https://github.com/user-attachments/assets/a07fc4a6-3d22-4b5c-aab0-51188197703f" />

</p>
<p> 

<p>
<img width="956" height="728" alt="Screenshot 2026-01-04 191540" src="https://github.com/user-attachments/assets/eaa772e1-2b0f-45fb-8d4f-f984135db416" />

</p>
<p>

 <p>
<img width="957" height="422" alt="Screenshot 2026-01-04 191700" src="https://github.com/user-attachments/assets/ba11929e-0a6b-44a6-afdf-c3259c21fd15" />

</p>
<p>

<p>
<img width="868" height="595" alt="Screenshot 2026-01-04 191711" src="https://github.com/user-attachments/assets/d1a0047c-b64e-4d87-ba53-53087ccb53f8" />

</p>
<p>

<p>

<h3>Step 5: Verify DNS Server: </h3>  
The output for the DNS settings should show DC-1's private IP address

-In Powershell, type in ipconfig /all
-You should see the DNS servers IP should be set to 10.0.0.4 (DC-1's private IP address)
</p>
<br />

<p>
<img width="825" height="594" alt="Screenshot 2026-01-04 191817" src="https://github.com/user-attachments/assets/89560c08-821d-4228-9450-ba97ea63a35f" />

</p>
<p>

 <p>
<img width="1036" height="871" alt="Screenshot 2026-01-04 191839" src="https://github.com/user-attachments/assets/42b88727-f856-46d3-b1c4-2f264ac1316f" />

</p>
<p> 

Deploying Active Directory Domain Services (AD DS) in Azure involves first preparing the foundational infrastructure. You begin by creating an Azure Virtual Network (VNet) with appropriate IP address ranges and subnets to host your domain controllers. Then, deploy one or more Windows Server virtual machines within this VNet. These VMs will serve as your domain controllers, and each should be assigned a static private IP address to ensure reliable DNS and replication behavior.
</p>
<br />


