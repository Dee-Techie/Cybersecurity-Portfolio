# 🧗 Pyramid of Pain</br>
Not all indicators are created equal; some of them are far more valuable than others.

<img src="https://github.com/user-attachments/assets/06bed36b-db06-4dfc-9442-62828687908d" alt="Pyramid of Pain" width="500" /></br>

The **Pyramid of Pain**, introduced by David Bianco in 2013, ranks indicators by how much **“pain”** they cause adversaries when detected. Higher layers force attackers to spend more time, money, and skill to reinvent their attacks. 🧩🚧

---

## 🔐 1. Hash Values (Trivial)

- **What?** File fingerprints (MD5, SHA-1, SHA-256).  
- **Defender tools:** VirusTotal, OPSWAT Metadefender, SIEM ingestion. :contentReference[oaicite:1]{index=1}  
- **Why attackers don’t care:** Change a byte, get a new hash. Polymorphic malware makes this trivial. :contentReference[oaicite:2]{index=2}  
- **💡 Tip:** Use YARA rules for stronger detection beyond static hashes. :contentReference[oaicite:3]{index=3}

---

## 🌐 2. IP Addresses (Easy)

- **What?** Malicious IPs or subnets.  
- **Defender gain:** Quick blocks via firewalls or TIPs (e.g., Recorded Future, Anomali). :contentReference[oaicite:4]{index=4}  
- **Attacker trick:** IP rotation, cloud proxies, Fast Flux DNS. :contentReference[oaicite:5]{index=5}  
- **Use case:** Sandboxes like ANY.RUN reveal dynamic IP behavior.

---

## 🌍 3. Domain Names (Simple)

- **What?** Malicious domains or subdomains.  
- **Defender gain:** Block domains, sinkhole them, analyze proxy logs.  
- **Attacker trick:** Punycode spoofing (e.g., `xn--addas-o4a.de` → looks like `adidas.de`), URL shorteners (`bit.ly+` preview). :contentReference[oaicite:6]{index=6}

---

## 🖥️ 4. Host Artifacts (Annoying)

- **What?** Malware artifacts on endpoints — registry keys, dropped files, strange processes (e.g. Word→PowerShell).  
- **🤖 Defender Tools:** EDR, SIEM, Process Monitor, Log analysis.  
- **Attacker pain:** They must change tooling or behavior; more work and cost. :contentReference[oaicite:7]{index=7}

---

## 🌐 5. Network Artifacts (Annoying)

- **What?** Behavioral network indicators — unusual HTTP POST URIs, custom user‑agents, C2 patterns.  
- **Detect with:** PCAP analysis (Wireshark/TShark), IDS/IPS signatures (Snort, Suricata).  
- **Why it hurts:** Attackers need to re-engineer their comms, so detection gains you time. :contentReference[oaicite:8]{index=8}

---

## 🛠️ 6. Tools (Challenging)

- **What?** The actual malware and scripts — backdoors, stegomalware, credential dumpers.  
- **Why it hurts:** Custom-built tools force them to rebuild or abandon their arsenal. :contentReference[oaicite:9]{index=9}  
- **Defender strategies:**
  - YARA rules, antivirus/EDR signatures  
  - Fuzzy hashing (SSDeep) to detect modified malware. :contentReference[oaicite:10]{index=10}  
  - Use feeds like MalwareBazaar, Malshare, SOC Prime TDM.  
- **Real-world context:** SentinelOne & Cisco enhance CTI by hunting behaviors, not just signatures. :contentReference[oaicite:11]{index=11}

---

## 🧠 7. TTPs (Tough)

- **What?** Tactics, Techniques & Procedures (e.g., MITRE ATT&CK methods).  
- **Detection methods:** Behavioral analytics, Windows Event logs, EDR/EDR/XDR correlation.  
- **Why it’s devastating:** Attackers must fully revamp their campaign — tooling, procedures, and training are all affected. :contentReference[oaicite:12]{index=12}  
- **Summiting the Pyramid:** MITRE Engenuity’s framework promotes analytic robustness by decomposing tools vs OS-native actions. :contentReference[oaicite:13]{index=13}

---

## 🧩 CTI & Real-World Use

- **How to use it:** Match detection efforts with CTI availability. Hashes/IPs are low effort but low impact; TTPs are high effort but high impact. :contentReference[oaicite:14]{index=14}  
- **EDR evolution:** With proper tools, TTP detection is now more approachable — not just academic theory. :contentReference[oaicite:15]{index=15}  
- **Threat scenario:** Ransomware ops now often register domains hours before use—illustrating how fast lower-layer indicators expire. :contentReference[oaicite:16]{index=16}

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

Stay sharp, hunt smart 🔍🛡️
