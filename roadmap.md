# 🧭 My Cybersecurity Learning Roadmap

## 🔹 Phase 1: Home Lab Setup (Now)
- [x] Install Wazuh Manager on Ubuntu
- [x] Connect Windows agent to Wazuh
- [x] Install Sysmon on Windows
- [ ] Enable File Integrity Monitoring
- [ ] Start analyzing logs from Wazuh dashboard
- [ ] Simulate simple attacks (e.g., PowerShell abuse)

---

## 🔹 Phase 2: Detection & Logging
- [ ] Create custom Wazuh rules
- [ ] Try Sigma rule format (convert one rule)
- [ ] Detect common Windows attacks (e.g., RDP brute force, suspicious parent-child)
- [ ] Set alerts for rare processes or command line flags
- [ ] Document each detection with notes and logs

---

## 🔹 Phase 3: Network Traffic + Threat Hunting
- [ ] Install and configure Wireshark
- [ ] Capture basic traffic samples (HTTP, FTP, SSH)
- [ ] Analyze PCAPs for anomalies
- [ ] Try out Zeek or Suricata for deeper visibility
- [ ] Start building detection rules from network data

---

## 🔹 Phase 4: Incident Simulation & Response
- [ ] Simulate phishing or malware download (lab-safe)
- [ ] Use Wazuh to respond and contain incidents
- [ ] Create a basic IR report template
- [ ] Write one full incident report from detection to resolution

---

## 📅 Bonus Goals (Stretch Targets)
- [ ] Start writing blog-style reports from your notes
- [ ] Learn MITRE ATT&CK and map your detections
- [ ] Try out tools like TheHive, MISP, or ELK stack
- [ ] Contribute to open source detection rules

---

## 📌 Notes

- This roadmap is flexible — I’ll update it as I learn more or switch focus.
- Check back for progress and new goals!
