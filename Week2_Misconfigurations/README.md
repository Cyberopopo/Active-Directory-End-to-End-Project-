# 🗓 Week 2 — Phase 2 (GUI only): Company Expands (Weaknesses Introduced)

**Goal:** Simulate misconfigurations using GUI tools only (lab environment only).

---

⚠️ **Safety reminder**
- Do this **only** in an isolated lab / VM snapshots taken.  
- Do **not** enable SMBv1 or weaken production systems.

---

## 🔹 Step 1 — Add users with weak passwords (ADUC GUI)

1. Log into the **Domain Controller** or a machine with **Remote Server Administration Tools (RSAT)** installed.  
2. Open **Active Directory Users and Computers** (`Start` → type **Active Directory Users and Computers** → Enter).  
3. Expand your domain → navigate to the target OU (e.g., `OU=HR`).  
4. Right-click the OU → **New** → **User**.  
5. Fill in: First name / Last name / User logon name (e.g., `WeakUser`) → **Next**.  
6. Enter a weak password in **Password** and **Confirm password**.  
   - Uncheck **User must change password at next logon** if you want the account to remain with the weak password.  
   - Optionally check **Password never expires** for persistent lab accounts.  
7. Click **Next → Finish**.  
8. Repeat for the number of weak accounts you need.  

📸 **Screenshot:**  
![Weak User Created](https://i.imgur.com/xNKU7td.png)  


---

## 🔹 Step 2 — Misconfigure groups & permissions via GUI (delegation & membership)

> Purpose: create intentionally risky delegations/memberships (lab-only).

---

### 🔹 A — Add a departmental group to another group
1. In **ADUC**, find the group you want to modify (e.g., `Server Operator`).  
2. Right-click → **Properties** → **Members** tab → **Add…** → add `IT_Group` → **OK**.  

---

### 🔹 B — Delegate control on an OU
1. In **ADUC**, right-click the OU → **Delegate Control…**.  
2. Click **Next** → **Add…** → pick the account/group you want to delegate (e.g., `weakuser`) → **Next**.  
3. Choose a task (e.g., **Create, delete and manage user accounts**)  
   → or **Custom task to delegate** → **Next → Finish**.  

📸 **Screenshot:**  
![Misconfigured Permissions](https://i.imgur.com/Jbv3aH7.png)  

---

## 🔹 Step 4 — Enable SMBv1 via GUI (Windows Features) & allow legacy auth via GPO GUI (lab only)

> **Warning:** SMBv1 and relaxed authentication are insecure. Use only on isolated lab VMs.

**A — Enable SMBv1 (GUI)**
1. On the target machine (file server or client VM): `Start` → **Control Panel** → **Programs and Features** → **Turn Windows features on or off**.  
2. In the list, find **SMB 1.0/CIFS File Sharing Support** → check it (expand and ensure **SMB 1.0/CIFS Server** is checked if required).  
3. Click **OK** → allow Windows to apply changes → **Restart** if prompted.

**Verify (GUI):** Reopen **Turn Windows features on or off** to confirm SMB 1.0 is checked; also open **Server Manager → File and Storage Services → Shares** to see server shares.

**B — Allow NTLM / relax LAN Manager auth via Group Policy Management (GUI)**
1. On the Domain Controller, open **Group Policy Management** (`Start` → type **Group Policy Management**).  
2. Right-click the domain or a test OU → **Create a GPO in this domain, and Link it here** → name it `Allow_NTLM_Lab`.  
3. Right-click the new GPO → **Edit**.  
4. Navigate to:  
   `Computer Configuration → Policies → Windows Settings → Security Settings → Local Policies → Security Options`.  
5. Find **Network security: LAN Manager authentication level** → double-click → set to a value that allows NTLM/LM responses (e.g., *"Send LM & NTLM responses"*), then **OK**.  
6. Close the editor. Ensure the GPO is linked to a test OU with only lab machines.

**Evidence:** screenshot GPO settings (the Security Options entry), screenshot the GPO linked under the domain/OU.

---

## 🔹 Step 5 — Create a vulnerable file share (File Explorer / Server Manager GUI)

**A — File Explorer method**
1. On the file server machine, open **File Explorer** → create folder `C:\VulnShare`.  
2. Right-click `C:\VulnShare` → **Properties** → **Sharing** tab → **Advanced Sharing…**.  
3. Check **Share this folder** → set Share name `VulnShare` → click **Permissions**.  
4. Click **Add…** → type `Everyone` → **OK** → check **Full Control** → **OK** → **Apply → OK**.  
5. Switch to **Security** tab → **Edit…** → **Add…** → add `Everyone` or `HR_Group` → give **Modify/Full control** → **OK**.

**B — Server Manager method (Windows Server)**
1. Open **Server Manager** → **File and Storage Services** → **Shares**.  
2. Click **Tasks** → **New Share** → choose an SMB share profile (Quick or SMB Share - Quick).  
3. Point to `C:\VulnShare`, name the share `VulnShare`, and on Permissions step add `Everyone` with Full Control → Finish.

**Evidence:** screenshot the Advanced Sharing dialog, Share Permissions, and Security tab showing NTFS permissions; screenshot Server Manager Shares view.

---

## 🔹 Step 6 — Document attack paths & collect GUI evidence

Collect the following from the GUI and save to your `week-2/evidence/` folder:

- ADUC screenshots: OU view, user properties, group properties (Members tab).  
- Export lists from ADUC: In the right-pane, select objects → right-click → **Export List…** → save CSV.  
- GPMC screenshots: GPO list, linked GPOs, and the specific Security Options entries.  
- File share screenshots: Advanced Sharing → Permissions, Security tab NTFS permissions.  
- Windows Features screenshot showing **SMB 1.0/CIFS** enabled.  
- Server Manager → File and Storage Services → Shares screenshot.  
- System timestamps: take a screenshot of the Event Viewer if desired (e.g., Security logs after tests).

---

## 🔁 GUI Rollback (undo changes)

1. **Disable SMBv1 (GUI)**  
   - Control Panel → Programs and Features → Turn Windows features on or off → uncheck **SMB 1.0/CIFS File Sharing Support** → OK → Restart.

2. **Remove vulnerable share (GUI)**  
   - File Explorer → right-click `C:\VulnShare` → Properties → Sharing → Advanced Sharing → uncheck **Share this folder**, or Server Manager → File and Storage Services → Shares → right-click `VulnShare` → **Stop Sharing** / **Remove**.  
   - Security tab → Edit → remove `Everyone` and restore proper NTFS permissions.

3. **Remove weak user accounts and groups (ADUC GUI)**  
   - ADUC → find user → right-click → **Delete** (confirm).  
   - ADUC → find group → right-click → **Delete** (confirm).  
   - Reverse any delegated OU control: ADUC → OU → **Delegate Control…** → select the delegated user → **Remove** or re-run the Delegation wizard and remove permissions.

4. **Unlink / delete lab GPO (GPMC GUI)**  
   - Group Policy Management → find `Allow_NTLM_Lab` → right-click → **Link Enabled** (uncheck) or **Delete** GPO (if safe).  
   - Force Group Policy refresh by restarting lab machines or using `gpupdate /force` on clients (GUI: restart clients).

---

## ✅ Deliverables (GUI-produced)
- `misconfigurations.md` — copy of the actions performed (include screenshot filenames).  
- `evidence/` — screenshots captured from ADUC, GPMC, File Explorer, Server Manager.  
- `weak-accounts.csv` — exported ADUC lists (use **Export List…** in ADUC).  
- `summary.md` — brief weakness report (impact, attack path, remediation).

---

**End of GUI-only Week 2 instructions.**
