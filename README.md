<div align="center">

# 🔐 Cybersecurity Lab Environment Setup

**Building an isolated virtual lab for penetration testing and ethical hacking practice**

</div>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2.6-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-Attacker_Machine-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
</p>

## 📌 Project Overview

This project focuses on designing and deploying a **virtual cybersecurity and penetration-testing laboratory** utilizing VirtualBox and Kali Linux. 

The primary purpose of this lab is to establish a secure, isolated, and controlled environment. This allows for the safe execution of network reconnaissance, vulnerability assessments, and ethical hacking practices without risking external networks. 

By configuring this lab on a private NAT network, the foundation is set to seamlessly integrate additional vulnerable target machines in the future, providing a comprehensive sandbox for ongoing security testing.

## 🎯 Objectives

The main objectives achieved in this project include:

- Installing and setting up VirtualBox as the host hypervisor.
- Importing and configuring Kali Linux as the primary attacking machine.
- Creating a private **NAT Network** (`10.0.0.0/24`) for isolated lab communication.
- Configuring a static IP assignment for Kali Linux to maintain a consistent environment.
- Enabling seamless host-to-VM interaction (shared folders, clipboard, and drag/drop).
- Resolving network connectivity and DNS resolution issues within the VM.
- Capturing a clean baseline snapshot of the VM for safe state-recovery.

## 🛡️ Purpose of the Lab

This laboratory provides an isolated sandbox intended strictly for educational security research. It facilitates practical, hands-on experience in:

- Network reconnaissance and mapping
- Vulnerability scanning and assessment
- Packet analysis and traffic interception
- Exploitation practice in a legally compliant environment
- Testing open-source cybersecurity tools

⚠️ **Important:** This laboratory is intended for authorized security testing only. Tools and techniques practiced here must never be deployed against unauthorized external systems or networks.

## ⚙️ Lab Configuration

| 🧩 Component         | ⚙️ Configuration  |
| -------------------- | ----------------- |
| 🖥️ Host OS          | Windows 11        |
| 🧠 Host RAM         | 24 GB             |
| ⚡ Processor         | Intel Core i7-13650HX |
| 🧰 Hypervisor       | VirtualBox 7.2.6  |
| 🐉 Security OS      | Kali Linux 2026.2 |
| 🌐 Virtual Network  | NAT Network       |
| 📡 Network Address  | 10.0.0.0/24       |
| 🐧 Kali IP Address  | 10.0.0.2/24       |
| 🌍 Connectivity     | Full Internet Access |

# 🪜 Lab Setup Procedure

## Step 1. Install 7-Zip

To ensure seamless extraction of compressed virtual machine images and deployment packages, 7-Zip was installed on the host machine. 

<img width="833" height="920" alt="1 - 7-zip Install" src="https://github.com/user-attachments/assets/24e19c35-7a7b-4bde-a710-cb12edfa853f" />

---

## Step 2. Install VirtualBox

VirtualBox (v7.2.6) was downloaded from the official repository and installed as the foundational hypervisor to manage our virtualized environment.

<img width="1097" height="790" alt="2 - Installed and set up VirtualBox" src="https://github.com/user-attachments/assets/3e53ed22-182f-45b6-b94e-92c187ae6652" />

---

## Step 3. Create the NAT Network

A dedicated NAT Network was created within VirtualBox. A **NAT Network** was deliberately chosen because it allows multiple virtual machines within the same subnet to communicate with each other while still retaining outbound internet access through the host machine.

**Configuration Parameters:**
- **Network Name:** NatNetwork
- **IPv4 Prefix:**  10.0.0.0/24
- **DHCP:**         Enabled
- **IPv6:**         Disabled

<img width="1097" height="790" alt="3 - VB NAT Network Configuration" src="https://github.com/user-attachments/assets/0799d525-cbea-4505-b110-5f15ce0f5daf" />

---

## Step 4. Import & Configure Kali Linux

The pre-built Kali Linux virtual machine was downloaded from the official Offensive Security repository and imported into VirtualBox to serve as the primary attacker machine.

Several crucial VM settings were adjusted to optimize workflow and lab connectivity:
1. **Network Adapter:** Attached to the previously created `NatNetwork` to ensure it falls within the `10.0.0.0/24` subnet.
2. **Quality of Life features:** Bidirectional clipboard and file drag-and-drop were enabled in the Virtual Machine settings.
3. **Shared Folders:** Enabled and linked to the host's `/downloads` folder to allow easy file transfers between the Windows 11 host and the Linux VM.

<img width="1097" height="790" alt="4 - Imported Kali Linux" src="https://github.com/user-attachments/assets/14db6bf5-df0b-42d9-ae6a-40d9fed1efe4" />

<img width="781" height="518" alt="4a - Updated Kali Linux NAT Setup " src="https://github.com/user-attachments/assets/2ec77785-50b1-469f-bb2e-148224bf2098" />

---

## Step 5. Configure the Kali Linux Network

To ensure the attacking machine is easily identifiable and consistent for future lab scenarios, a static IPv4 address was configured within Kali Linux.

**Static IP Configuration:**
- **IP Address:** 10.0.0.2
- **Subnet Mask:** 24 (255.255.255.0)
- **Gateway:** 10.0.0.1
- **DNS Servers:** 8.8.8.8

<img width="1380" height="864" alt="5 - Kali Linux IP Configuration Setup" src="https://github.com/user-attachments/assets/1d61cbc3-e300-4c71-bf62-628787ec9c8f" />

The configuration was then verified via the terminal using the `ifconfig` command to confirm the interface registered the correct IP.

<img width="1380" height="864" alt="5a - Checking IP Configuration" src="https://github.com/user-attachments/assets/37d9d2de-f822-4675-a9be-dbae75afdf3f" />

---

## Step 6. Create a Clean VM Snapshot

Once the system was fully configured, updated, and networked correctly, a VirtualBox snapshot was captured.

This snapshot acts as a baseline. In the event that a future penetration test, misconfiguration, or system failure breaks the operating system, the VM can be instantly restored to this known-good state.

<img width="1920" height="1032" alt="6 - Snapshot Set Up" src="https://github.com/user-attachments/assets/f4556314-c3ca-4c6e-a925-28ec0787a8f2" />

# 🐞 Problems Encountered & Solutions

## Network Connection Hanging on Static IP

**Issue:** 
After changing the IPv4 settings in Kali Linux to the required static IP (`10.0.0.2`), the network failed to establish a connection. The interface struggled to initialize outbound traffic despite the correct gateway and DNS configurations.

**Solution:**
The issue was rooted in Duplicate Address Detection (DAD) timing out within the NetworkManager. To resolve this, I applied a specific configuration modifier via the command line to bypass the DAD timeout on the primary wired interface:

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
```

# 💡 What I Learned

Building this lab provided practical exposure to core virtualization and networking principles required for cybersecurity:

### 1. Network Address Translation (NAT) Environments
I learned the functional distinction between standard NAT (which isolates a VM completely) and a NAT Network (which creates a localized subnet allowing internal VM-to-VM communication alongside external web access). This is a foundational concept for building target-rich penetration testing labs.

### 2. Static IP Management in Linux
By manually configuring the IP addressing, I gained experience using Linux NetworkManager GUI and CLI tools (like `nmcli` and `ifconfig`) to enforce static IP rules, ensuring the attacking machine remains at a predictable address (`10.0.0.2`).

### 3. Hypervisor Workflow Optimization
Setting up bidirectional clipboards, shared folders, and proper resource allocation taught me how to bridge the gap between a host OS and a security VM efficiently without compromising the isolation of the lab environment.

### 4. Baseline State Management (Snapshots)
Taking a snapshot immediately following a successful configuration reinforced the best practice of establishing a "clean slate." Security testing often involves risky commands or malware handling; having a snapshot guarantees rapid recovery.

# 🔗 Tools & Resources

- **7-Zip:** [https://7-zip.org/download.html](https://7-zip.org/download.html)
- **VirtualBox:** [https://virtualbox.org/wiki/Downloads](https://virtualbox.org/wiki/Downloads)
- **Kali Linux:** [https://kali.org/get-kali](https://kali.org/get-kali)
- **OBS Studio:** [https://obsproject.com/](https://obsproject.com/)

# 👤 Author

**Ali Abbas Qazi**\
Cybersecurity Student

LinkedIn: [https://www.linkedin.com/in/ali-abbas-qazi/](https://www.linkedin.com/in/ali-abbas-qazi/)\
GitHub: [https://github.com/Ali-Abbas-Qazi](https://github.com/Ali-Abbas-Qazi)

<br>

<div align="center">
  <a href="[https://www.linkedin.com/in/ali-abbas-qazi/](https://www.linkedin.com/in/ali-abbas-qazi/)">
    <img src="[https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)" alt="LinkedIn" />
  </a>
  <a href="[https://github.com/Ali-Abbas-Qazi](https://github.com/Ali-Abbas-Qazi)">
    <img src="[https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)" alt="GitHub" />
  </a>
</div>

## 📌 Project Information

**Program:** Cybersecurity | **Project:** Cybersecurity & Pentesting Lab Setup
