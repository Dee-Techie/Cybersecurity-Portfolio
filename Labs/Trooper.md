# 🕵️‍♂️ Trooper - CTI Investigation Lab

> **Goal**  
> Use Cyber Threat Intelligence knowledge and tools to investigate a real-world APT scenario targeting a multinational tech company.

---

## 📘 Scenario Overview

A multinational technology company has experienced multiple targeted cyber attacks. These attacks have resulted in the theft of sensitive intellectual property and disruptions to business operations.

A **threat advisory report** has been shared detailing similar attacks:
🔗 [TrendMicro Report](https://www.trendmicro.com/en_us/research/20/e/tropic-troopers-back-usbferry-attack-targets-air-gapped-environments.html)

As a **CTI Analyst**, your mission is to:

- Investigate the adversary's tactics, techniques, and procedures (TTPs)
- Use OpenCTI and MITRE ATT&CK Navigator to correlate threat data
- Identify threat actor identity, malware used, and associated tools

---

## 🛠️ Tools Used

- 🧠 [MITRE ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/)
- 🛰️ [OpenCTI](https://www.opencti.io/)

---

## 🧩 Investigation Tasks & Answers

| 💡 Question | ✅ Answer |
|------------|----------|
| What kind of phishing campaign does APT X use? | `Spear-phishing emails` |
| What is the name of the malware used by APT X? | `USBferry` |
| What is the malware's STIX ID? | `malware--5d0ea014-1ce9-5d5c-bcc7-f625a07907d0` |
| What technique did APT X use for initial access with USB? | `Replication through removable media` |
| What is the identity of APT X? | `Tropic Trooper` |
| Number of ATT&CK techniques linked on OpenCTI? | `39` |
| Tool linked to the APT? | `BITSAdmin` |
| Valid Accounts sub-technique used? | `Local Accounts` |
| Tactics for the above technique? | `Initial Access, Persistence, Defense Evasion, Privilege Escalation` |
| Known collection technique? | `Automated Collection` |

---

## 📸 Screenshots & Tool Output

Below are snapshots of the tools and resources used during analysis:

### 🔍 MITRE ATT&CK Navigator

![image](https://github.com/user-attachments/assets/ef619bc3-bc11-4c1c-9e3c-b4074c95b7ba)

---

### 📊 OpenCTI Analysis

![image](https://github.com/user-attachments/assets/f9affb9f-8ef8-4524-96ea-6f76bb794c3c)
![image](https://github.com/user-attachments/assets/ccfffb4a-45c4-4b78-a65d-345ad4191c15)
![image](https://github.com/user-attachments/assets/3367dc33-b740-4464-825c-594872516a61)

---

## 🧠 Lessons Learned

- 🧩 **Understanding TTPs**: Identifying an APT group's Tactics, Techniques, and Procedures is essential for proactive defense.
- 🧰 **Tool Synergy**: Using OpenCTI in conjunction with MITRE Navigator helps visualize and map threats with clarity.
- 🛡️ **Collection Techniques**: Adversaries like Tropic Trooper often leverage USB-based delivery and automated data collection — highlighting the importance of endpoint control and removable media policies.
- 🔐 **Account Misuse**: Valid account abuse (e.g., local accounts) spans multiple tactics, showing how privilege management and hardening are essential.
- 🧷 **STIX Format Usage**: Being able to reference malware by its **STIX ID** makes intelligence reporting more structured and interoperable.

---

## 📎 References

- [TrendMicro: Tropic Troopers Back USBferry Attacks](https://www.trendmicro.com/en_us/research/20/e/tropic-troopers-back-usbferry-attack-targets-air-gapped-environments.html)
- [MITRE ATT&CK](https://attack.mitre.org/)
- [OpenCTI](https://www.opencti.io/)
- [VirusTotal](https://www.virustotal.com/)

---

## 🧷 Tags

`#CTI` `#APT` `#TropicTrooper` `#MITRE` `#OpenCTI` `#TryHackMeLab` `#ThreatHunting` `#STIX`

