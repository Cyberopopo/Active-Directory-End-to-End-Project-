# 📅 Week 1 — Phase 1: Company is Born (Foundation)  

---

## 🎯 Goal  
Build a functioning **Active Directory (AD) domain** with clients and basic policies.  

---

## 🔹 Step 1: Deploy Windows Server 2022 as Domain Controller (corp.local)  
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
   - Domain: `corp.local`  
3. Enter admin credentials from the Domain Controller.  
4. Restart the client → verify it is joined to the domain.  

📸 **Screenshot:**  
![Client Joined to Domain](https://i.imgur.com/Bf1xJl8.png)  

---

## 🔹 Step 3: Create Organizational Units (OUs)  
1. On `DC1`, open **Active Directory Users and Computers (ADUC)**.  
2. Right-click domain → **New → Organizational Unit**.  
3. Create:  
   - **HR**  
   - **IT**  
   - **Finance**  

📸 **Screenshot:**  
![Organizational Units](https://i.imgur.com/M3zrqjU.png)  

---

## 🔹 Step 4: Add Users and Groups  
1. Inside each OU, create sample users:  
   - HR: `hr_user1`, `hr_user2`  
   - IT: `it_admin`, `it_support`  
   - Finance: `fin_analyst`, `fin_manager`  
2. Create security groups for each department.  

📸 **Screenshot:**  
![Users and Groups](https://i.imgur.com/yZKIOyq.png)  

---

## 🔹 Step 5: Apply Basic GPOs  
1. Open **Group Policy Management** on `DC1`.  
2. Create and link new GPOs:  
   - **Password Policy** → enforce strong passwords.  
   - **Lock Screen Policy** → set auto lock after inactivity.  
   - **Drive Mapping Policy** → map network drive for shared files.  
3. Force update on clients:  
   ```bash
   gpupdate /force
