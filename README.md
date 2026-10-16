# Active-Directory-Lab
<h2>Description:</h2>
This project is a walkthrough of how I set up an Active Directory Home Lab using Hyper-V. I set up a Windows Server to run Active Directory, configured a Domain Controller to run a domain and added 2 users.

<h2>Utilities Used:</h2>

- Active Directory

<h2>Software Used:</h2>

- Hyper-V
- Windows Server 2025
- Windows Pro Workstation
  
<h2>Walkthrough:</h2>

I started by creating a virtual machine using Hyper-V with its own virtual disk, installing Windows Server 2025 from an ISO file, updating the OS using an external virtual switch attached to one of the two virtual network adapter and named the virtual machine "DC1".

<img width="875" height="485" alt="image" src="https://github.com/user-attachments/assets/aa361632-14b7-4c8f-b099-0ea76bf2fce2" />



I used two different virtual network adapters on this virtual machines. One with an external virtual switch ("External-Switch") that utilizes NAT to access my host machine's network, and the other one with a private virtual switch ("AD-Static-Switch") for the Domain Controller to communicate with other virtual machines.

<img width="300" height="442" alt="image" src="https://github.com/user-attachments/assets/ff379d92-c3ec-44fb-9078-83e9da2e72bd" />





Using Server Manager I installed Active Directory Domain Services with the Add Roles and Features Wizard. I promoted the server to a domain controller using the Active Directory Domain Services Configuration Wizard then added a new forest and domain named "lab.local".

https://github.com/user-attachments/assets/c064db24-9bf1-4ac9-b480-6ad55b160802

https://github.com/user-attachments/assets/8cf801ce-05fc-49bb-bc71-62fddd9c2c77



After rebooting I congfigured the private virtual switch (AD-Static-Switch) on the domain controller to have a static IPv4 address (192.168.1.100), set the subnet mask to 255.255.255.0, and used the loopback address 127.0.0.1 as the DNS server.

<img width="1727" height="836" alt="image" src="https://github.com/user-attachments/assets/910a42e1-85e2-47af-9d9d-5aa6fc8b55b7" />



I added 2 User Objects ("John Smith" & "Jane Doe") and 2 group objects ("IT DEPT" & "HR DEPT").

<img width="544" height="272" alt="image" src="https://github.com/user-attachments/assets/aab95757-e3e8-420b-a7f8-6e700790ac23" />
<img width="544" height="278" alt="image" src="https://github.com/user-attachments/assets/c5a470c5-dc36-43c9-b71d-bf8f1d0dba16" />
<img width="542" height="403" alt="image" src="https://github.com/user-attachments/assets/e94ebea3-73ef-4250-a738-beedcbdd0e0f" />
<img width="541" height="407" alt="image" src="https://github.com/user-attachments/assets/12aa29d7-9337-4080-aa18-01bf5935e114" />



I added user "John Smith" to the "IT DEPT" group and user "Jane Doe" to the "HR DEPT" group.

<img width="497" height="229" alt="image" src="https://github.com/user-attachments/assets/0e169435-dce7-49d0-8da1-6c14b623fd7a" />
<img width="496" height="225" alt="image" src="https://github.com/user-attachments/assets/6ce1d309-b3fa-41d7-a020-fbe3d7d438e5" />





On a separate virtual machine I installed and updated Windows 11 Pro Workstation and named it "PC01".

<img width="876" height="490" alt="image" src="https://github.com/user-attachments/assets/440f1280-c9ce-46cd-b7e0-55669921adf2" />


