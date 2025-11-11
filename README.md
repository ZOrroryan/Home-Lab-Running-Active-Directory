# Home-Lab-Running-Active-Directory (VirtualBox)

This project demonstrates the deployment and configuration of a fully functional **Active Directory environment** on a personal computer using **Oracle VirtualBox**. The lab simulates a small Windows network environment with a **Domain Controller (Server 2019)** and a **Windows 10 client**, covering domain services, DHCP, NAT, and user management automation via PowerShell.

---

## 🔧 Project Overview

This lab was designed to help develop practical experience with **Active Directory**, **Windows Server administration**, and **Windows networking** fundamentals. It replicates a simplified enterprise setup where users can log into multiple systems under one centralized domain.

### Environment Components
- **Virtualization Platform:** Oracle VirtualBox  
- **Operating Systems:**  
  - Windows Server 2019 (Domain Controller)  
  - Windows 10 Pro (Client)
- **Networking Setup:**  
  - Adapter 1: NAT (Internet access)  
  - Adapter 2: Internal Network (Private LAN for domain communication)

---

## 🧩 Configuration Steps

### 1. Virtual Machine Setup 
- Installed **Oracle VirtualBox** and the **Extension Pack**.
- Created two VMs:
  - **Domain Controller (DC)**
  - **Windows 10 Client**
- Assigned two network adapters to the DC:
  - **NAT** for external internet access.
  - **Internal Network** for private connectivity.

#### 📸 Visual Reference
Below are screenshots of the **VirtualBox environment** showing both virtual machines prior to startup — serving as a visual reference for the lab setup.

<p align="center">
  <img src="vbox_vm_list.png" alt="VirtualBox VM List" width="600"/>
</p>

> *Screenshot:* The VirtualBox Manager displaying the two configured VMs (Server 2019 and Windows 10 Client) before being powered on.

### 2. Windows Server 2019 Configuration
- Installed **Server 2019** on the Domain Controller VM.
- Installed **VirtualBox Guest Additions** for better performance and display scaling.
- Configured **static IP addressing**:
  - Internal NIC: `172.16.0.1`
  - Subnet Mask: `255.255.255.0`
  - DNS: `127.0.0.1` (loopback)

#### 📸 Visual Reference
Below is a screenshot of the **network configuration** inside the Domain Controller VM, showing the static IP setup used for the internal network.

<p align="center">
  <img src="Internalnetworksetup.jpg" alt="Windows Server 2019 Network Configuration" width="600"/>
</p>

> *Screenshot:* The Windows Server 2019 network configuration displaying the static IP settings for the internal NIC.

### 3. Active Directory Setup
- Installed the **Active Directory Domain Services (AD DS)** role.
- Created a new forest and domain: `OmarDomain.com`.
- Created a dedicated **Domain Admin account** under an OU named `MyAdmins`.
- Granted the account **Domain Admin** privileges.

#### 📸 Visual Reference
Below is a screenshot taken during the **Active Directory setup process**, showing where the domain name was specified while creating the new forest.

<p align="center">
  <img src="Activedirectorydomaincreation.jpg" alt="Active Directory Domain Naming Setup" width="600"/>
</p>

> *Screenshot:* The domain naming screen during the Active Directory setup for `OmarDomain.com`.

### 4. Network Services
- Installed and configured **Routing and Remote Access Service (RRAS)** with **NAT** to allow clients on the internal network to reach the internet via the DC.
- Installed **DHCP Server** and created a scope:
  - IP Range: `172.16.0.100 – 172.16.0.200`
  - Default Gateway: `172.16.0.1`
  - DNS Server: `172.16.0.1`
- Authorized the DHCP server and activated the scope.

### 5. PowerShell Automation
Created and executed a **PowerShell script** that automatically generated 1,000 Active Directory users.

#### Script Summary
- Reads names from an external `.txt` file.
- Creates an `_Users` OU in Active Directory.
- Adds users with a default password (`Password1`).
- Ensures consistency and simulates a realistic enterprise directory.

### 6. Windows 10 Client Setup
- Installed **Windows 10 Pro** on the second VM.
- Connected the VM to the **Internal Network**.
- Verified automatic IP assignment from DHCP.
- Confirmed network connectivity and internet access via NAT.
- Joined the Windows 10 machine to the `mydomain.com` domain.
- Logged into the system using a domain user account to verify domain authentication.

---

## 🧠 Key Skills Demonstrated
- Active Directory installation and configuration  
- Windows Server administration  
- DHCP and DNS setup  
- Network Address Translation (NAT) with RRAS  
- PowerShell scripting for automation  
- Domain join and authentication troubleshooting  
- Virtual networking and VM management

---

## 🧰 Tools & Technologies
- **Oracle VirtualBox**
- **Windows Server 2019**
- **Windows 10 Pro**
- **Active Directory Domain Services**
- **Routing and Remote Access (RRAS)**
- **DHCP Server**
- **PowerShell**

---

## 📈 Outcomes
By completing this project:
- Gained hands-on experience managing a Windows domain environment.
- Automated Active Directory user creation via PowerShell scripting.
- Built a realistic, scalable home lab environment suitable for practicing enterprise networking and administration concepts.

---

## 📸 Future Enhancements
- Add **Group Policy Objects (GPOs)** for centralized management.
- Configure **File Sharing and Permissions** across domain users.
- Integrate **Windows Server Update Services (WSUS)** or **Sysmon logging** for further enterprise simulation.
- Extend lab with **SIEM integration (Splunk, Sentinel, etc.)** for security monitoring.

---

## 🪪 Author
**Omar — Cybersecurity Analyst | CompTIA CySA+ | Splunk Certified**

---

