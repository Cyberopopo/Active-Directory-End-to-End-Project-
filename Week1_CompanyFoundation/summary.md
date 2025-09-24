# 📝 Week 1 Summary Report — Phase 1: Company is Born (Foundation)

**Goal:** Build a functioning Active Directory (AD) domain.

---

## 🔹 Objectives Achieved
- Deployed **Windows Server 2022** as a Domain Controller (`corp.local`).  
- Added **Windows 10/11 clients** to the domain.  
- Created **Organizational Units (OUs)**: HR, IT, Finance.  
- Added **sample users and security groups**.  
- Applied **basic Group Policy Objects (GPOs)** for security.

---

## 🔹 Key Steps Completed

1. **Domain Controller Deployment**
   - Installed **AD DS role**.  
   - Promoted server to **Domain Controller** with new forest `corp.local`.  
   - Verified server restart and functionality.  
   - 📸 Screenshot: ![Domain Controller Setup](https://i.imgur.com/dFYmpRD.png)

2. **Client Domain Join**
   - Configured **Windows 10/11 VM** to join domain `cyberopopo.local`.  
   - Entered **DC admin credentials**.  
   - Restarted and verified domain membership.  
   - 📸 Screenshot: ![Client Joined to Domain](https://i.imgur.com/TUYQWTI.png)

3. **Organizational Units (OUs)**
   - Created OUs for **HR, IT, and Finance**.  
   - Enabled **protection from accidental deletion**.  
   - 📸 Screenshot: ![OUs Created](https://i.imgur.com/zfQGpbK.png) <!-- replace with actual -->

4. **Users and Groups**
   - Created sample users in each OU.  
   - Created security groups and added users accordingly.  
   - 📸 Screenshot: ![Users and Groups](https://i.imgur.com/zfQGpbK.png) <!-- replace with actual -->

5. **Basic GPOs Applied**
   - Password policy: Minimum 8 characters, complexity enabled.  
   - Account lockout: 5 failed login attempts.  
   - Screen lock/idle timeout: 10 minutes.  
   - 📸 Screenshot: ![GPO Applied](https://i.imgur.com/zfQGpbK.png) <!-- replace with actual -->

---

## 🔹 Challenges Encountered
- Ensuring **proper DNS configuration** during domain join.  
- Restarting VMs multiple times to verify **domain replication**.  
- Screenshot management for proper documentation.

---

## 🔹 Learnings
- Understanding the **importance of structured OUs** and user management.  
- Applying **basic security policies** at the domain level.  
- Establishing a **baseline AD environment** for future phases.  

---

## 🔹 Next Steps (Week 2 Preview)
- Simulate **real-world misconfigurations**.  
- Add **users with weak passwords**.  
- Misconfigure **groups and permissions**.  
- Enable **vulnerable protocols** (SMBv1, NTLM).  
- Document **attack paths** for cybersecurity learning.
