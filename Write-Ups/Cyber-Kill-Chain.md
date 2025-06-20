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
| 🔍 **Reconnaissance**  | Adversary gathers intel on the target (e.g., open ports, employees, services) |
| 💣 **Weaponization**   | Prepares malware, payloads, or exploits based on discovered vulnerabilities |
| ✉️ **Delivery**        | Sends malicious content via email, USB, phishing, drive-by downloads, etc.   |
| 💥 **Exploitation**    | Triggers the malicious code to exploit system vulnerabilities                |
| 📦 **Installation**    | Installs backdoors, malware, or tools for persistence                        |
| 🛰️ **Command & Control** | Establishes a remote connection to control the compromised system           |
| 🎯 **Actions on Objectives** | Executes final goals: data theft, encryption, sabotage, or lateral movement |

---

>Each stage is a point where defenders can detect and **interrupt the chain** before serious damage is done. 🔐

# 🔍 Reconnaissance

**Reconnaissance** is the first and foundational phase of the Cyber Kill Chain. It involves gathering intel about the target — whether it’s a person, system, or organization. This is the **planning phase** where attackers collect as much public information as possible before launching an attack. 🧠🕵️‍♂️

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

If defenders can **detect and limit OSINT exposure**, they can **break the kill chain early**. That’s why awareness of reconnaissance tactics is crucial for:
- SOC Analysts
- Threat Hunters
- Blue Teams
- Cybersecurity-aware employees 🛡️
