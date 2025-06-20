# 🔗 Cyber Kill Chain

The **Cyber Kill Chain®**, introduced by Lockheed Martin in 2011, is a cybersecurity framework adapted from a military attack structure. It outlines the **7 key phases** an adversary typically follows to execute a cyberattack. 🎯

Understanding the kill chain helps security professionals like **SOC Analysts, Threat Hunters, and Incident Responders** detect, disrupt, and respond to threats more effectively — especially **ransomware**, **APTs**, and **security breaches**. 🛡️

---

## 🧠 Why It Matters
- Helps identify gaps in your **security controls**
- Supports **threat modeling** and **incident response**
- Enhances ability to **anticipate and break attack chains**

---

## 🧱 The 7 Phases of the Cyber Kill Chain

| Phase              | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| 🔍 [**Reconnaissance**](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Cyber-Kill-Chain.md#-reconnaissance)  | Adversary gathers intel on the target (e.g., open ports, employees, services) |
| 💣 [**Weaponization**](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Cyber-Kill-Chain.md#%EF%B8%8F-weaponization)   | Prepares malware, payloads, or exploits based on discovered vulnerabilities |
| ✉️ **Delivery**        | Sends malicious content via email, USB, phishing, drive-by downloads, etc.   |
| 💥 **Exploitation**    | Triggers the malicious code to exploit system vulnerabilities                |
| 📦 **Installation**    | Installs backdoors, malware, or tools for persistence                        |
| 🛰️ **Command & Control** | Establishes a remote connection to control the compromised system           |
| 🎯 **Actions on Objectives** | Executes final goals: data theft, encryption, sabotage, or lateral movement |

---

>Each stage is a point where defenders can detect and **interrupt the chain** before serious damage is done. 🔐

# 🔍 Reconnaissance

**Reconnaissance** is the <ins>first and foundational phase</ins> of the Cyber Kill Chain. It involves gathering intel about the target — whether it’s a person, system, or organization. This is the **planning phase** where attackers collect as much public information as possible before launching an attack. 🧠🕵️‍♂️

---

## 🌐 What is OSINT?

[**OSINT**](https://www.varonis.com/blog/what-is-osint) (Open-Source Intelligence) refers to information collected from publicly available sources. This can include:
- Company websites
- Social media platforms (LinkedIn, Twitter, Facebook, Instagram)
- Employee names, emails, roles
- IP addresses, domains, technologies used

This helps attackers **profile the target** and **plan personalized attacks**, such as phishing or social engineering.

---

## 🎯 Attacker’s POV: Meet “Megatron”

Imagine an attacker named **Megatron**, planning a high-impact cyberattack. Before anything else, he needs to:
1. Identify a suitable target 🎯
2. Collect background info using OSINT 🌐
3. Harvest emails for phishing attempts 📧
4. Study social media for insights on employees 🕸️

---

## 🛠️ Reconnaissance Tools

| Tool           | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| 🔎 theHarvester | Gathers emails, names, subdomains, IPs, and URLs from public sources        |
| 🧑‍💼 Hunter.io     | Finds email addresses linked to a domain — great for phishing prep         |
| 🧰 [OSINT Framework](https://osintframework.com/) | Curated collection of OSINT tools categorized by type (social, technical) |

---

## ⚠️ Why It Matters

🛡️ If defenders(Blue team, SOC analyst) can **detect and limit OSINT exposure**, they can **break the kill chain early**.


---

## ⚔️ Weaponization

Once our adversary completes his Reconnaissance mission, he moves on to crafting his digital weapon. This stage — **Weaponization** — is all about <ins>creating or acquiring a **malicious payload** that can exploit the target’s system</ins> without needing direct interaction. Think of it as assembling a high-tech trap. 🪤💻

---

### 🧠 What happens during Weaponization?

According to Lockheed Martin’s Cyber Kill Chain framework, Weaponization is the phase where attackers:
- Combine **malware** (malicious software) and an **exploit** (code that takes advantage of a vulnerability),
- Wrap them into a **payload** (the actual code that runs on the victim’s system),
- And prepare this weapon for delivery (usually via email, USB, websites, or other means).

---

### 💡 Example Scenario

Megatron decides he doesn’t want to write malware from scratch. So, he:
- Buys a pre-built malicious payload from the [**Dark Web**](https://www.kaspersky.com/resource-center/threats/deep-web) 🕶️,
- Embeds it into a Microsoft Word document using a **malicious macro**, and
- Prepares the document for email delivery as part of a phishing campaign.
---

## 💻 Real-World Examples of Weaponization

Attackers may choose different weaponization strategies depending on their skills, budget, and target. For example:

### 📝 Infected Documents
Creating malicious Microsoft Office documents with embedded:
- Macros (e.g., VBA scripts)
- Links to dropper files
- Auto-executing malware when opened

> 📚 Learn more: [Intro to Macros and VBA for Script Kiddies by TrustedSec](https://www.trustedsec.com)

### 🧬 Custom Payloads
Advanced attackers — like **APT groups** — may:
- Write custom malware to bypass detection
- Use **packers**, **crypters**, or **obfuscation** to avoid AV/EDR
- Combine remote access tools (RATs) and shellcode loaders

### 🕵️ Buying From the Dark Web
Less-skilled attackers often purchase:
- Ready-made malware kits
- 0-day exploits
- [C2](https://attack.mitre.org/tactics/TA0011/) frameworks (e.g., Cobalt Strike, Sliver)

---

## 🔌 Weaponization Techniques

Weaponization isn’t just about writing malware — it's about **delivery strategy**:

| 🧰 Technique                         | Description |
|-------------------------------------|-------------|
| 📨 Malicious Email Attachments       | Infected Word, Excel, PDF files with auto-run code |
| 💾 USB Malware Implantation          | Dropping infected USB drives in public areas |
| 🌐 Drive-by Downloads                | Exploiting unpatched browsers via malicious sites |
| 🧬 Custom Malware                    | Creating or modifying malware to evade AV/EDR detection. |
| 🛒 Dark Web Payloads                 | Buying exploits, malware kits, or RATs like NjRAT or Quasar. |
| 📡 Command & Control (C2) Setup      | Pre-configuring infrastructure to control the victim's machine remotely (via Botnets, zombies, etc.) |
| 🔙 Backdoor Implantation             | Installing persistent access to bypass authentication later |

---

### 🛡️ Why This Phase Matters for Defenders

Detecting Weaponization is tricky because it usually happens **before the malware reaches your network**. However, defenders can still:

- Use **sandboxing** to analyze file behavior,
- Block **macro-enabled documents** from untrusted sources,
- Implement **email filtering** and **URL rewriting**,
- Use **YARA rules** to detect known malicious patterns.

Weaponization is the attacker’s blueprint phase — preparing the digital tools needed to exploit a target. It doesn’t involve interaction yet, but it sets the stage for Delivery and Exploitation. Understanding how attackers weaponize payloads helps us all 💪.

---



