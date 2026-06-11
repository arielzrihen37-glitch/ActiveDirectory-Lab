# ActiveDirectory-Lab
i did a lab on Active Directory (Entra-ID) and also ticketing system and learned to use it for a better employment and so being to find a work in IT to help people and resolve problems everyday.

# 🖥️ Active Directory Home Lab: Domain Join, RDP Access, and PowerShell Bulk User Creation

## 📌 Project Title 
**Active Directory Implementation on Windows Server 2022**  
*Hands-on lab simulating a small business domain environment*

## 📄 Project Summary 

### Brief Description
This project is a **step‑by‑step walkthrough** of setting up a fully functional Active Directory domain from scratch. It demonstrates:
- Installing Active Directory Domain Services (AD DS) on a Windows Server 2022 VM (DC-1)
- Creating domain admin and standard user accounts
- Joining a Windows 10/11 client (client-1) to the domain
- Configuring Remote Desktop (RDP) access for non‑administrative users
- Generating 100+ random domain users using a PowerShell script

### Languages Used
- **PowerShell** (for bulk user creation and automation)

### Environments Used
- **Windows Server 2022** (Domain Controller)
- **Windows 10/11 Pro** (Client machine)
- On‑premises lab or **Azure Virtual Machines** (if you used cloud)

### Technologies/Applications/Services
- **Active Directory Domain Services (AD DS)**
- **DNS** (CNAME record testing)
- **Remote Desktop Protocol (RDP)**
- **Group Policy Management** (for RDP permissions)
- **PowerShell ISE** (scripting)

## 🖼️ Media – Images and/or Video (3 points)

> *Replace these placeholders with actual screenshots from your lab*

![Active Directory Users and Computers showing created users](screenshots/ad-users.png)
*Figure 1: Active Directory Users and Computers with bulk users*

![PowerShell script generating random users](screenshots/powershell-bulk-users.png)
*Figure 2: PowerShell script creating 150 domain users*

![RDP connection error and fix](screenshots/rdp-access-denied.png)
*Figure 3: Troubleshooting "account not authorized for remote login" error*

![Client-1 joined to domain](screenshots/domain-join-success.png)
*Figure 4: Client-1 successfully joined to the domain*


## 🧪 Demonstration (4 points)

### Step 1: Install Active Directory on DC-1
- Installed Windows Server 2022 VM
- Added AD DS role and promoted server to Domain Controller
- Created domain: `mylab.local`

### Step 2: Create Domain Admin Account
- In AD Users and Computers, created `admin-john`
- Added to `Domain Admins` and `Enterprise Admins` groups

### Step 3: Join Client-1 to the Domain
- Set client-1 DNS to DC-1's IP
- Used `System Properties > Change domain` to join `mylab.local`
- Restarted and verified domain join with `whoami` (showed `MYLAB\client-1$`)

### Step 4: Configure RDP for Non‑Admin Users
- On client-1, went to `System Properties > Remote`
- Added `Domain Users` group to "Remote Desktop Users"
- Tested login with standard user → got `error 0x3` (access denied)
- **Fix:** On DC-1, added the user to `Remote Desktop Users` group and modified Group Policy `Allow log on through Remote Desktop Services`
- Successfully logged in as `mylab\john.doe`

### Step 5: Bulk Create Random Users with PowerShell
- Ran the following script on DC-1 as Administrator:
```powershell
