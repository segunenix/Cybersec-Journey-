# Active Directory Home Lab Project 🖥️🔐
## Introduction  
This project documents how I built and configured an **Active Directory environment** in my home lab. My main goals were to: - Learn how to deploy and manage a Windows Server Domain Controller.  
- Create and manage users, groups, and Group Policies.  
- Deploy Sysmon for endpoint logging.  
- Send logs to Splunk for security monitoring and analysis.  
- Document challenges and solutions for future reference.  

---

## Lab Architecture  
- **Hypervisor:** VirtualBox
- **VMs Used:**  
  - Windows Server 2019/2022 (Domain Controller)  
  - Windows 11 Client  
  - Ubuntu Server (Splunk Enterprise)  

**Project Diagram:**  
https://github.com/segunenix/AllScreenshots/blob/0c16ce2fd599e084d82bdbbe6d43309d528fca71/ad-project%20diagram.png

---

## Setup Process  

### Network Configuration  
- Configured a custom NAT network.  
https://github.com/segunenix/AllScreenshots/blob/680a3a2875958360d41deb2de8b1b41d097e9bef/Screenshot%202025-08-17%20122214.png
- Assigned static IPs:  
  - `192.168.10.7` → Windows Server (Domain Controller)  
https://github.com/segunenix/AllScreenshots/blob/c775c08947db11242e61b7893eb0ce6fc481a222/Screenshot%202025-08-17%20124647.png
  - `192.168.10.100` → Windows 11 Client  
https://github.com/segunenix/AllScreenshots/blob/27d20a7ae65ca842a0f2bb0d4ad00b9b50801606/Screenshot%202025-08-17%20123139.png
  - `192.168.10.10` → Ubuntu Server (Splunk Enterprise)  
https://github.com/segunenix/AllScreenshots/blob/4a4f72ff5b1c1376c3e95f6302b8bec5ff71a179/Screenshot%202025-08-17%20123429.png

### Domain Controller Setup  
- Installed AD DS role on Windows Server.  
https://github.com/segunenix/AllScreenshots/blob/73ba55cd34433fed0ec5f8503c316487447b7534/Screenshot%202025-08-17%20125305.png
- Promoted server to Domain Controller.  
https://github.com/segunenix/AllScreenshots/blob/bd9e7bb262600cbb392888b5ad8269e0b97038b4/Screenshot%202025-08-17%20125551.png
(i already promoted it without taking a screenshot, but the flag will be in the marked spot)
- Configured DNS. 
https://github.com/segunenix/AllScreenshots/blob/c7a5d21d84c0ea291128196cccc3757d7fac97f0/Screenshot%202025-08-17%20130409.png
- ADUC (Active Directory Users and Computers) Console.
https://github.com/segunenix/AllScreenshots/blob/bb7c5f760ae805ff8563682b6f58abc3cb389eb4/Screenshot%202025-08-17%20130638.png



### User & Group Management  
- Created organizational units (OU).  
https://github.com/segunenix/AllScreenshots/blob/30a21fde7aa8a8031655ad92fde743ede6351fb5/Screenshot%202025-08-17%20131747.png
(I created the organizational unit HR and IT)
- Added test users

- Grouped users for easier policy management.  

---

## Security Monitoring  

### Sysmon Installation  
- Installed Sysmon on both Windows machine with a custom config(olaf config).
https://raw.githubusercontent.com/olafhartong/sysmon-modular/master/sysmonconfig.xml  
- Generated logs for process creation, network connections, and registry changes.  

### Splunk Integration  
- Installed Splunk Enterprise on Ubuntu Server.  
- Installed Splunk Universal Forwarder on both Windows machines.  
- Configured forwarders to send Sysmon logs to Splunk.  
https://github.com/segunenix/AllScreenshots/blob/733864558f54ad11741e37cbe71b77c26327e13a/Screenshot%202025-08-17%20120613.png 

---

## Challenges & Fixes  
- **Problem:** Sysmon logs not showing in Splunk.  
  - **Fix:** Updated Splunk inputs.conf file (True and fales were suppose to be 1 and 0).  
https://github.com/segunenix/AllScreenshots/blob/feba2df3a6a32e609fed0620a104a319edb12547/Screenshot%202025-08-17%20121212.png
https://github.com/MyDFIR/Active-Directory-Project
- **Problem:** Splunk web interface not accessible.  
  - **Fix:** Confirmed service was running on port 8000.  


---

## Results  
- Successfully logged in with domain user accounts.  
https://github.com/segunenix/AllScreenshots/blob/8b980588e3ced3fc8c30581bc1d2f4d6294e5f4b/Screenshot%202025-08-17%20121647.png
- Sysmon logs collected and analyzed in Splunk.
https://github.com/segunenix/AllScreenshots/blob/feba2df3a6a32e609fed0620a104a319edb12547/Screenshot%202025-08-17%20120613.png

---

## Lessons Learned  
- Active Directory depends on DNS to function.  
- Group Policies are important for centralized security management.  
- Sysmon provides detailed telemetry for threat detection.  
- Splunk is effective for visualizing logs.  

--- 
