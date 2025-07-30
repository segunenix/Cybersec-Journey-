# 📊 Logs Analysis in Wazuh

This document explains how I analyzed alerts in Wazuh after connecting the agent. It includes my personal experience, the steps I followed, and the mapping to MITRE ATT&CK.

---

## ✅ My Experience
When I first connected the agent, I expected to see alerts immediately, but the dashboard was empty.  
I later learned that Wazuh only alerts when specific events occur. So I needed to **generate logs** manually by performing actions like:
- Entering wrong SSH credentials
- Modifying system files
- Running suspicious commands

This was the turning point for me in understanding **how Wazuh detection works**.

---

## ✅ Generating Test Events
To test the alerts, I triggered **SSH brute force attempts** on the Windows agent.

### **On the Agent (Windows)**
I ran this command in the powershell to simulate a brute force attack:
```bash
# Parameters
$UserName = "TestUser"
$WrongPasswords = @("password1","123456","admin","letmein","wrongpass","qwerty")
$Domain = $env:COMPUTERNAME

# Brute-force simulation
foreach ($pwd in $WrongPasswords) {
    Write-Host "Attempting login with password: $pwd"
    $result = (New-Object DirectoryServices.DirectoryEntry("WinNT://$Domain/$UserName,user",$UserName,$pwd)).psbase.Name
    Start-Sleep -Seconds 1
}
Write-Host "Simulation complete. Check Event Viewer (Security) for Event ID 4625."
```
![(simulated)Brute Force Command](Segundevsz/screenshots/blob/main/Screenshot%202025-07-30%20141011.png)
