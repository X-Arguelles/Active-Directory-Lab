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

I started by creating a virtual machine using Hyper-V with its own virtual disk, installing and updating Windows Server 2025 from an ISO file and named it "DC1".
<img width="877" height="662" alt="image" src="https://github.com/user-attachments/assets/0569a67b-e854-4a0b-a8b5-a723e256781b" />
<img width="427" height="477" alt="image" src="https://github.com/user-attachments/assets/1264fae6-6dc8-494b-aaf3-85d8f2222642" />



I used two different virtual network adapters on the virtual machines. The default switch on Hyper-V that utilizes NAT to access my host machine's network was used to install and update Windows Server 2025. A private virtual switch, that I named "AD-Static-Switch", was necessary for the Domain Controller to communicate with other Virtual Machines because the default network adapter would change the subnet or gateway after reboots.
<img width="898" height="857" alt="image" src="https://github.com/user-attachments/assets/ac2ecbbc-ba61-4f2a-b977-c0a344fcba40" />
<img width="897" height="848" alt="Screenshot 2026-10-12 231626" src="https://github.com/user-attachments/assets/dee9b379-3678-40f4-9778-c7d6f0ec87b1" />

Using Server Manager I installed Active Directory Domain Services with the Add Roles and Features Wizard. I then added a new forest and domain and named it "lab.local" as well as configured the server as a domain controller with the Active Directory Domain Services Configuration Wizard.
<img width="1886" height="826" alt="image" src="https://github.com/user-attachments/assets/9352efdf-39be-4e0f-a5a3-d6573645a392" />
<img width="1891" height="831" alt="image" src="https://github.com/user-attachments/assets/3ac7e071-7647-435b-bf80-7e0b1b9d3eb7" />

I assigned a static IPv4 address to the domain controller (192.168.0.100), set the subnet mask to 255.255.255.0, used the loopback address 127.0.0.1 as the DNS server, and renamed the PC to "DC01".
<img width="1826" height="837" alt="image" src="https://github.com/user-attachments/assets/caf2c120-5aaa-4868-9708-31c7bfa566af" />
<img width="796" height="327" alt="image" src="https://github.com/user-attachments/assets/3fb011f0-7f8e-43ff-8e82-31f8d58032d6" />

On a separate virtual machine I used the default switch to install and update Windows 11 Pro Workstation and named it "PC01".


