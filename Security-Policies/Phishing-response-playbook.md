# 🛡️ Phishing Response Playbook

## 🎯 Objective
To provide a standardized, repeatable, and efficient process to detect, analyze, respond to, and remediate **phishing emails** across the organization, minimizing the risk of credential theft, malware infection, and data compromise.

---

## 👥 Target Audience

- SOC Analysts (Tier 1–3)
- Incident Responders
- IT Support Staff
- Email/System Admins
- End Users (Employees)

---

## 🧑‍🏫 What Is Phishing?
Phishing is a **social engineering attack** that uses deceptive emails to trick users into revealing sensitive data (like login credentials or financial information) or executing malicious actions (like clicking malware-laced links or downloading harmful attachments).

---

## 🚨 Phishing Incident Classification

| Type                      | Description                                               |
|---------------------------|-----------------------------------------------------------|
| **Phishing**              | Mass-email campaigns attempting to trick users.           |
| **Spear Phishing**        | Targeted phishing toward specific individuals or groups.  |
| **Whaling**               | Targeted phishing toward senior executives.              |
| **Business Email Compromise (BEC)** | Phishing impersonating executives or suppliers.   |
| **Malicious Attachment**  | Email contains malware payloads.                          |
| **Credential Harvesting** | Links to fake login portals to steal passwords.           |

---

## 📬 Steps for Users/Employees

**If you receive or interact with a suspicious email:**

### 🧍‍♂️ Do:
- ✅ Use the **Report Phishing** button in your email client (if available).
- ✅ Forward the suspicious email to **security@yourdomain.com**.
- ✅ Stop all interaction with the email (don’t click links or open attachments).
- ✅ If you clicked a link or entered credentials, **inform IT/Security immediately**.

### 🚫 Don’t:
- ❌ Reply to the email.
- ❌ Download or open attachments.
- ❌ Forward the email to colleagues.
- ❌ Attempt to investigate on your own.

**Quick Checklist (if you engaged):**
- 🔄 Change your passwords immediately.
- 🔐 Enable MFA (if not already active).
- 🧪 Run an antivirus/EDR scan.
- 📞 Notify your manager.

---

## 🧠 Common Phishing Red Flags

- Misspelled sender domains (e.g., amaz0n[.]com)
- Unusual file attachments (e.g., `.scr`, `.exe`, `.js`)
- Urgent language like "Immediate action required!"
- Hyperlinks that don’t match the display text
- Requests for sensitive info (credentials, payments, W2s)

---

## 🔎 Detection Sources

- Reported by employees
- SIEM alerts (email logs, proxy logs)
- Email gateway alerts (e.g., Mimecast, Proofpoint, Microsoft Defender)
- Endpoint alerts (AV/EDR tools)
- DNS logs (malicious domains or DGA detection)

---

## 🛠️ Tools Used

| Category             | Tools                                                   |
|----------------------|---------------------------------------------------------|
| Email Analysis       | Mailheader Analyzer, PhishTool, dmarcian, MXToolbox     |
| URL/Attachment Scan  | VirusTotal, Any.run, HybridAnalysis, URLScan.io         |
| IOC Investigation    | OTX AlienVault, ThreatFox, AbuseIPDB, Shodan             |
| Environment Search   | Splunk, Sentinel, Google Workspace, M365 Security Center|

---

## 🧩 Response Workflow

### 🟠 Phase 1: Triage

1. Validate the report (is it actually phishing?).
2. Review email metadata (headers, sender domain, reply-to).
3. Identify and defang IOCs (URLs, IPs, file hashes).
4. Check SPF, DKIM, DMARC results.
5. Tag incident severity (Low/Medium/High/Critical).

### 🟡 Phase 2: Investigation

1. Analyze links and attachments in a sandbox.
2. Search internal logs (SIEM/EDR/email logs) for IOC hits.
3. Determine scope (who else received/interacted).
4. Query user activity and network behavior for any impact.

### 🔴 Phase 3: Containment

1. Remove email from inboxes using admin console.
2. Block IOCs in:
   - Email gateway
   - Firewall/DNS filtering
   - Web proxy
3. Reset user credentials if compromised.
4. Quarantine/restore affected endpoints.

### 🟢 Phase 4: Recovery

1. Restore systems or access as needed.
2. Patch software or update controls.
3. Conduct after-action report.
4. Communicate resolution to stakeholders.

---

## ✅ Summary Table

| Control               | Goal                          | Tool/Method                                  |
|----------------------|-------------------------------|----------------------------------------------|
| Email Filtering       | Block bad content             | SEG (Mimecast, Proofpoint, M365 Defender)    |
| IOC Enrichment        | Confirm malicious indicators  | VirusTotal, ThreatFox, AbuseIPDB             |
| Threat Hunting        | Find signs of compromise      | SIEM, EDR, DNS Logs                          |
| Containment           | Stop further spread           | Email purge, IP/URL block                    |
| Credential Rotation   | Reset exposed accounts        | AD/M365 Admin, User Self-Service             |
| User Notification     | Awareness & remediation       | Slack, Email Blast, Ticket Update            |

---

## 📊 Role Responsibility Matrix (RACI)

| Task                                  | SOC | IR Team | IT | User | Manager |
|---------------------------------------|-----|---------|----|------|---------|
| Detect phishing email                 | R   | A       | C  | R    | I       |
| Analyze headers and IOCs              | A   | R       | C  | -    | -       |
| Email purge and containment           | C   | A       | R  | -    | -       |
| Credential reset                      | C   | A       | R  | -    | -       |
| End-user communication                | C   | R       | C  | I    | A       |
| Lessons learned & reporting           | R   | A       | I  | -    | C       |

*R = Responsible, A = Accountable, C = Consulted, I = Informed*

---

## 🔒 Preventative Measures

- ✅ Enforce SPF, DKIM, and DMARC ✅
- ✅ Use **Multi-Factor Authentication (MFA)** on all accounts
- ✅ Disable automatic download of remote content in email
- ✅ Train users with phishing simulations (KnowBe4, GoPhish)
- ✅ Use attachment sandboxing
- ✅ Enforce minimal permissions (Least Privilege)

---

## 📚 Resources

- [MITRE ATT&CK - Phishing (T1566)](https://attack.mitre.org/techniques/T1566/)
- [Phishing IR Template (Counteractive)](https://github.com/counteractive/incident-response-plan-template/blob/master/playbooks/playbook-phishing.md)
- [Microsoft - Phishing Protection](https://learn.microsoft.com/en-us/security/phishing)
- [CISA - Anti-Phishing Tips](https://www.cisa.gov/news-events/news/protecting-against-phishing-attacks)
- [dmarcian SPF/DKIM Tools](https://dmarcian.com/tools/)

---

## 🧠 Lessons Learned

After every phishing incident:
- Conduct a **post-mortem** or root cause analysis.
- Identify gaps in training, detection, or containment.
- Share sanitized incident details to educate staff.
- Continuously tune rules and update IOC detection lists.

---

🧪 Phishing attacks are inevitable. What matters is how **prepared, trained, and responsive** your organization is.

🛡️ Stay vigilant. Stay ready.

