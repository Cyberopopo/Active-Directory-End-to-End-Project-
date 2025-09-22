# 🛠️ Week 0 — Lab Setup (Environment Installation)

This folder contains documentation, screenshots, and notes for **setting up the lab environment** before starting the Active Directory project.  

We will install and configure:  
- **VMware Workstation Pro** (or VirtualBox)  
- **Windows Server 2022** (Domain Controller)  
- **Windows 10 Pro Client**  
- **Windows 11 Pro Client**  
- **Kali Linux Attacker Machine**  

---

## 🎯 Goal
Prepare a fully functional virtual lab environment to simulate a corporate Active Directory infrastructure.

---

## ✅ Tasks
- Install VMware Workstation Pro  
- Create and configure Windows Server 2022 VM  
- Create and configure Windows 10 Pro client VM  
- Create and configure Windows 11 Pro client VM  
- Create and configure Kali Linux VM  

---

## 🖥️ Step 1: Install Virtualization Software
1. Download and install **VMware Workstation Pro** (or VirtualBox).  
2. Verify virtualization is enabled in BIOS/UEFI.  

📸 **Screenshot:**  
![VMware Installed](https://i.imgur.com/xxxxx.png)

---

## 🏛️ Step 2: Create Windows Server 2022 VM
1. Open VMware → **Create a New Virtual Machine**.  
2. Select **I will install the OS later**.  
3. OS: **Windows Server 2022 (x64)**.  
4. Name VM: `DC1`  
5. Set disk size: **60 GB** (recommended).  
6. Hardware: **4 GB RAM, 2 CPUs, Network = Host-Only**.  
7. Mount **Windows Server 2022 ISO**.  

📸 **Screenshot:**  
![Windows Server VM Setup](https://i.imgur.com/xxxxx.png)

---

## 🖥️ Step 3: Create Windows 10 Pro Client VM
1. Start New VM Wizard → **Typical**.  
2. Select **I will install OS later**.  
3. OS: **Windows 10 Pro (x64)**.  
4. Name VM: `Win10-Client1`.  
5. Disk size: **20 GB**, Split into multiple files.  
6. Hardware: **2 GB RAM, 2 CPUs, Host-Only network**.  
7. Mount **Windows 10 ISO**.  

📸 **Screenshot:**  
![Windows 10 VM Setup](https://i.imgur.com/xxxxx.png)

---

## 🖥️ Step 4: Create Windows 11 Pro Client VM
1. Start New VM Wizard → **Typical**.  
2. Select **I will install OS later**.  
3. OS: **Windows 11 Pro (x64)**.  
4. Name VM: `Win11-Client1`.  
5. Disk size: **25 GB**, Split into multiple files.  
6. Hardware: **4 GB RAM, 2 CPUs, Host-Only network**.  
7. Mount **Windows 11 ISO**.  

📸 **Screenshot:**  
![Windows 11 VM Setup](https://i.imgur.com/xxxxx.png)

---

## 🐧 Step 5: Create Kali Linux VM
1. Download **Kali Linux ISO** from official site.  
2. Open VMware → **Create New VM**.  
3. OS: **Linux → Debian 64-bit**.  
4. Name VM: `Kali-Attacker`.  
5. Disk size: **40 GB**, Split into multiple files.  
6. Hardware: **4 GB RAM, 2 CPUs, Bridged network (for internet)**.  
7. Mount **Kali Linux ISO**.  

📸 **Screenshot:**  
![Kali Linux VM Setup](https://i.imgur.com/xxxxx.png)

---

## ⚙️ Step 6: Networking Setup
1. Open VMware **Virtual Network Editor**.  
2. Configure a **Host-Only Network (VMnet1)** for AD lab traffic.  
3. Ensure **Server + Clients** are on Host-Only.  
4. Kali can have **dual NICs** (Host-Only + Bridged).  

📸 **Screenshot:**  
![VMware Network Setup](https://i.imgur.com/xxxxx.png)

---

## 📖 Summary
At the end of **Week 0 (Lab Setup)**, we have:  
✔️ VMware Workstation installed  
✔️ Windows Server 2022 (DC1) VM created  
✔️ Windows 10 & 11 client VMs created  
✔️ Kali Linux attacker machine created  
✔️ Networking configured (Host-Only for lab, Bridged for attacker if needed)  

✅ Next step: Move to **Week 1 — Phase 1: Company is Born (Foundation)**, where we install AD DS and build the company’s Active Directory domain.
