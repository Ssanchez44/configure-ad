
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

- Provisioning Azure Virtual Machines
- Installing Active Directory Domain Services
- Configuring Network and Security Settings
- Join Domain and Manage Users

<h2>Deployment and Configuration Steps</h2>

<p>

![image](https://github.com/user-attachments/assets/f20a86e0-7ba9-4d03-8f16-c2eedab13466)

</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>

![image](https://github.com/user-attachments/assets/02595d2a-6bb2-4431-8553-82813903be16)

![image](https://github.com/user-attachments/assets/68c0e116-c67f-4c55-9ba9-9e594c412953)

![image](https://github.com/user-attachments/assets/f0ea6525-d092-44cd-8f71-b28dd23ed789)

![image](https://github.com/user-attachments/assets/ca99cb24-7ac4-4db1-b5f1-8c6594797778)

![image](https://github.com/user-attachments/assets/ab318bfc-4d6d-4c87-8669-94db7c0b1298)

![image](https://github.com/user-attachments/assets/122854e0-7582-4c2c-9d1d-97ff2b687810)



</p>
<p>

Step 1: Set Static IP on DC-1 (Domain Controller)
Navigate to DC-1 Settings:

In the Azure Portal, go to Virtual Machines and select DC-1.
Configure Static IP for DC-1:

Under Settings, go to Networking.
Under the Network Interface section, click on IP configurations.
Select the IP configuration (typically named ipconfig1).
In the Private IP address settings, click on the IP Assignment drop-down.
Change the setting from Dynamic to Static.
Click Save to apply the changes.
By setting the private IP to static, the IP address of DC-1 will remain the same, ensuring consistent communication for DNS and domain services.

Disable Firewall on DC-1

In the DC-1 settings, go to Networking and ensure there are no restrictions on inbound traffic, specifically allowing RDP, DNS, and any other necessary services.
Additionally, disable the Windows Firewall or adjust the firewall rules if necessary to allow communication for domain services.
To disable the firewall in DC-1, you can use the following command on the VM:
bash
Copy
netsh advfirewall set allprofiles state off
Step 2: Configure DNS on Client-1
Navigate to Client-1 Settings:

In the Azure Portal, go to Virtual Machines and select Client-1.
Configure DNS Settings for Client-1:

Under Settings, go to Networking.
Under the Network Interface section, click on IP configurations.
Select the IP configuration (typically named ipconfig1).
In the DNS servers section, choose Custom.
Enter the static private IP address of DC-1 as the DNS server address (for example, 10.0.0.4).
Click Save to apply the DNS settings.
This ensures that Client-1 uses DC-1 for DNS resolution, which is necessary for domain joining.

Step 3: Join Client-1 to the Domain
Log in to Client-1:

Log into Client-1 either through RDP or directly via the Azure Portal.
Join Client-1 to the Domain:

Open the System Properties by right-clicking This PC and selecting Properties, then click on Change settings under the "Computer name, domain, and workgroup settings" section.
Click on Change to rename this PC or join a domain.
Select the option Domain and enter the domain name.
When prompted, enter the domain administrator credentials for DC-1.
Restart the machine when prompted to complete the domain join process.
Step 4: Verify the Domain Join on Client-1
Check Domain Join:

After restarting, log into Client-1 using the domain credentials.
Verify that Client-1 has successfully joined the domain by checking the System Properties.
Test Connectivity and DNS Resolution:

Open powershall on Client-1 and run:
bash
Copy
nslookup dc-1
This should resolve to the IP address of DC-1, confirming that DNS is functioning properly.
</p>
<br />

<p>
