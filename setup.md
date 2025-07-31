## Wazuh Setup Guide

This guide covers installing **Wazuh Manager** and **Wazuh Agent** in a home lab environment on the same machine.

---

## ✅ **Architecture Overview**
- **Wazuh Manager**: Collects, analyzes logs, and generates alerts.
- **Wazuh Agent**: Installed on endpoints to forward logs to the manager.

---

## 🔹 **Environment**
- **Manager OS**: Ubuntu 24.04.2 LTS (Server)
- **Agent OS**: Windows 11
- **Agent OS(second)**: Windows 11
- **Virtualization**: VirtualBox
- **Network**: NAT + Host-Only (for Internet and Manager-Agent communication)

---

## ✅ **Step 1: Update Your Manager**

```sudo apt update && sudo apt upgrade -y```

---

## ✅ **Step 2: Install Wazuh Manager**

```curl -sO https://packages.wazuh.com/4.x/wazuh-install.sh sudo bash wazuh-install.sh -a```


## ✅ **Step 3: Install Wazuh Agent(Both Windows)**
1. Download the installer from Wazuh Website.
2. During setup: Enter the Manager IP (Ubuntu system IP).
3. Start the Wazuh Agent service.


## ✅ **Step 4: Register the agent(Windows)**
On the Manager, 
1. run: sudo /var/ossec/bin/manage_agents
2. Add a new agent
3. Get the generated key.


## ✅ **Step 1: Verify Connection**
On the Manager dashboard:
You should see your agent listed as active.



