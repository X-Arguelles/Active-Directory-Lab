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

I started by creating a virtual machine using Hyper-V with its own virtual disk, installing Windows Server 2025 from an ISO file, updating the OS and named the virtual machine "DC1". I used two different virtual network adapters on this virtual machine. One connected to an external virtual switch ("External-Switch") that utilizes NAT to access my host machine's network, and the other one to a private virtual switch ("AD-Static-Switch") for the Domain Controller to communicate with other virtual machines.

<img width="875" height="485" alt="image" src="https://github.com/user-attachments/assets/aa361632-14b7-4c8f-b099-0ea76bf2fce2" />
<img width="300" height="442" alt="image" src="https://github.com/user-attachments/assets/ff379d92-c3ec-44fb-9078-83e9da2e72bd" />


Using Server Manager I installed Active Directory Domain Services with the Add Roles and Features Wizard. I promoted the server to a domain controller using the Active Directory Domain Services Configuration Wizard then added a new forest and domain named "lab.local".

https://github.com/user-attachments/assets/c064db24-9bf1-4ac9-b480-6ad55b160802

https://github.com/user-attachments/assets/8cf801ce-05fc-49bb-bc71-62fddd9c2c77


After rebooting I congfigured the private virtual switch ("AD-Static-Switch") on the domain controller to have a static IPv4 address (192.168.100.1), set the subnet mask to 255.255.255.0, and used the loopback address 127.0.0.1 as the DNS server.

<img width="727" height="532" alt="image" src="https://github.com/user-attachments/assets/7b8c9487-7b37-48de-ae1e-f46b21b1f61a" />


I added 2 User Objects ("John Smith" & "Jane Doe") and 2 group objects ("IT DEPT" & "HR DEPT").

<img width="544" height="272" alt="image" src="https://github.com/user-attachments/assets/aab95757-e3e8-420b-a7f8-6e700790ac23" />
<img width="544" height="278" alt="image" src="https://github.com/user-attachments/assets/c5a470c5-dc36-43c9-b71d-bf8f1d0dba16" />
<img width="542" height="403" alt="image" src="https://github.com/user-attachments/assets/e94ebea3-73ef-4250-a738-beedcbdd0e0f" />
<img width="541" height="407" alt="image" src="https://github.com/user-attachments/assets/12aa29d7-9337-4080-aa18-01bf5935e114" />


I added user "John Smith" to the "IT DEPT" group and user "Jane Doe" to the "HR DEPT" group.

<img width="497" height="229" alt="image" src="https://github.com/user-attachments/assets/0e169435-dce7-49d0-8da1-6c14b623fd7a" />
<img width="496" height="225" alt="image" src="https://github.com/user-attachments/assets/6ce1d309-b3fa-41d7-a020-fbe3d7d438e5" />


I started up two new virtual machine I installed Windows 11 Pro Workstation with only one network adapter connected to an external virtual switch to update the OS on both, and named them "PC1" for user "John Smith" & "PC2" for user "Jane Doe".

<img width="876" height="490" alt="image" src="https://github.com/user-attachments/assets/440f1280-c9ce-46cd-b7e0-55669921adf2" />
<img width="662" height="356" alt="image" src="https://github.com/user-attachments/assets/c26f2a73-240c-4fd4-bbc3-971e7b579e85" />


After updating the OS I disconnected the "External-Switch" and connected both VM's virtual network adapters on each VM to the "AD-Static-Switch", set a static IPv4 address for "PC1"(192.168.100.10) and one for "PC2" (192.168.100.11) set the DNS server address to the "lab.local" domain IP address (192.168.100.1) on both.

<img width="731" height="553" alt="image" src="https://github.com/user-attachments/assets/d66c228d-70ae-4913-90bc-f30ff684b008" />


I joined both users and computers to the Active Directory domain.

https://github.com/user-attachments/assets/2c5ad38c-b36a-4873-ba02-28f097619f1b

https://github.com/user-attachments/assets/e506b037-3e5c-4d55-9418-983ec31e7377

<img width="937" height="657" alt="Screenshot 2026-10-19 123928" src="https://github.com/user-attachments/assets/fbac3024-6288-40d6-8b00-68f3e20ae9bc" />


I created a new Group Policy Object in which I enabled Remote Desktop Services, enabled Network Level Authentication, created a new inbound rule to allow connections through port 3389 and applied the Group Policy settings using Powershell.

<img width="481" height="225" alt="image" src="https://github.com/user-attachments/assets/02deabb5-23b6-4673-9607-365b24b4556f" />

https://github.com/user-attachments/assets/7054ab99-5bf8-400c-811c-4d680f917095

https://github.com/user-attachments/assets/e0e1ec6b-50a6-4820-b85e-534bf51f3967

<img width="778" height="352" alt="Screenshot 2026-10-20 020559" src="https://github.com/user-attachments/assets/083b0a51-8ecf-4b07-a7fc-14f171f90e9a" />


Finally I checked that the GPO settings were applied and made sure that I could connect to PC1 and PC2 with the Administrator account.

<img width="940" height="645" alt="image" src="https://github.com/user-attachments/assets/d95ff590-73ed-40bc-8db2-999f06dd6b04" />
