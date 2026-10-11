# Active-Directory-Lab
<h2>Description:</h2>
This project is a walkthrough of how I set up an Active Directory Home Lab using Hyper-V. I set up a Windows Server to run Active Directory, configured a Domain Controller to run a domain and added 2 users.

<h2>Languages & Utilities Used:</h2>

- Active Directory
- PowerShell

<h2>Software Used:</h2>

- Hyper-V
- Windows Server 2025
- Windows Pro Workstation

<h2>Walkthrough:</h2>

I used two different virtual network adapters on the Virtual Machines. The default switch that utilizes NAT to access my host machine's network was used to install and update Windows Server 2025 and Windows 11 Pro.
<img width="898" height="857" alt="image" src="https://github.com/user-attachments/assets/ac2ecbbc-ba61-4f2a-b977-c0a344fcba40" />
<img width="900" height="856" alt="image" src="https://github.com/user-attachments/assets/97cddbda-afea-4386-8d85-6cd33fe644bc" />

Using Server Manager I installed Active Directory Domain Services with the Add Roles and Features Wizard. I then added a new forest and domain and named it "lab.local" as well as configured the server as a domain controller with the Active Directory Domain Services Configuration Wizard.
<img width="1886" height="826" alt="image" src="https://github.com/user-attachments/assets/9352efdf-39be-4e0f-a5a3-d6573645a392" />
<img width="1891" height="831" alt="image" src="https://github.com/user-attachments/assets/3ac7e071-7647-435b-bf80-7e0b1b9d3eb7" />



A private virtual switch was necessary for the Domain Controller to communicate with other Virtual Machines because the default network adapter would change the subnet or gateway after reboots.
<img width="895" height="851" alt="image" src="https://github.com/user-attachments/assets/5d1c77a8-8c32-458d-a772-755f128fe0b5" />
<img width="900" height="855" alt="image" src="https://github.com/user-attachments/assets/cb2ad4b2-32c2-449a-845c-5f1d94b5434e" />

