# SOC HOMELAB

## Table Contents
1. [Introduction](#introduction)
2. [Hardware Specifications](#hardware-Specifications)
3. [Set Up Virtual Machines](#Set-Up-Virtual-Machines)
4. [Choose SIEM Platform](#Choose-SIEM-Platform)
5. [Install and Configure Wazuh SIEM](#Install-and-Configure-Wazuh-SIEM)
6. [Connect Agents to Wazuh](#Connect-Agents-to-Wazuh)
### 📊 Step 7: Monitor and Investigate
### 📈 Step 8: Create Dashboards and Alerts
### 🧪 Step 9: Learn and Practice Use Cases

## 📌Introduction
This project demonstrates the setup of a home lab environment for cybersecurity testing, including an attack machine (Kali Linux), a target machine (Windows 10 VM), and a logging system (Splunk) to monitor malicious activities. The project involves:
- Setting up virtual machines
- Installing and configuring Sysmon for log collection
- Deploying malware using `msfvenom`
- Monitoring attacks using Splunk


## Hardware-Specifications
- Minimum specs (for running 2–3 VMs):
- CPU: 4 cores (i5/Ryzen 5 or better)
- RAM: 16 GB (8 GB possible with care)
- Storage: 256–500 GB SSD
- OS: Windows/Linux/Mac (any)

 ## Set-Up-Virtual-Machines
 ✅ Step 1: Download VirtualBox
🔗 Go to: https://www.virtualbox.org/wiki/Downloads

- Download the VirtualBox platform package for your OS (Windows/macOS/Linux).
- Install it using the default options.
- Also download and install the Extension Pack (for USB 3.0 support, etc.).
- ![image](https://github.com/NATTOMR/images/blob/main/extention.png)

## ✅ Step 2: Download an ISO File
- Kali Linux (for hacking/pen testing)
➤ https://www.kali.org/get-kali/
- ![image](https://github.com/NATTOMR/images/blob/main/kali.png)
- Ubuntu Desktop (for general Linux use)
➤ https://ubuntu.com/download/desktop
 - ![image](https://github.com/NATTOMR/images/blob/main/ubuntu.png)
- Windows 10/11 ISO (for SOC/Victim VM)
➤ https://www.microsoft.com/software-download/windows10
- ![image](https://github.com/NATTOMR/images/blob/main/windows.png)

✅ Step 3: Create a New VM in VirtualBox
- Open VirtualBox
- Click "New"
- ![image](https://github.com/NATTOMR/images/blob/main/Screenshot%202025-07-31%20174447.png)
- Name your VM (e.g., "Ubuntu SOC VM")
- Select Type = Linux or Windows, and Version (e.g., Ubuntu (64-bit), Windows 10)
- Click Next

✅ Step 4: Allocate Resources
Memory (RAM): Minimum 2 GB, recommended 4–8 GB
Hard Disk:
- Choose Create a virtual hard disk now
- Select VDI (VirtualBox Disk Image)
- Choose Dynamically allocated
- Size: 25–50 GB

✅ Step 5: Mount the ISO and Start the VM
- Select your new VM → Click Start
- VirtualBox will prompt you to select a start-up disk:
- Click the folder icon and select the ISO you downloaded (Ubuntu, Kali, Windows)
- Click Start

✅ Step 6: Install the OS Inside the VM
Follow the OS-specific installation steps:

🔹 For Ubuntu/Kali:
- Choose language and keyboard layout
- Set up username and password
- Choose "Erase disk and install" (this only affects the virtual disk)
- Wait for installation, then reboot

🔹 For Windows:
- Choose version (Home/Pro)
- Skip product key if you don’t have one
- Choose the drive to install
- Let it complete the installation and reboot

✅ Step 7: Install Guest Additions (Important!)
Guest Additions improve performance and allow clipboard sharing, screen resizing, etc.
- Start the VM
- Click Devices → Insert Guest Additions CD image
- Run the installer inside the VM

✅ Step 8: Take Snapshots (Optional)
Before making changes or tests:

- Go to Machine → Take Snapshot
- Name it (e.g., “Clean Ubuntu Install”)
- You can restore it later if something breaks

✅ Step 9: Update and Secure Your VM
 
 Once the VM is running:
- Run system updates (e.g., sudo apt update && sudo apt upgrade on Ubuntu)
- Install any required tools or packages
- Set a strong password for the user account

## ✅ Choose SIEM Platform
- SIEM, which stands for Security Information and Event Management, is a cybersecurity technology that helps organisations detect, analyse, and respond to security threats. It works by collecting and analysing security data from various sources within an IT environment, such as endpoints, servers, applications, and firewalls. SIEMs combine two key functions: Security Information Management (SIM) and Security Event Management (SEM)

### 🔹 Data Collection:
- SIEMs collect data from various sources, including logs, network traffic, and security tools. 
### 🔹Event Correlation:
- They analyse this data to identify patterns and relationships, potentially uncovering threats that individual security tools might miss. 
### 🔹 Real-time Monitoring:
- SIEMs provide a centralised view of security events, enabling real-time monitoring and alerting. 
### 🔹 Incident Response:
- They facilitate faster investigation and response to security incidents by providing context and insights. 
### 🔹 Compliance:
- SIEMs help organisations meet regulatory requirements by providing audit trails and reporting capabilities.

# ✅ Install-and-Configure-Wazuh-SIEM
Wazuh is an open-source SIEM with HIDS (Host-based IDS), log analysis, file integrity monitoring (FIM), and vulnerability detection.
This guide covers:
✅ Wazuh Server Setup (Kali)
✅ Elastic Stack Integration (for Dashboards)
✅ Adding Agents (Linux/Windows) for Monitoring

