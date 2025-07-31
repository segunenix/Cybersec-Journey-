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

![Example Alert](screenshots/alert-example.png)

### **What This Means**
- **Technique:** Brute Force (MITRE ATT&CK T1110)
- **Tactic:** Credential Access
- **Why Detected:** Wazuh monitored repeated failed authentication attempts in system logs.

**Full Simulation Steps → [Brute Force Detection Lab](../detection-labs/brute-force-test.md)**

---

## ✅ Other Alerts Reviewed
1. **File Integrity Monitoring:** Modification of system files.  
2. **Privilege Escalation:** Attempt to gain higher privileges.  
(See detailed attack simulations in the [Detection Labs](../detection-labs/) section.)

---

## ✅ Key Learnings
- Wazuh alerts are **log-driven**, not automatic.
- To analyze alerts effectively:
  - Know the **source log files** (e.g., `auth.log`, Windows Event Logs).
  - Understand the **MITRE ATT&CK mapping** for each alert.
- Simulating attacks is the best way to learn detection and response.

---

### ✅ Next Steps
- Expand detection coverage by simulating:
  - Privilege Escalation ([Lab here](../detection-labs/privilege-escalation-test.md))
  - Malware Execution
  - Suspicious Process Activity
