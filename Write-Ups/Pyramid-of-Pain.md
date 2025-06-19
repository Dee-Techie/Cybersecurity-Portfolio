# 🧗 Pyramid of Pain</br>
Not all indicators are created equal; some of them are far more valuable than others.

<img src="https://github.com/user-attachments/assets/06bed36b-db06-4dfc-9442-62828687908d" alt="Pyramid of Pain" width="500" /></br>

The **Pyramid of Pain**, introduced by David Bianco in 2013, ranks indicators by how much **“pain”** they cause adversaries when detected. Higher layers force attackers to spend more time, money, and skill to reinvent their attacks. 🧩🚧

---

## 🔐 1. Hash Values (Trivial)

- **What?** File fingerprints (MD5, SHA-1, SHA-256).  
- **Defender tools:** VirusTotal, OPSWAT Metadefender, SIEM ingestion. 
- **Why attackers don’t care:** Change a byte, get a new hash. Polymorphic malware makes this trivial.
- **💡 Tip:** Use YARA rules for stronger detection beyond static hashes.

---

## 🌐 2. IP Addresses (Easy)

- **What?** Malicious IPs or subnets.  
- **Defender gain:** Quick blocks via firewalls or TIPs (e.g., Recorded Future, Anomali).
- **Attacker trick:** IP rotation, cloud proxies, Fast Flux DNS.
- **Use case:** Sandboxes like ANY.RUN reveal dynamic IP behavior.

<img src="https://github.com/user-attachments/assets/30cb980c-c292-4c00-807c-45a9c53c63a6" alt="Domain/IP Reports" width="1350" /></br>

---

## 🌍 3. Domain Names (Simple)

- **What?** Malicious domains or subdomains.  
- **Defender gain:** Block domains, sinkhole them, analyze proxy logs.  
- **Attacker trick:** Punycode spoofing (e.g., `xn--addas-o4a.de` → looks like `adidas.de`), URL shorteners (`bit.ly+` preview).

---

## 🖥️ 4. Host Artifacts (Annoying)

- **What?** Malware artifacts on endpoints — registry keys, dropped files, strange processes (e.g. Word→PowerShell).  
- **🤖 Defender Tools:** EDR, SIEM, Process Monitor, Log analysis.  
- **Attacker pain:** They must change tooling or behavior; more work and cost.

<img src="https://github.com/user-attachments/assets/9b329f95-366b-4047-9444-692c02be78b0" alt="Host Artifacts Report 1" width="500" /></br>

<img src="https://github.com/user-attachments/assets/d83133c0-c189-44d3-a01d-4d8a7c58f6f4" alt="Host Artifacts Report 2" width="500" /></br>

---

## 🌐 5. Network Artifacts (Annoying)

- **What?** Behavioral network indicators — unusual HTTP POST URIs, custom user‑agents, C2 patterns. An attacker might use a User-Agent string that hasn’t been observed in your environment before or seems out of the ordinary. The User-Agent is defined by [RFC2616](https://datatracker.ietf.org/doc/html/rfc2616#page-145) as the request-header field that contains the information about the user agent originating the request.
- **Detect with:** PCAP analysis (Wireshark/TShark), IDS/IPS signatures (Snort, Suricata).  
- **Why it hurts:** Attackers need to re-engineer their comms, so detection gains you time.
- P.S. If you can detect the custom User-Agent strings that the attacker is using, you might be able to block them, creating more obstacles and making their attempt to compromise the network more annoying.👿😤
---

## 🛠️ 6. Tools (Challenging)

- **What?** The actual malware and scripts — backdoors, stegomalware, credential dumpers.  
- **Why it hurts:** Custom-built tools force them to rebuild or abandon their arsenal.
- **Defender strategies:**
  - YARA rules, antivirus/EDR signatures  
  - Fuzzy hashing (SSDeep) to detect modified malware.
  - Use feeds like MalwareBazaar, Malshare, SOC Prime TDM.  
- **Real-world context:** SentinelOne & Cisco enhance CTI by hunting behaviors, not just signatures.

---

## 🧠 7. TTPs (Tough)

- **What?** Tactics, Techniques & Procedures (e.g., [MITRE ATT&CK](https://attack.mitre.org/) methods).  
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
- Command and Control (C2) Infrastructure are a set of programs used to communicate with a victim machine. This is comparable to a reverse shell, but is generally more advanced and often communicate via common network protocols, like HTTP, HTTPS and DNS. What is [C2](https://www.varonis.com/blog/what-is-c2)
- URI - Uniform Resource Identifier
- CTPH (Context Triggered Piecewise Hashes)/Fuzzy Hashing/Ssdeep hashing - Fuzzy hashing helps you to perform similarity analysis - match two files with minor differences based on the fuzzy hash values. One of the examples of fuzzy hashing is the usage of SSDeep; on the SSDeep official website, you can also find the complete explanation for fuzzy hashing.
- Fast Flux - is a technique where cybercriminals rapidly change the IP address associated with a malicious website's domain name, typically every few minutes or seconds. This uses a large network of compromised computers (a botnet) to act as proxies. It makes it extremely difficult for security teams or law enforcement to block or shut down the malicious site, as its location is constantly shifting. This tactic enhances the resilience and evasiveness of illegal online operations.

Stay sharp, hunt smart 🔍🛡️
