# 🧠 MISP – Malware Information Sharing Platform Cheat Sheet

---

## 🔍 What is MISP?

**[MISP](https://www.misp-project.org/)** is an open-source **Threat Intelligence Platform (TIP)** designed to collect, store, share, and correlate **Indicators of Compromise (IOCs)** related to:

- 🦠 Malware
- 🎣 Phishing
- 💳 Financial Fraud
- 🛡️ Cyber Attacks

It supports private, semi-private, and public threat-sharing communities.

---

## 🚀 Use Cases

- 🔬 Malware Reverse Engineering
- 🕵️ Security Investigations
- 🧠 Threat Intelligence & Adversary Tracking
- 👮 Law Enforcement & Forensics
- 📊 Risk Research
- 💰 Financial Fraud Detection

---

## ⚙️ Key Features

| Feature | Description |
|--------|-------------|
| 🧠 IOC Database | Store malware, attack, and threat-related data |
| 🔗 Correlation Engine | Connect events and attributes across campaigns |
| 🔁 Distributed Sharing | Supports granular sharing permissions |
| ⬇️ Import/Export | Compatible with formats like OpenIOC and ThreatConnect |
| 📡 API Integration | Automate ingestion and export of events |
| 🧬 Event Graph | Visualize relationships between indicators |

---

## 🧩 Key Terminologies

- **Events** – Container for grouped attributes and metadata  
- **Attributes** – Individual data points (e.g., IPs, hashes)  
- **Objects** – Groups of related attributes  
- **Tags & Taxonomies** – Classification for attributes/events  
- **Sightings** – Logs of observed IOCs  
- **Galaxies** – High-level threat actor or malware context  

---

## 🛠️ Event Management Workflow

1. **Create Event** – Add title, risk level, and sharing scope
2. **Add Attributes** – Input IOCs manually or in batch
3. **Attach Files** – Upload malware binaries or reports
4. **Tag with Taxonomies** – Enrich with standardized context
5. **Publish Event** – Submit for organizational or public visibility

---

## 🌐 Feeds & Tagging

- 🔄 **Feeds** – External threat data sources auto-updated into MISP
- 🏷️ **Tags** – Classify data and improve filtering
- 📚 **Taxonomies** – Use standard vocabularies like TLP, Confidence, Threat Level

### Tagging Best Practices

- Apply tags at **event level** unless exceptions apply.
- Use critical tags such as:
  - **TLP** (Traffic Light Protocol)
  - **Confidence**
  - **Origin**
  - **Permissible Actions Protocol**

---

## 🧰 Practical Use for SOC Analysts

SOC analysts use MISP to:

- 📥 Enrich alerts from SIEM with threat intel
- 🧠 Search IOCs to validate alerts
- 📡 Share validated threats across trusted communities
- 🤖 Automate IOC ingestion and distribution using APIs

Example: If a phishing domain is flagged in the SIEM, MISP can help verify if it has been previously seen or tagged malicious, and help track related IOCs.

![image](https://github.com/user-attachments/assets/14d60b35-61af-4bcc-964d-32132eb0b00a)
![image](https://github.com/user-attachments/assets/1268010e-2a90-4430-927a-c9a3af818393)
![image](https://github.com/user-attachments/assets/2f9be0ec-1b82-465a-b3d8-c6f5b4d10a63)

---

## 📚 Resources

- 📘 [MISP Book](https://www.misp-project.org/book/)
- 🛠️ [MISP GitHub](https://github.com/MISP/MISP)
- 🎓 [CIRCL MISP Training Module 1](https://www.circl.lu/doc/misp/)
- 🎓 [CIRCL MISP Training Module 2](https://www.circl.lu/doc/misp-training/)
- [View THM Room](https://tryhackme.com/room/misp)
- [THM Explanation](https://medium.com/@haircutfish/tryhackme-misp-task-4-feeds-taxonomies-task-5-scenario-event-task-6-conclusion-1eab9d364039)
