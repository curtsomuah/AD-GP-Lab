# AD-GP-Lab
Active Directory/Group Policy Home Lab on Windows Servers 2022
Overview
This project demonstrates how I set up a Windows Server 2022 Active Directory environment in a home lab using UTM on macOS. It includes:
* Installing Windows Server from ISO
* Promoting the server to a domain controller
* Creating organizational units and users
* Applying Group Policy Objects (GPOs)
* Configuring Account Lockout Policy
* Enabling logon auditing and reviewing logs in Event Viewer

-Technologies Used:
* macOS + UTM (Virtualization)
* Windows Server 2022 ISO (Evaluation Edition)
* Active Directory Domain Services
* Group Policy Management Console (GPMC)
* Event Viewer

Lab Setup Steps
1. Install Windows Server 2022 ISO in UTM (macOS)
* Downloaded: SERVER_EVAL_x64FRE_en-us.iso from Microsoft Eval Center
* Created a new virtual machine using UTM with 2 CPUs, 4GB RAM, and 60GB storage
* Booted using the ISO and selected “Custom: Install Windows Only”
* Chose Windows Server 2022 Standard (Desktop Experience)

2. Create Initial Administrator Account
* Set an administrator password as prompted after installation
* Logged into the server using Ctrl + Alt + Delete (simulated using UTM key shortcut)

3. Configure the Domain Controller
* Renamed the computer
* Installed the Active Directory Domain Services (AD DS) role via Server Manager
* Promoted the server to a domain controller with:
    - Domain Name: home.lab1
    - Forest root domain
    - DNS & Global Catalog selected
    - Rebooted after promotion

4. Created Organizational Units and Users
Created OU structure:
home.lab1/
└── Departments
    └── IT
    └── HR
    └── Finance
    └── Interns
5. Applied Group Policy Objects (GPO)
* Configured a GPO at the domain level to enforce:
  * Account Lockout Policy:
    - Lockout threshold: 4 attempts
    - Duration: 30 minutes
  * Password Policy:
    - Enforce complexity
    - Minimum length: 8 characters
* Forced GPO update with gpupdate /force

6. Enabled Logon Auditing
* Edited GPO to enable:
    Computer Configuration → Policies → Windows Settings → Security Settings → Advanced Audit Policy Configuration → Logon/Logoff
* Audit Logon Events: Success and Failure
* Simulated failed logon attempt
* Verified event in Event Viewer under:
    Windows Logs → Security → Event ID 4625

7. Screenshots
<img width="799" alt="Screenshot 2025-05-14 at 11 14 00 PM" src="https://github.com/user-attachments/assets/afd32e39-9465-4b87-910a-b23b492935af" />
<img width="1019" alt="Screenshot 2025-05-15 at 4 33 17 PM" src="https://github.com/user-attachments/assets/bb034296-e1a4-4efb-842f-f48dd3fab8ff" />
<img width="1019" alt="Screenshot 2025-05-15 at 5 47 29 PM" src="https://github.com/user-attachments/assets/de54f653-0302-4feb-accf-79c7b167937b" />
<img width="877" alt="Screenshot 2025-05-15 at 10 42 14 PM" src="https://github.com/user-attachments/assets/55e1922c-bf51-44b9-b7bd-faa12e503f5e" />
<img width="847" alt="Screenshot 2025-05-16 at 1 43 16 AM" src="https://github.com/user-attachments/assets/06a9299a-9c63-4783-b01e-f42be7619d71" />
<img width="847" alt="Screenshot 2025-05-16 at 1 44 52 AM" src="https://github.com/user-attachments/assets/56a21ba7-4f15-49ec-beaf-7735949b5964" />
<img width="847" alt="Screenshot 2025-05-16 at 1 47 52 AM" src="https://github.com/user-attachments/assets/02b0d457-bebc-4a2b-a85b-7b0dd37d1301" />
<img width="847" alt="Screenshot 2025-05-16 at 1 50 12 AM" src="https://github.com/user-attachments/assets/16d01b0b-6027-4848-b43f-bbda7b77cd8a" />
<img width="847" alt="Screenshot 2025-05-16 at 2 06 48 AM" src="https://github.com/user-attachments/assets/813b1b68-b3c0-4857-bf02-8a2d4b743539" />

