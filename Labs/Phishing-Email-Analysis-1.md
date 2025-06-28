# 🧪 Phishing Lab Blog I: Investigating Suspicious Emails

## 🔍 Scenario
You are a **Level 1 SOC Analyst** 🧑‍💻. Several suspicious emails have been forwarded to you from coworkers. Your mission is to **analyze the emails** and extract key details so your team can implement rules to block similar future phishing or spam messages.

## 🛠️ Task Overview
- Analyze **email headers and bodies**
- Use any tools covered in previous modules (e.g., Google Header Analyzer, VirusTotal, URLscan.io, etc.)
- Extract and defang key indicators of compromise (IOCs)

## 🛠️ Tools Used
- PhishTool
- CyberChef

---

## 📥 Email Analysis Questions

### 1️⃣ What brand was this email tailored to impersonate?
```
Netflix
```

---

### 2️⃣ What is the **From** email address?
```
NetfIix<JGQ47wazXe1xYVBrkeDg-JOg7ODDQwWdR@JOg7ODDQwWdR-yVkCaBkTNp.gogolecloud.com>
```

---

### 3️⃣ What is the **originating IP**? *(Defang the IP address)*
```
209[.]85[.]167[.]226
```

---

### 4️⃣ What do you think is the **domain of interest**? *(Defang the domain)*
```
etekno[.]xyz
```

---

### 5️⃣ What is the **shortened URL**? *(Defang the URL)*
```
hxxps[://]t[.]co/yuxfzm8kpg?amp=1
```

---

## 🖼️ Screenshots
![image](https://github.com/user-attachments/assets/5827732b-43d5-4b21-b58f-51f30ff26039)
<img src="https://github.com/user-attachments/assets/f09c8e2f-5c4e-44da-879d-fce19741a07f" alt="Phishing email url" width="600" height="300" />


---

## ✅ Outcome
Strengthened ability to investigate real-world phishing threats and extract indicators to help the SOC team take preventative action. 💪

---

🧠 **Pro Tip:** Always double-check email headers and verify domains, URLs, and attachments before interacting.

🔗 [TryHackMe Room](https://tryhackme.com/room/phishingemails3tryoe)
