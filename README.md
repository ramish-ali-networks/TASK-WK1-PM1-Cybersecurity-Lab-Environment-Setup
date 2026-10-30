# TASK-WK1-PM1-Cybersecurity-Lab-Environment-Setup
Building an isolated cybersecurity and ethical hacking lab using VirtualBox and Kali Linux with NAT Network, static IP configuration, shared folders, and internet connectivity.
# 🔐 TASK-WK1-PM1 | Cybersecurity Lab Environment Setup

<p align="center">
  <strong>Building an Isolated Cybersecurity & Ethical Hacking Lab</strong>
  <br>
  <em>VirtualBox • Kali Linux • NAT Networking • Linux Administration</em>
</p>

---

## 📌 Project Overview

This project focuses on building and configuring an isolated cybersecurity testing laboratory using Oracle VirtualBox and Kali Linux.

The main objective is to establish a controlled virtual environment for learning cybersecurity, ethical hacking, network reconnaissance, vulnerability assessment, and penetration-testing fundamentals.

The laboratory uses a custom NAT Network with the `10.0.0.0/24` subnet, allowing Kali Linux to communicate through a dedicated virtual network while maintaining internet connectivity.

This environment also provides a foundation for adding additional virtual machines for future authorized security-testing activities.

## 🎯 Project Objectives

- Install and configure 7-Zip.
- Install Oracle VirtualBox.
- Create a custom NAT Network using `10.0.0.0/24`.
- Download and import Kali Linux.
- Configure Kali Linux network settings.
- Assign a consistent IPv4 address to Kali Linux.
- Configure internet connectivity.
- Enable shared clipboard and drag-and-drop.
- Configure a shared folder between host and guest.
- Verify network connectivity and DNS resolution.
- Create a clean virtual machine snapshot.
- Prepare the environment for future cybersecurity practicals.

## 🏗️ Lab Architecture

The laboratory consists of a Windows host machine running Oracle VirtualBox, with Kali Linux operating as the primary cybersecurity testing machine.

### Network Architecture

```text
                 INTERNET
                    |
                    |
              WINDOWS 10
               HOST OS
                    |
                    |
             ORACLE VIRTUALBOX
                    |
                    |
               NAT NETWORK
              10.0.0.0/24
                    |
                    |
               KALI LINUX
              10.0.0.2/24
                    |
                    |
          CYBERSECURITY LAB
```

Additional Windows, Linux, and Android virtual machines can be connected to the same NAT Network in future practical exercises.

## ⚙️ Lab Configuration

| Component | Configuration |
|---|---|
| Host Operating System | Windows 10 |
| Virtualization Platform | Oracle VirtualBox |
| Security Operating System | Kali Linux |
| Virtual Network Type | NAT Network |
| Network Name | NatNetwork |
| Network Address | 10.0.0.0/24 |
| Kali Linux IP Address | 10.0.0.2/24 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 10.0.0.1 |
| Shared Folder | /downloads |
| Internet Connectivity | Enabled |
| Virtual Machine Snapshot | Clean Baseline |

**Note:** The gateway address `10.0.0.1` is used where required for connectivity troubleshooting.

## 🧰 Tools & Technologies

| Tool / Technology | Purpose |
|---|---|
| 7-Zip | Extracting virtual machine archives |
| Oracle VirtualBox | Virtualization platform |
| Kali Linux | Cybersecurity testing environment |
| NetworkManager | Linux network management |
| NMCLI | Command-line network configuration |
| NAT Network | Virtual network connectivity |
| IPv4 | Network addressing |

## 🪜 Lab Implementation

### PHASE 1: Environment Preparation

### Step 1 – Install 7-Zip

Installed 7-Zip to extract the Kali Linux virtual machine archive.

Download: https://7-zip.org/download.html

### Step 2 – Install Oracle VirtualBox

Installed Oracle VirtualBox as the primary virtualization platform for creating and managing virtual machines.

Download: https://virtualbox.org/wiki/Downloads

### Step 3 – Create a Custom NAT Network

Created a dedicated NAT Network in VirtualBox.

**Network Configuration:**

| Setting | Value |
|---|---|
| Network Name | NatNetwork |
| IPv4 Network | 10.0.0.0/24 |
| Network Type | NAT Network |
| IPv6 | Disabled |

A NAT Network allows multiple connected virtual machines to communicate with one another while providing outbound internet connectivity.

### Step 4 – Download and Import Kali Linux

Downloaded and imported the Kali Linux virtual machine into Oracle VirtualBox.

Official Download: https://kali.org/get-kali

**Virtual Machine Network Settings:**

- Attached to: NAT Network
- Network: NatNetwork
- Adapter Type: Intel PRO/1000 MT Desktop

### Step 5 – Configure Kali Linux Networking

Configured the Kali Linux network interface with a consistent IPv4 address.

**Network Configuration:**

| Setting | Value |
|---|---|
| Interface | eth0 |
| IP Address | 10.0.0.2 |
| Prefix Length | /24 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 10.0.0.1 |

A consistent IP address makes the virtual machine easier to identify and manage during future cybersecurity exercises.

### Step 6 – Configure Virtual Machine Integration

Configured VirtualBox integration settings to enable communication and file sharing between the host and guest operating systems.

**Configured Features:**

- Shared Clipboard: Enabled
- Drag and Drop: Enabled
- Shared Folder: /downloads

These settings support clipboard sharing and file exchange between Windows and Kali Linux.

### Step 7 – Create a Clean Virtual Machine Snapshot

Created a baseline snapshot after completing the initial Kali Linux configuration.

**Snapshot Name:**

`Clean Kali - Network Setup`

The snapshot provides a recovery point before performing future cybersecurity experiments.

## 🌐 Network Troubleshooting

### Problem: Kali Linux Internet Connectivity

During the laboratory configuration, internet connectivity issues were encountered with the Kali Linux network connection.

A workaround involved modifying the IPv4 Duplicate Address Detection timeout through NetworkManager.

### Solution: NMCLI Commands

**1. Modify IPv4 DAD Timeout**

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
```

**2. Deactivate the Network Connection**

```bash
sudo nmcli connection down "Wired connection 1"
```

**3. Reactivate the Network Connection**

```bash
sudo nmcli connection up "Wired connection 1"
```

These commands modify the connection settings and restart the network connection.

**Important:** The connection name may differ between systems. Identify the actual connection name before executing these commands.

## 🔎 Lab Verification

The following commands can be used to verify the laboratory configuration.

| Test | Command | Purpose |
|---|---|---|
| Check IP Address | `ip a` | Verify IPv4 configuration |
| Check Routing Table | `ip route` | Verify default gateway |
| Test Gateway | `ping 10.0.0.1` | Check gateway connectivity |
| Test Internet | `ping 8.8.8.8` | Check external connectivity |
| Test DNS | `nslookup networkwalks.com` | Verify DNS resolution |
| Check Network Interface | `nmcli device status` | Check interface status |
| Check Network Connection | `nmcli connection show` | Display configured connections |

## 📸 Project Screenshots

The following screenshots document the practical implementation of the laboratory.

### 01. Kali Linux Desktop

Shows the Kali Linux desktop environment and its network connection status.

![Kali Linux Desktop](screenshots/01-kali-desktop.png)

### 02. Virtual Network Connections

Shows the configured Ethernet network connection in Kali Linux.

![Network Connections](screenshots/02-network-connections.png)

### 03. Kali Linux Network Settings

Shows the Ethernet interface configuration and network adapter settings.

![Kali Linux Network Settings](screenshots/03-kali-network-settings.png)

### 04. Network Troubleshooting Commands

Shows the NMCLI commands used to modify and restart the network connection.

![Network Troubleshooting](screenshots/04-internet-connectivity-fix.png)

## 🧠 What I Learned

Through this practical project, I gained hands-on experience with the following concepts:

1. **Virtualization:** Understanding how Oracle VirtualBox creates and manages virtual machines.
2. **NAT Networking:** Learning how NAT Network enables communication between virtual machines and external networks.
3. **IPv4 Addressing:** Configuring IP addresses, subnet masks, and default gateways.
4. **Linux Networking:** Working with Kali Linux network interfaces and NetworkManager.
5. **NMCLI:** Using Linux command-line tools to manage network connections.
6. **Virtual Machine Integration:** Configuring shared folders, shared clipboard, and drag-and-drop.
7. **Network Troubleshooting:** Identifying and resolving network connectivity issues.
8. **VM Snapshots:** Creating recovery points before performing security experiments.
9. **Technical Documentation:** Recording configurations, commands, and practical implementation steps.

## 🔮 Future Lab Expansion

The laboratory can be expanded by adding additional virtual machines to the same NAT Network.

**Planned Optional Additions:**

- Windows 10 / Windows 11
- Windows Server
- Android Virtual Machine
- Additional Linux Virtual Machines
- Intentionally vulnerable testing machines

These machines can be used for authorized network scanning, vulnerability assessment, packet analysis, and penetration-testing exercises.

## 🔐 Security & Ethical Use

This laboratory is designed exclusively for educational purposes and authorized cybersecurity testing.

All security assessments and penetration-testing activities must be performed only on systems owned by the user or where explicit permission has been granted.

## 🔗 Tools & Resources

- [7-Zip](https://7-zip.org/download.html)
- [Oracle VirtualBox](https://virtualbox.org/wiki/Downloads)
- [Kali Linux](https://kali.org/get-kali)
- [NetworkWalks](https://www.networkwalks.com/)

## 👨‍💻 Author

**Ramish Ali**

Computer Science | Networking | Cybersecurity


- LinkedIn: https://www.linkedin.com/in/ramish-ali01/

## 📌 Project Information

| Detail | Information |
|---|---|
| Program | Cybersecurity at NetworkWalks |
| Week | Week 01 |
| Task ID | WK1-PM1 |
| Project | Cybersecurity Lab Environment Setup |
| Platform | Oracle VirtualBox |
| Primary Operating System | Kali Linux |
| Network Type | NAT Network |
| Repository | TASK-WK1-PM1-Cybersecurity-Lab-Environment-Setup |

---

<p align="center">
  **LEARNING • BUILDING • SECURING**
  <br>
  Hands-on Cybersecurity & Networking Practice
</p>
