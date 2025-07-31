# 📊 Wazuh Logs Analysis

This section summarizes how I analyzed alerts in Wazuh after setting up the manager and agent:
- What events generate alerts
- How to interpret alert details
- How to map alerts to MITRE ATT&CK techniques

---

## ✅ Why This Was Important
When I first installed and connected the agent, I expected alerts to appear immediately.  
But the dashboard stayed empty. I later realized Wazuh only alerts when specific events occur.  
This led me to perform **log analysis after generating test events**.

---

## ✅ SSH Brute Force Alert (Example)
I simulated a brute force attack by triggering multiple failed SSH login attempts on a Windows system using a PowerShell script.  
Wazuh detected the activity and raised the following alert:

- **Rule ID:** 5712  
- **Description:** Multiple SSH authentication failures  
- **Severity:** High  

[![Example Alert](screenshots/alert-example.png)](https://github.com/segunenix/AllScreenshots/blob/05f3de61764c2903a7190bd15b0a231a69ce76a2/Screenshot%202025-07-29%20201104.png)

### **What This Means**
- **Technique:** Brute Force (MITRE ATT&CK T1110)
- **Tactic:** Credential Access
- **Why Detected:** Wazuh monitored repeated failed authentication attempts in system logs.


---
