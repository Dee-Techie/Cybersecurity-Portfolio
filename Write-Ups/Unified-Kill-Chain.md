# 🔗 Unified Kill Chain: A Complete Look at Modern Cyber Attacks

The **Unified Kill Chain** expands on both the Cyber Kill Chain and MITRE ATT&CK to provide a more comprehensive map of modern adversary behavior. It categorizes the attack into three key stages: getting **In**, moving **Through**, and getting **Out**.

---

## 🚪 Stage 1: IN — Initial Foothold

| # | Attack Phase | Description |
|----|--------------|-------------|
| 1️⃣ | **Reconnaissance** | Researching and identifying targets via open-source or active scanning. |
| 2️⃣ | **Resource Development** | Setting up infrastructure like domains, malware, or fake identities. |
| 3️⃣ | **Delivery** | Sending the weaponized payload (e.g., phishing, infected USB). |
| 4️⃣ | **Social Engineering** | Tricking users into unsafe actions (e.g., clicking links). |
| 5️⃣ | **Exploitation** | Exploiting vulnerabilities to gain access to the system. |

---

## 🔄 Stage 2: THROUGH — Network Propagation

| # | Attack Phase | Description |
|----|--------------|-------------|
| 6️⃣ | **Persistence** | Gaining long-term access (e.g., registry keys, startup scripts). |
| 7️⃣ | **Defense Evasion** | Hiding from AV, EDR, or security monitoring tools. |
| 8️⃣ | **Command & Control** | Connecting compromised systems back to attacker. |
| 9️⃣ | **Pivoting** | Accessing additional systems via the initial compromise. |
| 🔟 | **Discovery** | Mapping the network and identifying further targets. |
| 1️⃣1️⃣ | **Privilege Escalation** | Gaining higher-level permissions (e.g., Admin, root). |
| 1️⃣2️⃣ | **Execution** | Running malicious commands or payloads. |
| 1️⃣3️⃣ | **Credential Access** | Harvesting login credentials from memory, files, etc. |
| 1️⃣4️⃣ | **Lateral Movement** | Moving through the network to other systems. |

---

## 📦 Stage 3: OUT — Action on Objective

| # | Attack Phase | Description |
|----|--------------|-------------|
| 1️⃣5️⃣ | **Collection** | Gathering sensitive data like PII, financial info, or IP. |
| 1️⃣6️⃣ | **Exfiltration** | Stealing and sending the data out of the network. |
| 1️⃣7️⃣ | **Impact** | Disrupting, destroying, or encrypting data (e.g., ransomware). |
| 1️⃣8️⃣ | **Objectives** | Achieving strategic goals like espionage, financial gain, or disruption. |

---

## 🎯 Summary

This structured kill chain helps organizations detect and respond earlier in the attack lifecycle. By breaking the chain at any stage — especially the “IN” phase — you dramatically reduce risk.

> 💡 Use this model to build threat detection rules, IR plans, and tabletop exercises.
