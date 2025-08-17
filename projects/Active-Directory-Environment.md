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
- Assigned static IPs:  
  - `192.168.10.7` → Windows Server (Domain Controller)  
  - `192.168.10.100` → Windows 11 Client  
  - `192.168.10.10` → Ubuntu Server (Splunk Enterprise)  

### Domain Controller Setup  
- Installed AD DS role on Windows Server.  
- Promoted server to Domain Controller.  
- Configured DNS and DHCP.  

### User & Group Management  
- Created organizational units (OU).  
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
- Created dashboards to monitor authentication events and system activity.  

---

## Challenges & Fixes  
- **Problem:** Sysmon logs not showing in Splunk.  
  - **Fix:** Updated Splunk inputs.conf file (True and fales were suppose to be 1 and 0).  
https://github.com/MyDFIR/Active-Directory-Project
- **Problem:** Splunk web interface not accessible.  
  - **Fix:** Allowed firewall rules, confirmed service was running on port 8000.  

*(add more as you go along)*  

---

## Results  
- Successfully logged in with domain user accounts.  
- Sysmon logs collected and analyzed in Splunk.  
- Built a Splunk dashboard to visualize security events.  

*(insert screenshots from `/screenshots/` folder here)*  

---

## Lessons Learned  
- Active Directory depends on DNS to function.  
- Group Policies are important for centralized security management.  
- Sysmon provides detailed telemetry for threat detection.  
- Splunk is effective for visualizing logs.  

--- 
