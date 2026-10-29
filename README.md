# NetworkWalks-B083-weekly-Cybersecurity-lab-setup
My cybersecurity lab setup week 1
# Cybersecurity Lab Environment Setup

## 📌 Project Overview

This project documents my setup of a virtual cybersecurity laboratory using Oracle VirtualBox and Kali Linux 2023.4 on a Windows 11 host machine.

I configured a virtual network named **LabNetwork** to provide a networking environment for my Kali Linux virtual machine. This lab will serve as my practical learning environment for exploring cybersecurity concepts, network reconnaissance, network scanning, and security assessment in a controlled and authorized setting.

This project also provides a foundation for expanding my lab in the future by adding other virtual machines for testing and learning purposes.

## 🎯 Objectives

The main objectives of this project are to:

- Set up Oracle VirtualBox as my virtualization platform.
- Import and configure Kali Linux 2023.4 as a virtual machine.
- Create a NAT Network named **LabNetwork** using the subnet `10.0.0.0/24`.
- Configure the Kali Linux virtual machine's network settings.
- Configure and verify the virtual machine's IP address, gateway, and DNS settings.
- Test network connectivity and DNS resolution.
- Create a virtual machine snapshot for recovery, if completed.
- Document my lab configuration and setup process using screenshots.
- Establish a foundation for future hands-on cybersecurity exercises.

## 🛡️ Purpose of the Lab

The purpose of my lab is to provide a controlled virtual environment where I can develop my practical cybersecurity skills using Kali Linux 2023.4 and Oracle VirtualBox.

Through this lab, I aim to gain hands-on experience with networking concepts, security tools, and authorized testing techniques. The environment will also allow me to practice and explore different cybersecurity activities as I progress through my learning.

The lab can be used for activities such as:

- **Network reconnaissance** — learning how to discover devices and gather network information.
- **Port scanning** — identifying open ports on authorized test systems.
- **Vulnerability assessment** — learning how to identify potential security weaknesses.
- **Packet analysis** — examining network traffic to understand communication between systems.
- **Web security testing** — exploring common web application security issues in a controlled environment.
- **Exploitation practice** — learning how vulnerabilities may be exploited in systems specifically set up for testing.
- **Security-tool experimentation** — becoming familiar with the tools available in Kali Linux.

⚠️ **Ethical and Responsible Use:** I will use this laboratory only for educational purposes and test systems that I own or have explicit permission to assess. All security testing will be conducted responsibly and within authorized environments.

LAB ARCHITECTURE
![Cybersecurity Lab Environment Diagram](Cybersecurity%20Lab%20Environment%20Diagram.png)


## 🛠️ Lab Configurations

| Configuration | Details |
|:---|:---|
| 🖥️ Host OS | Windows 11 |
| 🧰 Hypervisor | Oracle VirtualBox 7.2.22 |
| 🐉 Security OS | Kali Linux 2023.4 |
| 🌐 Virtual Network | NAT Network (`LabNetwork`) |
| 📡 Network Address | `10.0.0.0/24` |
| 🚪 Default Gateway | `10.0.0.1` |
| 🌍 DNS Server | `10.0.0.1` |
| 🐧 Kali IP Address | `10.0.0.2/24`  |
| 🔮 Future VM Range | `10.0.0.3–10.0.0.99` |


# 🪜 Lab Setup Procedure

## Step 1: Install 7-Zip

7-Zip was used to extract the Kali Linux virtual-machine package, which may be distributed as a `.7z` archive.

**Tool:** 7-Zip

---

## Step 2: Install VirtualBox

Oracle VirtualBox 7.2.22 was installed on the Windows 11 host to run the Kali Linux virtual machine.

**Tool:** Oracle VirtualBox 7.2.22

---

## Step 3: Create the NAT Network

A dedicated NAT Network was created in VirtualBox to provide network connectivity for the cybersecurity lab.

**Network Configuration:**

| Setting | Value |
|:---|:---|
| Network Name | `LabNetwork` |
| IPv4 Prefix | `10.0.0.0/24` |
| DHCP | Enabled |
| IPv6 | Disabled |
| Default Gateway | `10.0.0.1` |


![Network Settings](network%20settings.png)

A NAT Network was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This will allow future attacker and target VMs to communicate within the lab.

Step 4. Import Kali Linux
The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:

Adapter 1
Attached to: NAT Network
Network:     NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
The VM was allocated:

RAM: 2048 MB
![Title Image](title%20image.png)

## Step 5: Configure the Kali Linux Network

The Kali Linux network interface was checked using the `ip addr` command. The output confirmed that the `eth0` interface was active and assigned the expected IPv4 address.

**Verified Network Configuration:**

| Setting | Value |
|:---|:---|
| Network Interface | `eth0` |
| Interface Status | `UP` |
| IP Address | `10.0.0.2` |
| Subnet Mask | `255.255.255.0` |
| CIDR Prefix | `/24` |

The configured IPv4 address allows the Kali Linux virtual machine to be identified within the lab network for future networking and cybersecurity exercises.

![Wireless Connection Screenshot](wirelessconnection%20screenshot.png)

## Step 6. Create a Clean VM Snapshot

After configuring the Kali Linux network, an existing VirtualBox snapshot was renamed to:

```text
Clean Kali - Network Setup
```

This snapshot serves as a recovery point for the Kali Linux virtual machine. It can be used to return the VM to a previously saved state if future laboratory exercises change the network configuration or affect the system.

The snapshot is saved in Oracle VirtualBox and documents the configured laboratory environment.

**Snapshot Status:** Created and renamed. Restoration testing is pending.

---

# 🔎 Lab Verification

The following tests were performed to verify the Kali Linux network configuration, internet connectivity, DNS resolution, and Nmap installation.

| **✅ Test** | **🧾 Command** | **🎯 Actual Result** | **📊 Status** |
|---|---|---|---|
| 🌐 Check IP address | `ip addr` | `eth0`: `10.0.0.2/24` | ✅ Passed |
| 🛣️ Check routing table | `ip route` | Default gateway: `10.0.0.1` | ✅ Passed |
| 📡 Test gateway connectivity | `ping -c 4 10.0.0.1` | 4 packets received; 0% packet loss | ✅ Passed |
| 🌍 Test internet connectivity | `ping -c 4 8.8.8.8` | 4 packets received; 0% packet loss | ✅ Passed |
| 🔎 Test DNS resolution | `nslookup networkwalks.com` | Resolved to `192.232.216.135` using DNS server `10.0.0.1` | ✅ Passed |
| 🧰 Verify Nmap installation | `nmap --version` | Nmap version `7.94SVN` | ✅ Passed |
| 🔄 Verify snapshot restoration | Restore the saved snapshot and run `ip addr` | Confirm the saved baseline configuration is restored | ⏳ Pending |

### Example Results

**IP Address**
```text
Interface: eth0
IPv4 address: 10.0.0.2/24
Network: 10.0.0.0/24
```

**Default Gateway**
```text
10.0.0.1
```

**DNS Resolution**
```text
DNS server: 10.0.0.1
Domain: networkwalks.com
Resolved IP: 192.232.216.135
```

**Internet Connectivity**
```text
Destination: 8.8.8.8
Packets received: 4
Packet loss: 0%
```

**Nmap Installation**
```text
Nmap version 7.94SVN
```

### Verification Summary

Six network and software verification tests passed. The VirtualBox snapshot was created previously and renamed to identify the saved network configuration. Snapshot restoration remains pending until it has been tested.

# 🐞 Problems Encountered & Solutions

During the setup and documentation of this cybersecurity laboratory, I encountered practical challenges involving screenshot management, VirtualBox snapshot navigation, and network verification.

## Problem 1. Transferring Screenshots from Kali Linux to Windows

**Problem:** Transferring screenshots from the Kali Linux virtual machine to the Windows host was challenging during the documentation process.

**Solution:** I worked through the screenshot transfer process and successfully uploaded the laboratory screenshots directly to my GitHub repository alongside the `README.md` file.

**Outcome:** The screenshots became available in the repository for documenting the laboratory configuration and setup.

## Problem 2. Locating VirtualBox Snapshot Controls

**Problem:** I was initially unsure where to shut down Kali Linux and how to locate and manage virtual machine snapshots in VirtualBox.

**Solution:** I navigated to the VirtualBox Snapshots view, identified the existing snapshots, and renamed `Snapshot 2` to `Clean Kali - Network Setup`.

**Outcome:** The snapshot has a clearer name that identifies its intended purpose as a network configuration recovery point. Restoring the snapshot has not yet been tested.

## Problem 3. Verifying Network Connectivity and Configuration

**Problem:** I needed to verify that the Kali Linux virtual machine had a working network configuration and could communicate with its gateway and the internet.

**Solution:** I used Linux networking commands to inspect the IP address and routing table, test connectivity, and verify DNS resolution.

Commands used:

```bash
ip addr
ip route
ping -c 4 10.0.0.1
ping -c 4 8.8.8.8
nslookup networkwalks.com
nmap --version
```

**Outcome:** The tests confirmed the Kali IP address (`10.0.0.2/24`), successful gateway and internet connectivity, successful DNS resolution, and the installed Nmap version (`7.94SVN`).

---

# 💡 What I Learned

Through this project, I learned how to configure and verify a Kali Linux virtual machine for cybersecurity practice.

### 1. Virtual Machine Networking

I learned how VirtualBox network settings, IP addresses, subnet masks, and default gateways affect connectivity.

### 2. Network Troubleshooting

I gained practical experience using `ip addr`, `ip route`, `ping`, and `nslookup` to check network configuration and connectivity.

### 3. DNS Resolution

I learned how to verify that a domain name resolves to an IP address using a DNS server.

### 4. Nmap Verification

I learned how to check whether Nmap is installed and identify its version using `nmap --version`.

### 5. Virtual Machine Snapshots

I learned how to locate and rename snapshots in VirtualBox and why a recovery point is useful before performing experimental cybersecurity exercises.

### 6. Technical Documentation

I learned how to organize screenshots, record test results, and document configuration and troubleshooting steps in a GitHub README.

---

# 🔐 Security & Ethical Use

This laboratory is intended strictly for educational purposes and authorized cybersecurity practice. All scanning and testing should be performed only on systems owned by me or on systems for which I have explicit permission.

# 🛠️ Tools & Resources

- **7-Zip:** [https://7-zip.org/download.html](https://7-zip.org/download.html)
- **Oracle VirtualBox:** [https://virtualbox.org/wiki/Downloads](https://virtualbox.org/wiki/Downloads)
- **Kali Linux:** [https://kali.org/get-kali](https://kali.org/get-kali)
- **Nmap:** [https://nmap.org/download.html](https://nmap.org/download.html)

---

# 👤 Author

**Silosizo Dube**  
Cybersecurity Student | Aspiring Cybersecurity Professional

LinkedIn: [linkedin.com/in/silosizo-dube-5523a9210](https://www.linkedin.com/in/silosizo-dube-5523a9210)

---

## 📌 Project Information

- **Program Name:** Cybersecurity at NetworkWalks
- **Week:** 01
- **Project:** Cybersecurity & Pentesting Lab Setup
- **Repository:** GitHub
