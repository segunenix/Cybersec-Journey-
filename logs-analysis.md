# 📊 Logs Analysis in Wazuh

This document explains how I analyzed alerts in Wazuh after connecting the agent. It includes my personal experience and the steps i followed.

---

## ✅ My Experience
Not gonna lie, my experiece here was quite smooth. I didnt have any problems.

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
https://github.com/segunenix/AllScreenshots/blob/05f3de61764c2903a7190bd15b0a231a69ce76a2/Screenshot%202025-07-30%20141011.png

## ✅ On The Agent

https://github.com/segunenix/AllScreenshots/blob/05f3de61764c2903a7190bd15b0a231a69ce76a2/Screenshot%202025-07-30%20105840.png

## ✅ Viewing Alerts in the Wazuh Dashboard

https://github.com/segunenix/AllScreenshots/blob/05f3de61764c2903a7190bd15b0a231a69ce76a2/Screenshot%202025-07-29%20201104.png

