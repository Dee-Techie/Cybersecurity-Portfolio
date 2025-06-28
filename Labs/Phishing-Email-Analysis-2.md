# 🧪 Phishing Lab Blog II: Malicious Attachment Analysis via Sandbox

## 🔍 Scenario
You are a **Level 1 SOC Analyst** 🧑‍💻. As part of your organization's security monitoring team, you’ve been tasked with investigating a **suspicious email attachment** flagged during earlier phishing triage.

This time, you’ll analyze a **malicious PDF file** uploaded to the sandbox environment **Any.Run**. Your job is to extract key **Indicators of Compromise (IOCs)** and gather intel to help your team block similar threats moving forward.

## 🛠️ Task Overview
- Examine suspicious file behavior using dynamic malware sandbox tools
- Identify malicious network activity
- Extract file hashes, flagged processes, and associated IPs
- Defang all malicious artifacts before sharing internally

## 🧰 Tools Used
- 🧪 [Any.Run](https://app.any.run/)
- 🦠 [VirusTotal](https://www.virustotal.com/)
- 🧂 [CyberChef](https://gchq.github.io/CyberChef/) (for defanging and decoding)
- 🔐 SHA256 checksum via `sha256sum`

---

## 📁 Analysis: Case Summary

### 📄 File Details

- **File Name**:  
  ```plaintext
  Payment-updateid.pdf
  ```

- **File Type**:  
  PDF Document 📎 (phishing lure for payment update)

- **SHA-256 Hash**:  
  ```plaintext
  cc6f1a04b10bcb168aeec8d870b97bd7c20fc161e8310b5bce1af8ed420e2c24
  ```

- **Classification by Any.Run**:  
  ```plaintext
  Suspicious activity ⚠️
  ```

---

### 🌐 Network Indicators

- **Malicious IPs (defanged)**:
  ```plaintext
  2[.]16[.]107[.]24, 2[.]16[.]107[.]83
  ```

These IPs were contacted during the execution of the payload within the sandbox, indicating **potential command-and-control (C2)** behavior or **exfiltration**.

---

### ⚙️ System Behavior

- **Flagged Process**:
  ```plaintext
  svchost.exe
  ```

This is a legitimate Windows process but was observed making **unusual network requests**, a known sign of exploitation or evasion.

---

## 🖼️ Screenshots
![image](https://github.com/user-attachments/assets/b3314e6d-2aa0-4f90-9ba6-75b84639a662)
![image](https://github.com/user-attachments/assets/980cccb0-d019-49c1-8280-8c7ae956e7a1)
![image](https://github.com/user-attachments/assets/e149ae9f-ccb6-41f9-b0bf-ba5d6afca69b)

---

## ✅ Outcome
This lab helped simulate how real SOC teams use **sandboxing and automated analysis** to respond to phishing threats. By extracting hashes, IPs, and suspicious behavior, I reinforced the importance of **dynamic analysis** over relying purely on static email inspection. 🛡️

---

🧠 **Pro Tip**: When handling attachments:
- Always sandbox files first — never open them directly.
- Cross-check SHA256 hashes on **VirusTotal**.
- Watch for suspicious child processes like `cmd.exe`, `powershell.exe`, or service-related calls like `svchost.exe`.

---

🔗 [TryHackMe Room](https://tryhackme.com/room/phishingemails3tryoe)

📚 Stay tuned for **Phishing Lab III**, where I’ll dig deeper into payload behavior and chain analysis! 🧵
