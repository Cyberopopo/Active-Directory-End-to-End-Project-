# 🖥️ Week 0 — Lab Setup  

### 🎯 Goal  
Prepare the virtualization environment and download all necessary operating systems for the Active Directory Lab.  

---

## 🔹 Step 1: Install Virtualization Software  
- Download and install **VMware Workstation Pro**.  
- Verify that virtualization is enabled in **BIOS/UEFI**.  

📸 **Screenshot:**  
![VMware Installation](https://i.imgur.com/zfQGpbK.png)


---

## 🔹 Step 2: Download Operating System ISOs  
Download the required ISO files for the lab:  
- **Windows Server 2022 ISO** → will serve as the **Domain Controller (DC1)**.  
- **Windows 10 Pro ISO** → client machine #1.  
- **Windows 11 Pro ISO** → client machine #2.  
- **Kali Linux ISO** → attacker machine.  

📸 **Screenshot:**  
![Downloaded ISOs](https://i.imgur.com/M3zrqjU.png)

---

## 🔹 Step 3: Create Domain Controller VM (Windows Server 2022)  
1. Open VMware Workstation → **Create a New Virtual Machine**.  
2. Choose **I will install the operating system later**.  
3. Select Guest OS: **Windows Server 2022**.  
4. Name the VM: `DC1`.  
5. Allocate:  
   - **RAM**: 2 GB  
   - **CPU**: 2 cores  
   - **Disk**: 20 GB  
   - **Network Adapter**: Host-Only  
6. Mount the **Windows Server 2022 ISO**.  
7. Finish setup → Power on → begin installation.  

📸 **Screenshot:**  
![Domain Controller VM Creation](https://i.imgur.com/yZKIOyq.png)


---

## 🔹 Step 4: Create Windows 10 Client VM  
1. New VM → Select **Windows 10 Pro (x64)**.  
2. Name: `Win10-Client1`.  
3. Allocate:  
   - **RAM**: 2 GB  
   - **CPU**: 2 cores  
   - **Disk**: 20 GB  
   - **Network Adapter**: Host-Only  
4. Mount the **Windows 10 ISO**.  
5. Finish and power on.  

📸 **Screenshot:**  
![Create Windows 10 VM](https://i.imgur.com/Bf1xJl8.png)


---

## 🔹 Step 5: Create Windows 11 Client VM  
1. New VM → Select **Windows 11 Pro (x64)**.  
2. Name: `Win11-Client1`.  
3. Allocate same resources as Windows 10 client.  
4. Mount the **Windows 11 ISO**.  
5. Finish and power on.  

📸 **Screenshot:**  
![Create Windows 11 VM](IMGUR_LINK_HERE)

---

## 🔹 Step 6: Create Kali Linux Attacker VM  
1. New VM → Select **Linux → Debian 64-bit**.  
2. Name: `Kali`.  
3. Allocate:  
   - **RAM**: 2 GB  
   - **CPU**: 2 cores  
   - **Disk**: 20 GB  
4. Mount the **Kali Linux ISO**.  
5. Finish and power on.  

📸 **Screenshot:**  
![Create Kali Linux VM](IMGUR_LINK_HERE)

---

## ✅ Deliverables for Week 0  
- VMware/VirtualBox installed.  
- ISO files downloaded (Windows Server, Windows 10, Windows 11, Kali Linux).  
- 4 Virtual Machines created:  
  - `DC1` (Windows Server 2022)  
  - `Win10-Client1`  
  - `Win11-Client1`  
  - `Kali`  

📸 **Screenshot:**  
![All VMs Created](IMGUR_LINK_HERE)
