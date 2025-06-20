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
| ✉️ [**Delivery**](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Cyber-Kill-Chain.md#-delivery)        | Sends malicious content via email, USB, phishing, drive-by downloads, etc.   |
| 💥 [**Exploitation**](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Cyber-Kill-Chain.md#-exploitation)    | Triggers the malicious code to exploit system vulnerabilities                |
| 📦 [**Installation**](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Cyber-Kill-Chain.md#%EF%B8%8F%EF%B8%8F-installation)    | Installs backdoors, malware, or tools for persistence                        |
| 🛰️ [**Command & Control**](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Cyber-Kill-Chain.md#-command--control-c2) | Establishes a remote connection to control the compromised system           |
| 🎯 [**Exfilteration-Actions on Objectives**](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Cyber-Kill-Chain.md#-exfiltration---actions-on-objectives) | Executes final goals: data theft, encryption, sabotage, or lateral movement |

---

>Each stage is a point where defenders can detect and **interrupt the chain** before serious damage is done. 🔐

# 🔍🔍 Reconnaissance

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

## 🛠️🛠️ Reconnaissance Tools

| Tool           | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| 🔎 theHarvester | Gathers emails, names, subdomains, IPs, and URLs from public sources        |
| 🧑‍💼 Hunter.io     | Finds email addresses linked to a domain — great for phishing prep         |
| 🧰 [OSINT Framework](https://osintframework.com/) | Curated collection of OSINT tools categorized by type (social, technical) |

---

## ⚠️ Why It Matters

🛡️ If defenders(Blue team, SOC analyst) can **detect and limit OSINT exposure**, they can **break the kill chain early**.


---

## ⚔️⚔️ Weaponization

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

## 🔌🔌 Weaponization Techniques

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

## 📦📦 Delivery

Now that **Megatron** 🦾 has built his weapon in the Weaponization phase, it’s time to <ins>deliver the malicious package</ins> to his target. The **Delivery** phase is where the attacker **transmits the payload** to the victim — and it’s one of the first points where defenders can actively **intervene**! 🚫🛡️

---

### 🧠 What happens during Delivery?

This phase is all about choosing **how** to get the malware into the hands (or machines) of the victims. Megatron has multiple options — each with different levels of stealth, complexity, and effectiveness.

---

### 📬 Common Delivery Methods

| 🚀 Method                     | 📝 Description |
|------------------------------|----------------|
| ✉️ **Phishing Emails**        | Sending emails with malicious attachments or links — sometimes targeted (spearphishing). |
| 🔌 **USB Drop Attacks**       | Leaving infected USB drives in public or mailing them with fake branding. |
| 🌐 **Watering Hole Attacks**  | Compromising a trusted website visited by the target and injecting malware. |
| 📎 **Malicious Attachments**  | Sending infected PDFs, Office docs, or zipped executables. |
| 📲 **Malicious Mobile Apps**  | Uploading malware-laden apps to app stores or sideloaded channels. |

---

### 💻 Example: Spearphishing in Action

Megatron finds out via LinkedIn that **Nancy** in Sales frequently interacts with **Scott** from another company. He creates a fake email that appears to come from Scott — using a similar-looking domain — and sends Nancy a convincing invoice attachment. 📄📧

The attachment contains Megatron’s payload, masked as a legitimate document. One careless click, and boom — malware is delivered! 💥

---

### ☠️ USB Drop Example

In a more "hands-on" approach, Megatron:
- Prints USBs with Company A’s logo 🖨️,
- Loads them with malware disguised as marketing material,
- Mails them with a handwritten note saying “Thanks for your partnership! 🎁”

Curiosity kills the cat... and the network.

🔗 **Real Case**: [Cybercriminals mailing USB drives](https://www.csoonline.com/article/3644094/cybercriminal-group-mails-malicious-usb-dongles-to-targeted-companies.html) pretending to be gifts. 🚚💣

---

### 🌐 Watering Hole Attack Explained

In this method:
- Megatron targets a **trusted website** frequently visited by Company A employees,
- Exploits a vulnerability to inject malicious code,
- Sends out emails with a “harmless” link to the site.

Once users visit, malware is downloaded without their knowledge — a **drive-by download**. 🕳️🦠

Example: A fake browser update popup appears on the site, urging the user to install a malicious “extension.” 🧩

---

### 🛡️ Defensive Tips

You can block attacks during the Delivery phase by:
- 🧼 Training employees to spot phishing
- 📥 Blocking suspicious file types at email gateways
- 💽 Disabling auto-run on USB ports
- 🔍 Using secure web gateways & DNS filtering
- 🛑 Monitoring web traffic for redirection and anomalies

---

The **Delivery** phase is the adversary's first real attempt to reach their target. Whether through clever phishing, rogue USBs, or poisoned websites, the goal is always the same: **get the malware onto the system**.

Defenders can make this step difficult by:
- Educating users 🙋‍♀️
- Filtering emails 📤
- Isolating threats early 🔒

---

## 💥💥 Exploitation

Once the malicious payload is delivered, it’s time for the attacker to **break in**! 🛠️ This is where "Megatron" moves from planning to **action**.

### 🎯 What Happens in This Phase?

The attacker exploits a **vulnerability** to execute malicious code on the victim’s system. This is the point where delivery turns into damage.

Megatron, our villain, went with two attacks:
- 📩 A phishing email with a **fake Office 365 login page**.
- 📎 Another with a **macro-enabled document** that launches ransomware when opened.

Both tricks worked — victims clicked, and now the system is compromised. 😬

---

### 🚪 Types of Exploits Used:
- **Email-based**: Victims open attachments or click phishing links.
- **Zero-Day Exploits**: 🕳️ Vulnerabilities unknown to the vendor. These are especially dangerous as there's **no patch or signature** yet.
- **System/Software Exploits**: Bugs in outdated or unpatched software.
- **Web Vulnerabilities**: SQLi, XSS, RCE — common in poorly secured web apps. Learn more in the [OWASP Top 10](https://tryhackme.com/room/owasptop10) room on TryHackMe.

---

### 🧗 Next Steps for the Attacker:
Once inside, Megatron might:
- Use **privilege escalation** techniques to gain admin rights 🔑
- Move laterally across the network (think: from one compromised machine to another) 🔄
- Steal credentials, maintain persistence, or install more payloads 👀

> 🛡️ **Tip for Defenders:** Detection is critical here. Endpoint Detection & Response (EDR), email filtering, sandboxing, and patch management can all stop Megatron in his tracks!

---

### 📚 Related Concepts:
- **Lateral Movement**: Moving within the network after gaining access. Often done using stolen credentials or remote tools.
- **Social Engineering**: Exploiting human trust is as effective as exploiting code.
- **Payload Execution**: This is when the malicious code actually runs.

🧠 Knowing how exploitation works helps defenders stop attacks before they escalate.

---

## 🛠️🛠️ Installation

After breaking in, the attacker needs a way to **stay in** — even if the system reboots or patches are applied. That’s where **persistence** comes in.

### 🚪 What’s a Backdoor?

A **backdoor** is an access point that allows attackers to bypass authentication and sneak back into a compromised system anytime they want — like having a hidden spare key under the mat. 🗝️

"**Megatron**" doesn’t want to lose access if the system gets rebooted or the initial exploit is removed. So, he installs a **persistent backdoor** to maintain access.

---

### 🔁 How Persistence is Achieved:

- **🕸️ Web Shells**  
  Malicious scripts (like `.php`, `.asp`, `.jsp`) uploaded to a web server to execute commands remotely.  
  ⚠️ These are often hard to detect and blend in as harmless files.

- **💻 Backdoors via Meterpreter**  
  A Metasploit payload that gives full remote control. Attackers can install it quietly and use it interactively.

- **🔧 Windows Services Modification (T1543.003)**  
  Adversaries create or tamper with Windows services to run their malware consistently.  
  They might name them something legit-sounding like `SystemUpdateService.exe` to avoid suspicion.

- **🗝️ Registry Run Keys & Startup Folder (T1547.001)**  
  Attackers add entries to ensure the malicious payload runs at login — for every user, every time.

- **🕒 Timestomping**  
  Modify file timestamps (created, modified, accessed) to blend malicious files with legitimate ones and avoid forensic detection.

---

### 🧠 Learn More:
- Explore [Windows Persistence Techniques](https://tryhackme.com/room/windowsinternals9) on TryHackMe.
- See [Microsoft’s guide on web shell attacks](https://www.microsoft.com/security/blog/2020/06/25/web-shell-attacks-a-walk-through-of-the-latest-threats/) for real-world insights.
- Browse [MITRE ATT&CK](https://attack.mitre.org) for more tactics like T1543 and T1547.

> 🔐 **Pro Tip**: Use EDR tools and regularly audit startup items and services to catch hidden persistence tricks.

Persistence isn’t just sneaky — it’s critical for an attacker to maintain long-term access. Detecting and removing it early can break their entire plan! 🚫👣

---

## 🎮🎮 Command & Control (C2)

Now that "Megatron" has persistence, it’s time to **take control**.  
Welcome to the **Command & Control** phase — where malware phones home. ☎️💀

---

### 🧠 What is C2?

**Command & Control (C2)** — also known as C&C/C2 **Beaconing** — refers to the communication between an attacker’s server and the compromised system.

- The infected host "beacons" back to the attacker's server.
- Once connected, the attacker can run commands, exfiltrate data, install more malware, or move laterally across the network.

---

### 🌐 C2 in Action

After persistence, Megatron’s malware opens a channel to a C2 server — think of it like malware calling its boss for orders. 📡

Traditionally, attackers used **IRC (Internet Relay Chat)** as their channel, but that’s outdated and easily detected.

### 🔌 Common C2 Channels Today

- **🛰️ HTTP/HTTPS (Ports 80 & 443)**  
  This is the **most common method** — blends in with regular web traffic, making it stealthy.  
  Firewalls often let it through unless deep packet inspection is used.

- **🌐 DNS Tunneling**  
  The malware disguises its data as DNS queries.  
  These frequent, tiny requests fly under the radar.  
  Example: Instead of `update.software.com`, the malware might query something like `a1b2c3.attacker.com`.

> 🛡️ *Why it matters*: These covert communication paths are how attackers control your system **after initial compromise** — detecting and cutting them off is vital to break the kill chain!

---

### 👁️‍🗨️ Who Owns the C2?

- The attacker could be directly operating the C2 infrastructure
- Or they might route it through another **compromised system** — making attribution harder.

---

### 🧰 Detect & Defend

- Monitor for **unusual beaconing patterns** (regular intervals, odd hours)
- Analyze DNS logs for **suspicious queries**
- Use EDR/XDR tools to track **outbound connections** from endpoints
- Deploy **network segmentation** to limit lateral movement

> 🔒 Cutting off C2 = cutting off the attacker’s control 🎯

---

## 🎯🎯 Exfiltration - Actions on Objectives

After climbing every stage of the Cyber Kill Chain, **"Megatron"** is finally ready to achieve what he came for — his ultimate goals. 🧑‍💻💣

---

### 💼 What Happens Here?

This is the final phase where attackers **act on their intent** — whether it's theft, destruction, or disruption.

With hands-on-keyboard access, the attacker can now:

- 🔐 **Steal credentials** (usernames, passwords, tokens)
- 🧱 **Escalate privileges** to gain elevated access (e.g. Domain Admin)
- 🕵️‍♂️ **Conduct internal reconnaissance** to map out the network or find more vulnerabilities
- 🔁 **Move laterally** through other systems or departments
- 📤 **Exfiltrate sensitive data** (e.g. intellectual property, customer info, source code)
- 🧹 **Delete backups and Shadow Copies** to prevent recovery
- 🧨 **Corrupt or overwrite critical data** to cause maximum damage

> ☠️ *This is where the attacker cashes in on all the previous steps.*

---

### 🛡️ Defenders, Pay Attention!

To defend against this phase, security teams should:

- Monitor for **data egress anomalies** (large outbound transfers, encryption)
- Use **DLP (Data Loss Prevention)** tools
- Restrict sensitive systems with **network segmentation**
- Log and alert on **Shadow Copy deletions or backup tampering**
- Enforce **least privilege access** across the network

> 🎓 *If you've detected the attack at this phase — it may already be too late. The best defense is stopping the attack much earlier in the chain.*


---

<sub>🔗 References & Resources:
TryHackMe — Cyber Kill Chain | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/cyberkillchainzmt)</sub>
