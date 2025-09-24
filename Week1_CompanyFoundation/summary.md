# 📝 Week 1 Summary Report — Phase 1: Company is Born (Foundation)

**Goal:** Build a functioning Active Directory (AD) domain.

---

## 🔹 Objectives Achieved
- Deployed **Windows Server 2022** as a Domain Controller (`cyberopopo.local`).  
- Added **Windows 10 client** to the domain.  
- Created **Organizational Units (OUs)**: HR, IT, Finance.  
- Added **sample users and security groups**.  
- Applied **basic Group Policy Objects (GPOs)** for security.

---

## 🔹 Key Steps Completed

1. **Domain Controller Deployment**
   - Installed **AD DS role**.  
   - Promoted server to **Domain Controller** with new forest `corp.local`.  
   - Verified server restart and functionality.  
  

2. **Client Domain Join**
   - Configured **Windows 10 VM** to join domain `cyberopopo.local`.  
   - Entered **DC admin credentials**.  
   - Restarted and verified domain membership.  
  
3. **Organizational Units (OUs)**
   - Created OUs for **HR, IT, and Finance**.  
   - Enabled **protection from accidental deletion**.  
 
4. **Users and Groups**
   - Created sample users in each OU.  
   - Created security groups and added users accordingly.  

5. **Basic GPOs Applied**
   - Password policy: Minimum 12 characters, complexity enabled.  
   - Account lockout: 5 failed login attempts.  
   - Screen lock/idle timeout: 5 minutes.  
 
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
