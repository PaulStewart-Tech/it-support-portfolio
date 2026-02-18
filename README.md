# 🖥 Active Directory Home Lab – IT Support Portfolio

This repository documents my hands-on Active Directory home lab built to simulate a real-world enterprise IT environment.

The lab focuses on Level 1 / Level 2 IT Support competencies including identity management, domain administration, and troubleshooting.

---

## 📌 Overview

This lab demonstrates:

- User provisioning and lifecycle management  
- Security group design using the AGDLP model  
- Password resets and account unlocks  
- Domain joins and authentication validation  
- DNS troubleshooting  
- Group Policy configuration  
- Basic PowerShell administration  

---

## 🏗 Lab Environment Architecture

### Domain Information

- **Domain Name:** `lab.local`  
- **Domain Controller:** `DC01`  
- **Client Machine:** `CLIENT01`  
- **Server OS:** Windows Server 2022 (Evaluation)  
- **Client OS:** Windows 10/11  
- **Virtualization Platform:** VirtualBox  
- **Network Type:** Internal Network  

---

### IP Configuration

| Machine   | Role               | IP Address     | DNS             |
|-----------|-------------------|---------------|-----------------|
| DC01      | Domain Controller | 192.168.10.10 | 192.168.10.10   |
| CLIENT01  | Domain Client     | 192.168.10.x  | 192.168.10.10   |

> The Domain Controller uses a static IP and acts as the DNS server to ensure proper authentication within the domain.

---

## 🔧 Core Skills Demonstrated

### Active Directory Administration

- Created Organizational Units (OUs)
- Created and managed users
- Disabled and re-enabled accounts
- Forced password change at next logon
- Reset passwords
- Unlocked locked accounts
- Moved users between OUs

---

### Security Group Strategy (AGDLP)


