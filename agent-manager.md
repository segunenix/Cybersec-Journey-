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

**Steps**
1. Add a New Agent on Manager.
*Run the manage_agents tool:
```sudo /var/ossec/bin/manage_agents```
2. Copy the agent key.
3. Register the agent on the endpoint.
4. Start the agent.


