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

I started by creating a virtual machine using Hyper-V with its own virtual disk, installing Windows Server 2025 from an ISO file, updating the OS using the Hyper-V default virtual switch as one of the virtual network adapter and named the virtual machine "DC1".
<img width="877" height="662" alt="image" src="https://github.com/user-attachments/assets/85bc2a84-659f-4d84-b936-03b37b6d9e83" />
<img width="427" height="238" alt="image" src="https://github.com/user-attachments/assets/66bc89ba-42c8-4a16-b99f-f23093e59160" />




I used two different virtual network adapters on the virtual machines. The default switch on Hyper-V that utilizes NAT to access my host machine's network, and a private virtual switch, that I named "AD-Static-Switch", was necessary for the Domain Controller to communicate with other virtual machines because the default network adapter would change the subnet or gateway after reboots.
<img width="898" height="857" alt="image" src="https://github.com/user-attachments/assets/ac2ecbbc-ba61-4f2a-b977-c0a344fcba40" />
<img width="901" height="857" alt="image" src="https://github.com/user-attachments/assets/f5a684f1-128d-4117-b9dc-7b6026a470e9" />

Using Server Manager I installed Active Directory Domain Services with the Add Roles and Features Wizard. I then promoted the server to a domain controller using the Active Directory Domain Services Configuration Wizard. Lastly I added a new forest and domain named "lab.local".

https://github.com/user-attachments/assets/c064db24-9bf1-4ac9-b480-6ad55b160802

https://github.com/user-attachments/assets/8cf801ce-05fc-49bb-bc71-62fddd9c2c77



After rebooting I assigned a static IPv4 address to the domain controller (192.168.0.100), set the subnet mask to 255.255.255.0, used the loopback address 127.0.0.1 as the DNS server, and renamed the PC to "DC01".
<img width="1826" height="837" alt="image" src="https://github.com/user-attachments/assets/caf2c120-5aaa-4868-9708-31c7bfa566af" />


On a separate virtual machine I used the default switch to install and update Windows 11 Pro Workstation and named it "PC01".


