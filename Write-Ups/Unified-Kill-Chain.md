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
>
> ---
>
> 
# 🔗 Unified Kill Chain: A Holistic View on Threat Actor Behavior

The **Unified Kill Chain (UKC)** by Paul Pols is a comprehensive model capturing the lifecycle of targeted cyber intrusions. It aligns closely with the [MITRE ATT&CK framework](https://attack.mitre.org) and is structured into three primary phases: **IN**, **THROUGH**, and **OUT**.

---

## 🚪 Stage 1: IN — Initial Foothold

| #️⃣ | Phase | Description | Example | MITRE Technique |
|-----|-------|-------------|---------|-----------------|
| 1️⃣ | Reconnaissance | Gathering target information via OSINT or scanning. | Googling company email formats, using Shodan | [T1595](https://attack.mitre.org/techniques/T1595) |
| 2️⃣ | Resource Development | Setting up domains, malware, accounts. | Registering lookalike domains, creating fake LinkedIn profiles | [T1583](https://attack.mitre.org/techniques/T1583) |
| 3️⃣ | Delivery | Sending malware to target. | Phishing emails, malicious USB drops | [T1566](https://attack.mitre.org/techniques/T1566) |
| 4️⃣ | Social Engineering | Trick users into insecure actions. | Fake invoices, gift card scams | [T1598](https://attack.mitre.org/techniques/T1598) |
| 5️⃣ | Exploitation | Triggering vulnerabilities. | Exploiting unpatched Exchange Server | [T1203](https://attack.mitre.org/techniques/T1203) |
| 6️⃣ | Persistence | Maintaining long-term access. | Startup scripts, registry keys | [T1547](https://attack.mitre.org/techniques/T1547) |
| 7️⃣ | Defense Evasion | Avoiding detection. | Obfuscation, packed binaries, timestomping | [T1562](https://attack.mitre.org/techniques/T1562) |
| 8️⃣ | Command & Control | Remote control of compromised systems. | HTTPS-based C2, DNS Tunneling | [T1071](https://attack.mitre.org/techniques/T1071) |

---

## 🔄 Stage 2: THROUGH — Network Propagation

| #️⃣ | Phase | Description | Example | MITRE Technique |
|-----|-------|-------------|---------|-----------------|
| 9️⃣ | Pivoting | Using one system to reach others. | Using a compromised HR server to access Finance systems | [T1570](https://attack.mitre.org/techniques/T1570) |
| 🔟 | Discovery | Mapping the network and users. | Enumerating shares, netstat, AD queries | [T1087](https://attack.mitre.org/techniques/T1087) |
| 1️⃣1️⃣ | Privilege Escalation | Gaining elevated permissions. | Token impersonation, exploiting SUID bit | [T1068](https://attack.mitre.org/techniques/T1068) |
| 1️⃣2️⃣ | Execution | Running malicious code. | PowerShell scripts, scheduled tasks | [T1059](https://attack.mitre.org/techniques/T1059) |
| 1️⃣3️⃣ | Credential Access | Stealing login credentials. | Mimikatz, LSASS dumping | [T1003](https://attack.mitre.org/techniques/T1003) |
| 1️⃣4️⃣ | Lateral Movement | Expanding access across systems. | RDP, SMB, PsExec | [T1021](https://attack.mitre.org/techniques/T1021) |

---

## 📦 Stage 3: OUT — Action on Objective

| #️⃣ | Phase | Description | Example | MITRE Technique |
|-----|-------|-------------|---------|-----------------|
| 1️⃣5️⃣ | Collection | Gathering targeted data. | Screenshotting desktops, scraping databases | [T1119](https://attack.mitre.org/techniques/T1119) |
| 1️⃣6️⃣ | Exfiltration | Removing data from network. | Zip and FTP, cloud sync abuse | [T1041](https://attack.mitre.org/techniques/T1041) |
| 1️⃣7️⃣ | Impact | Causing disruption or destruction. | Encrypting files via ransomware | [T1486](https://attack.mitre.org/techniques/T1486) |
| 1️⃣8️⃣ | Objectives | Achieving end goals. | Financial extortion, espionage, disruption | [TA0040](https://attack.mitre.org/tactics/TA0040) |

---

## 🛡️ Using UKC for Defense

- Identify and strengthen defenses at early phases to reduce attacker success.
- Map alerts and logs to specific phases for better threat triage.
- Build detection, response, and recovery playbooks aligned to these phases.

> 📌 UKC helps defenders think like attackers — and act before attackers succeed.

