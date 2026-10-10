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

The Virtual Machines used two seporate virtual network adapters. I used the default switch that utilizes NAT to access my host machine network for installing and updating Windows Server 2025 and Windows 11 Pro. I used a private virtual switch for the Domain Controller to communicate with other Virtual Machines because the default network adapter would change the subnet or gateway after networking changes or reboots.
<img width="895" height="851" alt="Screenshot 2026-10-10 021034" src="https://github.com/user-attachments/assets/5d1c77a8-8c32-458d-a772-755f128fe0b5" />

After using the default switch to install and update Windows Server 2025 I configured the Virtual Machine to only use the private virtual switch 

<img width="900" height="855" alt="Screenshot 2026-10-10 022000" src="https://github.com/user-attachments/assets/cb2ad4b2-32c2-449a-845c-5f1d94b5434e" />


