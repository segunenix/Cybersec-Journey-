# 🔗 Connecting Wazuh Agent to Manager

---

## ✅ My Experience
When I first installed the agent through the application, it showed the status “Never connected” on my Wazuh Manager dashboard. I reinstalled it countless times and was very careful when entering the IP address, but nothing worked.
I struggled with this issue for about a week. I checked online for fixes but found nothing helpful. The logs always said:"unable to connect to the server".
I even changed protocols, thinking that was the problem—but it wasn’t.
Then one blessed day, it hit me: maybe the problem was with VirtualBox. After doing some research, I discovered that I needed to adjust the network settings by adding another network adapter. The correct setup was:
•Adapter 1 → NAT (for Internet connection)
•Adapter 2 → Host-only (for Wazuh Manager ↔ Agent communication)

That was the missing step! The issue happened because I’m running all my operating systems on a single machine. Wazuh manager was on my Ubuntu VM and the agent is my windows host machine.


---

## ✅ Correct Steps to Connect Agent
Note: Wazuh Agents can either be installed through GUI or CLI (depending on the OS). This is for Windows.
**Steps**
1. Download Wazuh agent software on the website.
2. Install it and input your manager IP address.
3. Start the agent.


