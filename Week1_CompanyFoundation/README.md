# 🗓 Week 1 — Phase 1: Company is Born (Foundation)

**Goal:** Build a functioning Active Directory (AD) domain.

---

## 🔹 Step 1: Deploy Windows Server 2022 as Domain Controller (cyberopopo.local)  
1. Power on your **Windows Server 2022 VM (DC1)**.  
2. Open **Server Manager** → click **Add roles and features**.  
3. Install the **Active Directory Domain Services (AD DS)** role.  
4. Promote the server to a **Domain Controller**.  
   - New forest name: `cyberopopo.local`  
   - Restart when prompted.  

📸 **Screenshot:**  
![Domain Controller Setup](https://i.imgur.com/dFYmpRD.png)

---

## 🔹 Step 2: Add Windows 10/11 Clients to the Domain  
1. Open **System Properties** on the client VM.  
2. Under **Computer Name → Change**, set:  
   - Domain: `cyberopopo.local`  
3. Enter admin credentials from the Domain Controller.  
4. Restart the client → verify it is joined to the domain.  

📸 **Screenshot:**  
![Client Joined to Domain](https://i.imgur.com/TUYQWTI.png)

---

## 🔹 Step 3: Create Organizational Units (OUs)  
1. Open **Active Directory Users and Computers (ADUC)**.  
2. Right-click your domain → **New → Organizational Unit**.  
3. Create the following OUs:  
   - **HR**  
   - **IT**  
   - **Finance**  
4. Ensure **Protect container from accidental deletion** is checked.

📸 **Screenshot:**  
![OUs Created](https://i.imgur.com/zfQGpbK.png)  <!-- replace with your actual OU screenshot -->

---

## 🔹 Step 4: Add Sample Users and Groups  
1. In each OU, right-click → **New → User**.  
2. Create sample users:  
   - HR: `Alice.HR`, `Bob.HR`  
   - IT: `Charlie.IT`, `Diana.IT`  
   - Finance: `Eve.Fin`, `Frank.Fin`  
3. Create security groups for each department and add users accordingly.

📸 **Screenshot:**  
![Users and Groups](https://i.imgur.com/zfQGpbK.png)  <!-- replace with your actual screenshot -->

---

## 🔹 Step 5: Apply Basic Group Policies  
1. Open **Group Policy Management**.  
2. Create a new GPO → link it to the domain.  
3. Configure policies like:  
   - **Password Policy**: Minimum 8 characters, complexity enabled  
   - **Account Lockout Policy**: 5 failed login attempts  
   - **Screen Lock/Idle Timeout**: 10 minutes  

📸 **Screenshot:**  
![GPO Applied](https://i.imgur.com/zfQGpbK.png)  <!-- replace with your actual GPO screenshot -->

---

✅ **Deliverables for Week 1:**  
- Functional Windows Server 2022 Domain Controller  
- 1–2 Windows clients joined to the domain  
- OUs, users, and groups created  
- Basic GPOs applied  
- Screenshots documented in GitHub
