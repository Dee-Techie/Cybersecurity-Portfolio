# 🔗 Unified Kill Chain: A Complete Look at Modern Cyber Attacks

The **[Unified Kill Chain](https://www.unifiedkillchain.com/assets/The-Unified-Kill-Chain.pdf) (UKC)** by Paul Pols is a comprehensive model capturing the lifecycle of targeted cyber intrusions. It aligns closely with the [MITRE ATT&CK framework](https://attack.mitre.org) and is structured into three primary phases: **IN**, **THROUGH**, and **OUT**.

---

## 🚪 Stage 1: IN — Initial Foothold

| #️⃣ | Phase | Description | Example | MITRE Technique |
|-----|-------|-------------|---------|-----------------|
| 1️⃣ | Reconnaissance | Gathering target information via OSINT or scanning. | Googling company email formats, and other exposed services using Shodan | [T1595](https://attack.mitre.org/techniques/T1595) |
| 2️⃣ | Resource Development | Setting up attacker infrastructure (domains, malware, accounts). | Registering lookalike domains, creating fake LinkedIn profiles | [T1583](https://attack.mitre.org/techniques/T1583) |
| 3️⃣ | Delivery | Transmitting weaponized payload (malware) to target. | Phishing emails, malicious USB drops | [T1566](https://attack.mitre.org/techniques/T1566) |
| 4️⃣ | Social Engineering | Trick users into insecure actions. | Fake invoices, gift card scams, support calls | [T1598](https://attack.mitre.org/techniques/T1598) |
| 5️⃣ | Exploitation | Triggering vulnerabilities - Exploiting vulnerabilities to execute code. | Exploiting unpatched Exchange Server, Log4Shell or outdated plugins | [T1203](https://attack.mitre.org/techniques/T1203) |
| 6️⃣ | Persistence | Maintaining long-term access after initial intrusion. | Startup scripts, registry keys, backdoors | [T1547](https://attack.mitre.org/techniques/T1547) |
| 7️⃣ | Defense Evasion | Avoiding detection and maintaining stealth. | Obfuscation, packed binaries, timestomping | [T1562](https://attack.mitre.org/techniques/T1562) |
| 8️⃣ | Command & Control | Establishing remote communication. | HTTPS-based C2, DNS Tunneling | [T1071](https://attack.mitre.org/techniques/T1071) |

---

## 🔄 Stage 2: THROUGH — Network Propagation

| #️⃣ | Phase | Description | Example | MITRE Technique |
|-----|-------|-------------|---------|-----------------|
| 9️⃣ | Pivoting | Using one compromised system to reach others. | Using a compromised HR server to access Finance systems | [T1570](https://attack.mitre.org/techniques/T1570) |
| 🔟 | Discovery | Identifying/Mapping the systems, network and users. | Enumerating shares, netstat, AD queries | [T1087](https://attack.mitre.org/techniques/T1087) |
| 1️⃣1️⃣ | Privilege Escalation | Gaining elevated (e.g. Admin) permissions. | Token impersonation, exploiting SUID bit | [T1068](https://attack.mitre.org/techniques/T1068) |
| 1️⃣2️⃣ | Execution | Running malicious code on local or remote systems. | PowerShell scripts, scheduled tasks | [T1059](https://attack.mitre.org/techniques/T1059) |
| 1️⃣3️⃣ | Credential Access | Stealing login credentials. | Mimikatz, LSASS dumping | [T1003](https://attack.mitre.org/techniques/T1003) |
| 1️⃣4️⃣ | Lateral Movement | Expanding access across systems. | RDP, SMB, PsExec | [T1021](https://attack.mitre.org/techniques/T1021) |

---

## 📦 Stage 3: OUT — Action on Objective

| #️⃣ | Phase | Description | Example | MITRE Technique |
|-----|-------|-------------|---------|-----------------|
| 1️⃣5️⃣ | Collection | Gathering targeted data. | Dumping DBs, Screenshotting desktops, scraping databases, copying PII | [T1119](https://attack.mitre.org/techniques/T1119) |
| 1️⃣6️⃣ | Exfiltration | Removing data from network. | Zip and FTP to external server, cloud sync abuse | [T1041](https://attack.mitre.org/techniques/T1041) |
| 1️⃣7️⃣ | Impact | Causing disruption or destruction. | Encrypting files via ransomware, defacement | [T1486](https://attack.mitre.org/techniques/T1486) |
| 1️⃣8️⃣ | Objectives | Achieving end goals. | Financial extortion, espionage, disruption | [TA0040](https://attack.mitre.org/tactics/TA0040) |

---

## 🛡️ Using UKC for Defense

- Identify and strengthen defenses at early phases to reduce attacker success.
- Map alerts and logs to specific phases for better threat triage.
- Build detection, response, and recovery playbooks aligned to these phases.

> 📌 UKC helps defenders think like attackers — and act before attackers succeed.


---

## 🎯 Summary

This structured kill chain helps organizations detect and respond earlier in the attack lifecycle. By breaking the chain at any stage — especially the “IN” phase — you dramatically reduce risk.

> 💡 Use this model to build threat detection rules, IR plans, and tabletop exercises.

