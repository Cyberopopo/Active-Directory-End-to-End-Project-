# 📌 Summary — Weakness Introduced as Company Expands  

As the company expanded, file shares and access permissions were created to improve collaboration.  
However, this stage introduced **critical security weaknesses** due to misconfigurations and overly broad permissions.  

## 🔹 Key Weaknesses Introduced  
- **Overly permissive shares**  
  - A folder (`C:\VulnShare`) was shared with **Everyone → Full Control**.  
  - This allows any authenticated user on the network to read, modify, or delete files.  

- **Insecure NTFS permissions**  
  - NTFS (Security tab) was also configured to give **Everyone or broad groups** Modify/Full Control.  
  - This bypasses the principle of least privilege.  

- **Lack of role-based access control (RBAC)**  
  - Instead of restricting access to specific departmental groups (e.g., HR, Finance, IT), access was given globally.  

- **Expansion without proper governance**  
  - As departments grew, permissions were granted quickly for convenience rather than security.  
  - This mirrors real-world practices where speed often outweighs proper security configuration.  

## 🚩 Risk to the Organization  
- **Data exposure** → Confidential files can be accessed by unauthorized users.  
- **Privilege escalation** → Attackers can drop malicious files (e.g., ransomware) into shared folders.  
- **Loss of integrity** → Critical business data could be altered or deleted by accident or maliciously.  
- **Insider threats** → Any employee has the same power as an administrator within the vulnerable share.  

---

✅ **Learning Point**: Expansion without security controls leads to misconfigured shares and weak access policies.  
This sets the stage for **later exploitation phases**, where attackers can leverage these weaknesses to move laterally and escalate privileges. 

