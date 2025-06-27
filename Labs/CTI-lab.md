# 🕵️‍♂️ Friday Overtime - CTI Lab

**Tags**: `Cyber Threat Intelligence` `OSINT` `Malware Analysis` `MITRE ATT&CK` `CyberChef` `IOC Hunting`

---

## ⚠️ Disclaimer

> 🚨 **Please note:**  
The artefacts used in this scenario were retrieved from a **real-world cyber-attack**.  
Interaction with these artefacts **must be done only within the attached VM** as it is an isolated and secure environment. Engaging with them outside the VM may pose security risks.

---

## 📜 The Scenario

**Hello Busy Weekend. . .**

It's a late **Friday evening** at *PandaProbe Intelligence* when a sudden notification hits your CTI platform. While most of your colleagues are signing off for the weekend, you notice a **high-priority ticket** from *SwiftSpend Finance* 📩 — a company known for its tight cybersecurity protocols.

They've discovered **suspicious files** and need **immediate analysis**. As the lone CTI Analyst still clocked in, you take charge 💪.

> The attached ZIP file contains potentially **malicious DLLs** — your mission: **analyze, identify, and report.**

---

## 🧰 Tools Used

- 🖥️ Terminal  
- 🧠 MITRE ATT&CK Navigator  
- 🌐 OSINT  
- 📚 DocIntel  
- 🔎 Google  
- 🍳 CyberChef  
- 🧪 VirusTotal  

---

## 🎯 Objectives & Questions

You will uncover the following:

- ✅ **What is the SHA1 hash of the file `pRsm.dll` inside `samples.zip`?**  
  `9d1ecbbe8637fed0d89fca1af35ea821277ad2e8`

- ✅ **Which malware framework utilizes these DLLs as add-on modules?**  
  `MgBot`

- ✅ **Which MITRE ATT&CK Technique is linked to using `pRsm.dll` in this malware framework?**  
  `T1123 - Audio Capture`

- ⌛ **What is the CyberChef defanged URL of the malicious download location first seen on 2020-11-02?**  
  _Answer format: `*****://********.*********.****.****/****/**/********_****_*****.****`_

- ⌛ **What is the CyberChef defanged IP address of the C&C server first detected on 2020-09-14?**  
  _Answer format: `****.****.****.***`_

- ⌛ **What is the SHA1 hash of the SpyAgent family spyware targeting Android devices on 2022-11-16?**  
  _Answer format: `****************************************`_

---

## 🧪 Step-by-Step Investigation

### 1. 🔓 Extracting the Samples

📸 *Screenshot Placeholder - Unzipping `samples.zip` in terminal*

- Isolated VM booted
- Files extracted securely
- SHA1 hash calculated for `pRsm.dll`

---

### 2. 🧬 Initial Triage

📸 *Screenshot Placeholder - Automated scan results (VirusTotal or in-VM analysis)*

- Tools used: VirusTotal, CyberChef, strings, etc.
- Basic characteristics of DLLs noted

---

### 3. 🔍 Manual Deep Dive

📸 *Screenshot Placeholder - Inspecting code and behaviors*

- Observed DLL behavior
- Noticed audio capture and stealth functionality
- Linked to MgBot via signature & OSINT reports

---

### 4. 🌐 Threat Intel Correlation

📸 *Screenshot Placeholder - DocIntel/OSINT/MITRE ATT&CK*

- Confirmed `T1123` (Audio Capture)
- Checked timeline of C&C server activity
- Identified IP and download URL

---

### 5. 🧪 CyberChef Usage

📸 *Screenshot Placeholder - CyberChef transformation for URL & IP*

- URL defanged  
- IP address defanged

---

## 📌 Key Findings

| Indicator Type        | Value |
|-----------------------|-------|
| SHA1 (`pRsm.dll`)     | `9d1ecbbe8637fed0d89fca1af35ea821277ad2e8` |
| Malware Family        | `MgBot` |
| MITRE Technique       | `T1123 - Audio Capture` |
| Defanged URL          | _[To be added]_ |
| Defanged IP           | _[To be added]_ |
| Android SpyAgent SHA1| _[To be added]_ |

---

## 🧠 Lessons Learned

- 🧩 Always verify file integrity (hashing) before analysis
- 🧪 MITRE mapping helps contextualize behaviors quickly
- 🔍 CyberChef and VirusTotal are go-to tools for fast IOC enrichment
- 🧱 Never underestimate the importance of an isolated VM

---

## 🔗 References

- [MITRE ATT&CK T1123](https://attack.mitre.org/techniques/T1123/)
- [VirusTotal](https://virustotal.com/)
- [CyberChef](https://gchq.github.io/CyberChef/)
- [DocIntel](https://www.docintel.io/)  
- [MgBot Analysis - External Blog Reference](_Insert Link_)

---

> ✍️ **Authored by:** *Dee Bhatnagar*  
> 🗓️ *Date:* June 2025  
> 🔗 *More labs:* [Visit my GitHub Labs Section](#)

