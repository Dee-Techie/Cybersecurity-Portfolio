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

- ✅ **Which malware framework utilizes `pRsm.dll` as add-on modules?**  
  `MgBot`

- ✅ **Which MITRE ATT&CK Technique is linked to using `pRsm.dll` in this malware framework?**  
  `T1123 - Audio Capture`

- ⌛ **What is the CyberChef defanged URL of the malicious download location first seen on 2020-11-02?**  
  _Answer format: `hxxp[://]update[.]browser[.]qq[.]com/qmbs/QQ/QQUrlMgr_QQ88_4296.exe`_

- ⌛ **What is the CyberChef defanged IP address of the C&C server first detected on 2020-09-14?**  
  _Answer format: `122[.]10[.]90[.]12`_

- ⌛ **What is the SHA1 hash of the SpyAgent family spyware targeting Android devices on 2022-11-16?**  
  _Answer format: `1c1fe906e822012f6235fcc53f601d006d15d7be`_

---

## 🧪 Step-by-Step Investigation

### 1. 🔓 Extracting the Samples

![image](https://github.com/user-attachments/assets/a2a8c623-de4a-45e1-97cb-c1a05ed0ad42)

- Isolated VM booted
- Commands used :
  - cd : to enter a directory
  - ls : for listing content
  - unzip samples.zip : for unzipping
  - sha1sum pRsm.dll : for fetching SHA1 hash for the file
- Files extracted securely
- SHA1 hash calculated for `pRsm.dll`

---

### 2. 🧬 Initial Triage

![image](https://github.com/user-attachments/assets/f9e64342-c7dc-4334-bb17-109095bff711)
![image](https://github.com/user-attachments/assets/9d2528f4-7501-4e41-ab93-81ffdff0358e)

 ```bash
http://cgi1.apnic.net/cgi-bin/my-ip.php
http://loc.map.baidu.com/sdk.php
http://loc.map.baidu.com/sdk_ep.php
 ```
![image](https://github.com/user-attachments/assets/2ade1974-ad00-4989-9bf8-b098b67c502d)

- Tools used: VirusTotal, CyberChef, strings, etc.
- Basic characteristics of DLLs noted

---

### 3. 🔍 Manual Deep Dive

![image](https://github.com/user-attachments/assets/c536de56-78ca-4666-8ad8-cdabb29c2182)
![image](https://github.com/user-attachments/assets/9f3abcaf-eea0-4880-9691-7c2807073bd8)
![image](https://github.com/user-attachments/assets/c432ff5b-fe9a-40b3-9dce-12ff341058f8)

- Observed DLL behavior
- Noticed audio capture and stealth functionality
- Linked to MgBot via signature & OSINT reports

---

### 4. 🌐 Threat Intel Correlation

![image](https://github.com/user-attachments/assets/539285c4-d962-4ab7-872e-41c2b421907d)

- Confirmed `T1123` (Audio Capture)
- Checked timeline of C&C server activity
- Identified IP and download URL
- Cross-referenced with [MITRE](https://attack.mitre.org/versions/v12/techniques/T1123/)

---

### 5. 🧪 CyberChef Usage

![image](https://github.com/user-attachments/assets/3a2bacc1-1ec6-420a-aa8a-5954a086ab3e)
![image](https://github.com/user-attachments/assets/30cbe44a-8725-4fa1-b54c-d89320d7e000)

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
- 🛡️ Always defang (replace . with [.]) IOCs before including them in reports, blogs, or communications.

---

## 🔗 References

- [MITRE ATT&CK T1123](https://attack.mitre.org/techniques/T1123/)
- [VirusTotal](https://virustotal.com/)
- [CyberChef](https://gchq.github.io/CyberChef/)
- [DocIntel](https://www.docintel.io/)  
- [MgBot Analysis - External Blog Reference](https://www.welivesecurity.com/2023/04/26/evasive-panda-apt-group-malware-updates-popular-chinese-software/)

---

> ✍️ **Authored by:** *Dee Bhatnagar*  
> 🗓️ *Date:* June 2025  
> 🔗 *More labs:* [Visit my GitHub Labs Section](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Labs/README.md)

