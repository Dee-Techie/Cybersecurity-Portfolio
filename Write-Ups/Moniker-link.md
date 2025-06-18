# 📧 CVE-2024-21413 - Microsoft Outlook Moniker Link Vulnerability

On **February 13, 2024**, Microsoft disclosed a critical vulnerability in Microsoft Outlook, identified as **CVE-2024-21413**, discovered by **Haifei Li of Check Point Research**.

The issue arises from the way Outlook handles **Moniker Links**, which are special types of hyperlinks tied to Microsoft’s **Component Object Model (COM)**. These links can bypass Outlook’s built-in security and be weaponized in phishing emails to trigger credential theft or **Remote Code Execution (RCE)**.

---

## 🔍 What is a Moniker Link?

Moniker links are not regular URLs. They are COM-based identifiers that can:

- Access local files or network shares
- Bind to and execute COM objects
- Trigger unintended system behaviors when clicked

### Why It Matters

Outlook mishandles these links, allowing attackers to:

- Leak NTLM credentials to an external attacker-controlled server
- Potentially execute arbitrary code on the victim’s system

---

## 📊 Vulnerability Overview

| **Field**        | **Detail**                                                                 |
|------------------|-----------------------------------------------------------------------------|
| **CVE**          | [CVE-2024-21413](https://msrc.microsoft.com/update-guide/en-US/vulnerability/CVE-2024-21413) |
| **Publish Date** | February 13, 2024                                                           |
| **Impact**       | Remote Code Execution (RCE), Credential Leak                                |
| **Severity**     | Critical                                                                    |
| **Attack Complexity** | Low                                                                  |
| **CVSS Score**   | 9.8                                                                         |
| **Discovered By**| Haifei Li, Check Point Research                                             |

---

## 🖥️ Affected Software Versions

| **Office Release**                | **Affected Version(s)**                          |
|----------------------------------|--------------------------------------------------|
| Microsoft Office LTSC 2021       | From 19.0.0                                      |
| Microsoft 365 Apps for Enterprise| From 16.0.1                                      |
| Microsoft Office 2019            | From 16.0.1                                      |
| Microsoft Office 2016            | 16.0.0 before 16.0.5435.1001                     |

---

## 🧠 Technical Context: What Is COM?

Microsoft’s **Component Object Model (COM)** is a technology used for inter-process communication and object creation in Windows.

A **Moniker** in COM is:

- A type of “intelligent name” that identifies and binds to COM objects
- Capable of linking to local resources, network shares, or system components

When misused in links (e.g., in emails), these **Moniker Links** can instruct the system to perform high-privilege actions, leading to major security concerns.

---

## 🛡️ Exploitation Risk

Attackers exploit this by:

1. Sending a crafted email with a **malicious Moniker Link**
2. Victim clicks the link → triggers:
   - **NTLM credential theft**
   - **Remote Code Execution (RCE)**

These links bypass Outlook's default security warnings — making them especially dangerous.

---

## 📝 Summary

- **CVE-2024-21413** demonstrates the dangers of legacy tech (COM/Moniker) being used in modern apps
- Users should update Outlook immediately and apply Microsoft’s patches
- Be cautious of suspicious emails, especially those containing strange or non-http/https links

---

> 💡 Pro Tip: Disable automatic NTLM authentication to mitigate credential leakage risks from these types of exploits.
>
> ---

<sub>🔗 References & Resources:
- TryHackMe — Moniker Link | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/monikerlink)</sub>
- Wanna read more about [Moniker Link](https://research.checkpoint.com/2024/the-risks-of-the-monikerlink-bug-in-microsoft-outlook-and-the-big-picture/)
- Access [CVE Records](https://www.cve.org/CVERecord?id=CVE-2024-21413)

