# 🔍 Detection Lab: Privilege Escalation (Windows)

This lab simulates a **privilege escalation attempt** on Windows and demonstrates how Wazuh detects it using Sysmon logs.

---

## ✅ Objective
- Simulate privilege escalation on a Windows machine.
- Detect the event with Wazuh using Sysmon and Windows Event Logs.
- Map detection to MITRE ATT&CK.

---

## ✅ My Experience
*(Write your experience here after testing. Example:)*
At first, I thought running `runas` would immediately create a critical alert, but nothing appeared until I enabled the right Sysmon event IDs in my configuration. This taught me that detection depends heavily on correct event logging.

---

## ✅ Lab Setup
- **Machine:** Windows with Wazuh Agent + Sysmon installed
- **Manager:** Wazuh on Ubuntu
- **Tools Used:** PowerShell, Sysmon, Wazuh Dashboard

---

## ✅ Steps to Simulate Privilege Escalation

### **Step 1: Launch PowerShell as Administrator**
Run:
```powershell
Start-Process PowerShell -Verb RunAs

