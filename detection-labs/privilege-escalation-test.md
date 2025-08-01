# 🔍 Detection Lab: Privilege Escalation (Windows)

This lab simulates a **privilege escalation attempt** on Windows and demonstrates how Wazuh detects it using Sysmon logs.

---

## ✅ Objective
- Simulate privilege escalation on a Windows machine.
- Detect the event with Wazuh using Sysmon and Windows Event Logs.
- Map detection to MITRE ATT&CK.

---

## ✅ Lab Setup
- **Machine:** Windows with Wazuh Agent + Sysmon installed
- **Manager:** Wazuh on Ubuntu
- **Tools Used:** PowerShell, Sysmon, Wazuh Dashboard

---

## ✅ Steps to Simulate Privilege Escalation

### **Step 1: Launch PowerShell as Administrator**
### **Step 2: Create a New User With This Command**
```net user testuser Password123 /add```
https://github.com/segunenix/AllScreenshots/blob/e2add480b00286264a2f7b3a7be75f7eca6a6242/Screenshot%202025-08-01%20055946.png
### **Step 3: Open Powershell as the newly Created User**
```runas /user:testuser powershell```
https://github.com/segunenix/AllScreenshots/blob/e2add480b00286264a2f7b3a7be75f7eca6a6242/Screenshot%202025-08-01%20060427.png
NOTE: A new window will appear 
### **Step 4: Now Open Powershell as an Admin from the new user(testuser)**
```runas /user:Admin powershell```
https://github.com/segunenix/AllScreenshots/blob/e2add480b00286264a2f7b3a7be75f7eca6a6242/Screenshot%202025-08-01%20060103.png
These will trigger a privilege escalation event with Event ID (4672)

https://github.com/segunenix/AllScreenshots/blob/e2add480b00286264a2f7b3a7be75f7eca6a6242/Screenshot%202025-08-01%20054403.png


