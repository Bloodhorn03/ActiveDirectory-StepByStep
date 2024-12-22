# Active Directory Step-by-Step Guide

Welcome to the **Active Directory Step-by-Step Guide** by **Francesco DNT**! 🚀  
This repository is designed to help IT professionals and beginners learn how to set up, configure, and manage Active Directory (AD) in Windows environments.

---

## 🏗️ What is Active Directory?
Active Directory (AD) is a Microsoft technology for managing computers, users, and resources in a network. It is the backbone of many IT infrastructures, providing authentication, authorization, and more.

---

## 📚 Topics Covered

1. **Introduction to Active Directory**  
   - Overview of AD components: Forests, Trees, Domains, Organizational Units (OUs).  

2. **Step-by-Step Installation Guide**  
   - Prerequisites for installing AD.  
   - How to install AD DS and promote a server to a Domain Controller.  

3. **Basic Configuration**  
   - Creating and managing users, groups, and OUs.  
   - Applying Group Policies (GPO) for centralized management.  

4. **Advanced Administration**  
   - Delegation of control to other administrators.  
   - Monitoring and troubleshooting common AD issues.  

5. **Automation Scripts**  
   - Use PowerShell scripts for faster and consistent management.  

---

## 🛠️ Prerequisites

Before you begin, ensure you have:
- A Windows Server environment (2016, 2019, or 2022 recommended).
- Basic knowledge of networking and server administration.
- Administrator privileges on the system.

---

## 📖 Step-by-Step Guide

### **1. Install Active Directory**
1. Open the **Server Manager** on your Windows Server.
2. Click **Add Roles and Features**.
3. Select **Active Directory Domain Services (AD DS)**.
4. Complete the installation wizard.

---

### **2. Promote the Server to a Domain Controller**
1. After installing AD DS, click **Promote this server to a domain controller** in Server Manager.
2. Select one of the following:
   - **Add a new forest**: If you're creating a new AD structure.  
   - **Add a domain to an existing forest**: For expanding an existing setup.
3. Provide a domain name, e.g., `example.local`, and complete the configuration.
4. Restart the server when prompted.

---

### **3. Managing Users and Groups**
- Open **Active Directory Users and Computers (ADUC)**:
  1. Create Organizational Units (OUs):
     - Right-click the domain > **New** > **Organizational Unit**.
     - Name it, e.g., `IT Department`.
  2. Add Users:
     - Right-click the OU > **New** > **User**.
     - Fill in the user details and set a password.

---

## 📜 Example PowerShell Scripts

### **Create a New User**
```powershell
# Import the Active Directory module
Import-Module ActiveDirectory

# Create a new AD user
New-ADUser -Name "Jane Doe" -GivenName "Jane" -Surname "Doe" `
  -SamAccountName "janed" -UserPrincipalName "janed@example.local" `
  -Path "OU=IT Department,DC=example,DC=local" `
  -AccountPassword (ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force) `
  -Enabled $true
