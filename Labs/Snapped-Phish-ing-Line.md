# 🎯 Phishing Lab: SwiftSpend Financial Breach Investigation

## 📘 Disclaimer

This lab scenario is **based on real-world phishing campaign artifacts**, though names, characters, and events have been fictionalized for educational purposes.

⚠️ **Important:** The phishing kit used was retrieved from a real phishing campaign. All interactions should be conducted **strictly inside the provided isolated VM environment** to avoid risk.

---

## 🕵️ Scenario: An Ordinary Midsummer Day...

You're part of the **IT department at SwiftSpend Financial**. The day begins routinely—until a flood of helpdesk tickets begins to pile up. Employees across multiple departments report receiving a suspicious email. Alarmingly, some can no longer log into their accounts after submitting their credentials.

As a cybersecurity responder, your job is to:

- 🔍 Analyze email samples reported by staff.
- 🌐 Browse phishing URLs safely inside the VM.
- 📦 Retrieve and analyze the phishing kit.
- 🧠 Use CTI tooling to understand the adversary's tactics.
- 💾 Extract and review technical IOCs from the kit.

---

## 📋 Lab Findings

### 👤 Who received a malicious PDF attachment?
```
William McClean
```

### 📧 What email address was used to send the phishing emails?
```
Accounts.Payable@groupmarketingonline.icu
```

### 🌐 What was the redirection URL for Zoe Duncan? *(defanged format)*
```
hxxp[://]kennaroads[.]buzz/data/Update365/office365/40e7baa2f826a57fcf04e5202526f8bd/?email=zoe[.]duncan@swiftspend[.]finance&error
```
![image](https://github.com/user-attachments/assets/982893d9-2642-46e7-a4eb-7d66cf31e5e3)

### 🗜️ What is the URL of the phishing kit ZIP archive? *(defanged format)*
```
hxxp[://]kennaroads[.]buzz/data/Update365[.]zip
```

### 🔐 What is the SHA256 hash of the phishing kit?
```
ba3c15267393419eb08c7b2652b8b6b39b406ef300ae8a18fee4d16b19ac9686
```
![image](https://github.com/user-attachments/assets/ff3331f7-f487-43b7-ad41-a16a5bfab723)

### ⏱️ When was the phishing kit first submitted? *(UTC format)*
```
2020-04-08 21:55:50 UTC
```
![image](https://github.com/user-attachments/assets/e56ae5ad-332a-49f9-8f11-dd1e691f29e6)

### 🧾 When was the SSL certificate for the phishing domain first logged?
```
2020-06-25
```

### 🔁 Which user submitted their password twice?
```
michael.ascot@swiftspend.finance
```
![image](https://github.com/user-attachments/assets/64417f13-cbdb-4dca-883e-a0bf74cae107)

### 🎣 What email did the attacker use to collect stolen credentials?
```
jamestanner2299@gmail.com
```
![image](https://github.com/user-attachments/assets/66b3f871-7491-42b0-a035-226df3e46f1b)

### 📮 Another malicious email address from the phishing kit?
```
jamestanner2299@gmail.com
```

### 🏁 Hidden Flag
```
THM{pL4y_w1Th_tH3_URL}
```

---

## 🔐 Skills Practiced

- Email header analysis  
- Phishing URL inspection  
- IOC extraction from phishing kits  
- Threat intel research  
- Log correlation  
- Safe malware artifact handling  

---

## 🧠 Lessons Learned

- Attackers often reuse phishing kits across different campaigns.
- Users submitting credentials multiple times gives attackers more data.
- Email artifacts + CTI tools can provide deep adversary insight.
- **Always analyze email reports inside an isolated environment.**

---

## ✅ Outcome

Gained real-world experience analyzing phishing campaigns, inspecting URLs and headers, handling phishing kits, and extracting threat intelligence — all in a **safe, controlled lab**.

🧪 **Simulated breach, real skills.**

---

🔗 [View TryHackMe Room](https://tryhackme.com/room/phishingemails2rytmuv)
