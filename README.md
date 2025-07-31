# SOC HOMELAB

## Table Contents
1. [Introduction](#introduction)
2. [Hardware Specifications](#hardware-Specifications)
3. [Set Up Virtual Machines](#Set-Up-Virtual-Machines)
### 🖥️ Step 1: Check Your Hardware
### 🧱 Step 2: Choose Your SIEM Platform
### 🔧 Step 3: Set Up Virtual Machines
### ⚙️ Step 4: Install and Configure Wazuh SIEM
### 📥 Step 5: Connect Agents to Wazuh
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
- ![image](https://github.com/NATTOMR/SOCHomeLab/blob/main/Screenshot%202025-07-31%20173311.png)

## ✅ Step 2: Download an ISO File
- Kali Linux (for hacking/pen testing)
➤ https://www.kali.org/get-kali/
- ![image](https://github.com/NATTOMR/SOCHomeLab/blob/main/kali.png)
- Ubuntu Desktop (for general Linux use)
➤ https://ubuntu.com/download/desktop
- - ![image](https://github.com/NATTOMR/SOCHomeLab/blob/main/ubuntu.png)
- Windows 10/11 ISO (for SOC/Victim VM)
➤ https://www.microsoft.com/software-download/windows10
  - - ![image](https://github.com/NATTOMR/SOCHomeLab/blob/main/windows.png)
    - - ![image]()

✅ Step 3: Create a New VM in VirtualBox
- Open VirtualBox
- Click "New"
- Name your VM (e.g., "Ubuntu SOC VM")
- Select Type = Linux or Windows, and Version (e.g., Ubuntu (64-bit), Windows 10)
- Click Next

✅ Step 4: Allocate Resources
Memory (RAM): Minimum 2 GB, recommended 4–8 GB

Hard Disk:

Choose Create a virtual hard disk now

Select VDI (VirtualBox Disk Image)

Choose Dynamically allocated

Size: 25–50 GB

✅ Step 5: Mount the ISO and Start the VM
Select your new VM → Click Start

VirtualBox will prompt you to select a start-up disk:

Click the folder icon and select the ISO you downloaded (Ubuntu, Kali, Windows)

Click Start

✅ Step 6: Install the OS Inside the VM
Follow the OS-specific installation steps:

🔹 For Ubuntu/Kali:
Choose language and keyboard layout

Set up username and password

Choose "Erase disk and install" (this only affects the virtual disk)

Wait for installation, then reboot

🔹 For Windows:
Choose version (Home/Pro)

Skip product key if you don’t have one

Choose the drive to install

Let it complete installation and reboot

✅ Step 7: Install Guest Additions (Important!)
Guest Additions improve performance and allow clipboard sharing, screen resizing, etc.

Start the VM

Click Devices → Insert Guest Additions CD image

Run the installer inside the VM

✅ Step 8: Configure VM Settings (Optional but Helpful)
Click your VM → Settings:

System → Processor: Allocate 2+ CPUs if available

Display → Video Memory: Set to max (128 MB)

Shared Clipboard / Drag’n’Drop: Enable (Host to Guest or Bidirectional)

Network → Adapter 1: Use Bridged Adapter or NAT depending on whether you want the VM to be visible on your network

✅ Step 9: Take Snapshots (Optional)
Before making changes or tests:

Go to Machine → Take Snapshot

Name it (e.g., “Clean Ubuntu Install”)

You can restore it later if something breaks

✅ Step 10: Update and Secure Your VM
Once the VM is running:

Run system updates (e.g., sudo apt update && sudo apt upgrade on Ubuntu)

Install any required tools or packages

Set a strong password for the user account
