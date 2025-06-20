# 🧗 Pyramid of Pain</br>
Not all indicators are created equal; some of them are far more valuable than others.

The Pyramid of Pain helps security teams prioritize their resources. Instead of chasing easily changeable indicators like hashes and IPs (which leads to a constant, reactive game of "whack-a-mole"), it encourages focusing on detecting and disrupting higher-level indicators.

<img src="https://github.com/user-attachments/assets/06bed36b-db06-4dfc-9442-62828687908d" alt="Pyramid of Pain" width="500" /></br>

The **Pyramid of Pain**, introduced by David Bianco in 2013, ranks indicators by how much **“pain”** they cause adversaries when detected. Higher layers force attackers to spend more time, money, and skill to reinvent their attacks. 🧩🚧

---

## 🔐 1. Hash Values (Trivial)

- **What?** File fingerprints (MD5, SHA-1, SHA-256).  
- **Defender tools:** VirusTotal, OPSWAT Metadefender, SIEM ingestion. 
- **Why attackers don’t care:** Change a byte, get a new hash. Polymorphic malware makes this trivial.
- **💡 Tip:** Use YARA rules for stronger detection beyond static hashes.

### Practical Example : 
- Attack: SilentShadow sends a phishing email with an attachment that, when opened, drops their silent_shadow_v1.exe ransomware executable.
- Your Detection: Your antivirus (AV) system has a signature for the hash value of silent_shadow_v1.exe. It detects and quarantines the file on the first workstation that       attempts to open it.
- Adversary's "Pain": Trivial. SilentShadow learns that silent_shadow_v1.exe is detected. They simply recompile their ransomware with a tiny, irrelevant code change,   generating silent_shadow_v2.exe. This new file has a different hash, bypassing your current AV signature. They send out new phishing emails. You've blocked one instance, but they're back in minutes.

---

## 🌐 2. IP Addresses (Easy)

- **What?** Malicious IPs or subnets.  
- **Defender gain:** Quick blocks via firewalls or TIPs (e.g., Recorded Future, Anomali).
- **Attacker trick:** IP rotation, cloud proxies, [Fast Flux](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Pyramid-of-Pain.md#glossary) DNS.
- **Use case:** Sandboxes like ANY.RUN reveal dynamic IP behavior.
<img src="https://github.com/user-attachments/assets/30cb980c-c292-4c00-807c-45a9c53c63a6" alt="Domain/IP Reports" width="1350" /></br>

### Practical Example : 
- Attack: SilentShadow's ransomware (now silent_shadow_v2.exe) successfully executes on a user's machine. It then attempts to connect to their Command and Control (C2) server at 192.168.1.100 to register the infection and receive encryption keys.
- Your Detection: Your firewall logs show a connection attempt to 192.168.1.100. You block this IP address at the firewall level.
- Adversary's "Pain": Easy. SilentShadow realizes their 192.168.1.100 server is blocked. They simply spin up a new C2 server on a different cloud provider or compromised host, say 10.0.0.50. They update their ransomware to connect to the new IP. Again, a quick fix for them.
---

## 🌍 3. Domain Names (Simple)

- **What?** Malicious domains or subdomains to run typo-squatting campaigns.
- **Defender gain:** Block domains, sinkhole them, analyze proxy logs.  
- **Attacker trick:** Punycode spoofing (e.g., `xn--addas-o4a.de` → looks like `adidas.de`), URL shorteners (`bit.ly+` preview).

### Practical Example : 
- Attack: SilentShadow, annoyed by your IP blocking, decides to use a more resilient C2 mechanism. Their silent_shadow_v3.exe variant now uses a randomly generated domain name like malicious-c2-xyz123.com to communicate with their server, resolving to various IPs.
- Your Detection: Your network intrusion detection system (NIDS) observes a suspicious DNS query to malicious-c2-xyz123.com. You quickly add this domain to your blacklists on your DNS firewall.
- Adversary's "Pain": Simple. Registering new domains takes a bit more effort than changing IPs, but SilentShadow has automated tools for domain generation (DGA) and rapid registration. They register malicious-c2-abc456.com and push an update to their ransomware. It's an inconvenience, but not a showstopper.
---

## 🖥️ 4. Host Artifacts (Annoying)

- **What?** Malware artifacts on endpoints — registry keys, dropped files, strange processes (e.g. Word→PowerShell).  
- **🤖 Defender Tools:** EDR, SIEM, Process Monitor, Log analysis.  
- **Attacker pain:** They must change tooling or behavior; more work and cost.

<img src="https://github.com/user-attachments/assets/9b329f95-366b-4047-9444-692c02be78b0" alt="Host Artifacts Report 1" width="500" /></br>

<img src="https://github.com/user-attachments/assets/d83133c0-c189-44d3-a01d-4d8a7c58f6f4" alt="Host Artifacts Report 2" width="500" /></br>

### Practical Example : 
- Attack: SilentShadow's ransomware has successfully encrypted some files. To maintain persistence and hide its tracks, it creates a specific registry key: HKCU\Software\SilentShadow\Persistence. It also uses a unique network traffic pattern: small, encrypted UDP packets on port 4444.
- Your Detection: Your endpoint detection and response (EDR) system identifies the creation of HKCU\Software\SilentShadow\Persistence. Your network monitoring tools detect the unusual UDP traffic on port 4444. You configure your EDR to alert on this registry key and your firewall to block UDP 4444.
- Adversary's "Pain": Annoying. Now SilentShadow has to start changing more than just network addresses or file hashes. They need to modify their code to use a different registry key location or a different network protocol/port. This takes more development time and might disrupt their established tooling or processes. They're still effective, but you're making them work for it.
---

## 🌐 5. Network Artifacts (Annoying)

- **What?** Behavioral network indicators — unusual HTTP POST [URIs](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Pyramid-of-Pain.md#glossary), custom user‑agents, [C2](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Pyramid-of-Pain.md#glossary) patterns. An attacker might use a User-Agent string that hasn’t been observed in your environment before or seems out of the ordinary. The User-Agent is defined by [RFC2616](https://datatracker.ietf.org/doc/html/rfc2616#page-145) as the request-header field that contains the information about the user agent originating the request.
- **Detect with:** PCAP analysis (Wireshark/TShark), IDS/IPS signatures (Snort, Suricata).  
- **Why it hurts:** Attackers need to re-engineer their comms, so detection gains you time.
- P.S. If you can detect the custom User-Agent strings that the attacker is using, you might be able to block them, creating more obstacles and making their attempt to compromise the network more annoying.👿😤

### Practical Example : 
- Attack: After analyzing the silent_shadow_vX.exe samples, your incident response team discovers that SilentShadow is consistently using a custom-built, open-source tool called "ShadowSpray" for network scanning and lateral movement within your internal network before deploying the ransomware. ShadowSpray has specific command-line arguments and file names it leaves behind.
- Your Detection: You develop EDR rules that specifically detect the execution patterns of "ShadowSpray," its common command-line arguments, and its unique file drops. Your security team actively hunts for these tool-specific indicators.
- Adversary's "Pain": Challenging. SilentShadow now has a significant problem. Their tried-and-true lateral movement tool, "ShadowSpray," is being detected. They can't just change an IP; they have to either:
  - Find a completely new, comparable tool (which might be expensive or less effective).
  - Develop a new custom tool from scratch (very time-consuming and costly).
  - Heavily modify "ShadowSpray" to obscure its unique characteristics, which again requires significant development effort. You've severely hampered their ability to move   within your network, forcing them to re-evaluate their entire reconnaissance and lateral movement phase.
---

## 🛠️ 6. Tools (Challenging)

- **What?** The actual malware and scripts — backdoors, stegomalware, credential dumpers.  
- **Why it hurts:** Custom-built tools force them to rebuild or abandon their arsenal.
- **Defender strategies:**
  - YARA rules, antivirus/EDR signatures  
  - [Fuzzy hashing](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Pyramid-of-Pain.md#glossary) (SSDeep) to detect modified malware.
  - Use feeds like MalwareBazaar, Malshare, SOC Prime TDM.  
- **Real-world context:** SentinelOne & Cisco enhance CTI by hunting behaviors, not just signatures.

### Practical Example : 
- Attack:  Your security team, through meticulous analysis of multiple SilentShadow incidents (both against your company and others), identifies their overarching TTPs:
  - Initial Access: Phishing with malicious documents, followed by exploiting a specific vulnerability (e.g., "drive-by download via macro-enabled document").
  - Execution: Using powershell.exe to download secondary payloads, often obfuscated.
  - Persistence: Creating scheduled tasks disguised as legitimate system processes.
  - Lateral Movement: Using PsExec or WMI to move between systems.
  - Defense Evasion: Deleting event logs.
  - Exfiltration (Pre-Ransomware): Using BITSAdmin to transfer small files to cloud storage before encryption.
- Your Detection & Prevention: You implement comprehensive security controls and monitoring designed to detect these TTPs, regardless of the specific malware or tool being used:
  - Blocking macro execution from untrusted sources.
  - Monitoring all powershell.exe activity for suspicious command lines.
  - Alerting on suspicious scheduled task creation.
  - Implementing strong segmentation to limit lateral movement.
  - Detecting attempts to clear event logs.
  - Monitoring BITSAdmin usage for unusual exfiltration.
- Adversary's "Pain": Highest. SilentShadow's entire modus operandi is now compromised. Every step of their established playbook triggers an alarm. They can't just change a file or an IP; they have to:
  - Completely rethink their initial access strategy.
  - Develop entirely new ways to execute code, maintain persistence, and move laterally.
  - Invest in significant research and development to discover new vulnerabilities or develop novel evasion techniques. This level of disruption makes their attack campaign incredibly inefficient, costly, and potentially forces them to abandon the attack altogether or redirect their efforts to easier targets. You've not just blocked a single attack; you've dismantled their entire operational approach against your organization.

---

## 🧠 7. TTPs (Tough)

- **What?** Attackers plans and objectives - Tactics, Techniques & Procedures (e.g., [MITRE ATT&CK](https://attack.mitre.org/) methods).  
- **Detection methods:** Behavioral analytics, Windows Event logs, EDR/EDR/XDR correlation.  
- **Why it’s devastating:** Attackers must fully revamp their campaign — tooling, procedures, and training are all affected. 
- **Summiting the Pyramid:** MITRE Engenuity’s framework promotes analytic robustness by decomposing tools vs OS-native actions.

---

## 🧩 CTI & Real-World Use

- **How to use it:** Match detection efforts with CTI availability. Hashes/IPs are low effort but low impact; TTPs are high effort but high impact. 
- **EDR evolution:** With proper tools, TTP detection is now more approachable — not just academic theory.  
- **Threat scenario:** Ransomware ops now often register domains hours before use—illustrating how fast lower-layer indicators expire.

---

## 📝 TL;DR

| Layer                  | Attacker Pain ✔️     | Defender ROI 💪             |
|------------------------|-----------------------|-----------------------------|
| Hashes                 | Very Low              | Quick wins, but fleeting    |
| IPs                    | Low                   | Useful, but easily bypassed |
| Domains                | ↓ Moderate            | Better blocking, some resilience |
| Host Artifacts         | ↑ High                | Forces tool rework θ        |
| Network Artifacts      | ↑ High                | Behaviors harder to evade   |
| Tools                  | Very High             | Disrupts campaign mechanics |
| TTPs                   | Maximum               | Strategic advantage         |

---

## 🧭 Final Word

Climbing the pyramid equips your blue team with **strategic depth**. Shift from chasing weak signals at the bottom, to creating real **adversary friction** at the top. That's where you force attackers to bleed time, money—and sometimes mission failure.

## Glossary
- <ins>Command and Control (C2)</ins>Infrastructure are a set of programs used to communicate with a victim machine. This is comparable to a reverse shell, but is generally more advanced and often communicate via common network protocols, like HTTP, HTTPS and DNS. What is [C2](https://www.varonis.com/blog/what-is-c2)
- URI - Uniform Resource Identifier
- <ins>CTPH (Context Triggered Piecewise Hashes)/Fuzzy Hashing/Ssdeep hashing</ins> - Fuzzy hashing helps you to perform similarity analysis - match two files with minor differences based on the fuzzy hash values. One of the examples of fuzzy hashing is the usage of SSDeep; on the [SSDeep](https://ssdeep-project.github.io/ssdeep/index.html) official website, you can also find the complete explanation for fuzzy hashing.
- <ins>Fast Flux</ins>- is a technique where cybercriminals rapidly change the IP address associated with a malicious website's domain name, typically every few minutes or seconds. This uses a large network of compromised computers (a botnet) to act as proxies. It makes it extremely difficult for security teams or law enforcement to block or shut down the malicious site, as its location is constantly shifting. This tactic enhances the resilience and evasiveness of illegal online operations.
-  <ins>APT</ins>(Advanced Persistent Threat Groups) 

Stay sharp, hunt smart 🔍🛡️
