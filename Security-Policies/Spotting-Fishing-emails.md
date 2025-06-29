# 🎣 Spotting Phishing Emails: Red Flags & Response Guide

Phishing emails are one of the most common cyber threats facing individuals and organizations. These emails aim to **trick users into taking harmful actions**, such as clicking malicious links, entering credentials, or downloading malware.

This guide is designed to help you **spot**, **analyze**, and **respond** to phishing emails with confidence.

---

## 🚩 Common Red Flags in Phishing Emails

| 🔍 Red Flag               | 💬 Description |
|---------------------------|----------------|
| ❗ **Urgency or Threats**      | "Your account will be locked!" or "Immediate action required!" |
| 📧 **Generic Greetings**       | Lacks personalization like “Dear User” or “Hello Customer” |
| 🌐 **Suspicious Links**       | Hover to preview the actual URL (e.g., `micr0soft.com` vs `microsoft.com`) |
| 📎 **Unexpected Attachments** | PDFs, ZIPs, or `.scr` files from unknown senders |
| 🛑 **Spoofed Email Address**  | Looks real at first glance (e.g., `admin@micros0ft-support.co`) |
| 📄 **Spelling/Grammar Errors**| Sloppy formatting, typos, inconsistent fonts |
| 💼 **Too Good to Be True**    | Unrealistic offers, lottery winnings, or job offers out of nowhere |
| 🖼️ **Odd Branding or Logos**  | Pixelated logos, strange color schemes, wrong domain branding |

---

## 🧠 Advanced Tactics Used by Phishers

Attackers are becoming more sophisticated. Be aware of:

- **Display Name Spoofing**: The name appears correct but hides a malicious email underneath.
- **Homoglyph Attacks**: Using similar-looking characters like `micros0ft.com` (with a zero).
- **Shortened URLs**: Links using `bit.ly`, `t.co`, etc., that mask final destinations.
- **Social Engineering Hooks**: Emotionally manipulative messages (fear, greed, urgency).

---

## 🛠️ Basic Email Header Analysis (SOC Tip)

Analyzing email headers can reveal telltale signs of phishing.

- 🔗 `Return-Path`: Does it match the `From:` domain?
- 🌐 `Received:` IP address – Look it up on VirusTotal or AbuseIPDB.
- ✅ `SPF`, `DKIM`, `DMARC`: Authentication checks — softfail or fail are red flags.

Use this filter in Wireshark for SMTP response code analysis:

```bash
smtp.response.code
```

---

## 📷 Sample Phishing Email (Visual)

🖼️ *[Insert screenshot here: showing a fake login page, mismatched URL, and spoofed sender]*

Use annotations like:
- Red circles around odd email addresses
- Arrows pointing to spoofed URLs
- Highlights on suspicious grammar and urgency

---

## ✅ What to Do If You Suspect a Phishing Email

1. **🚫 Do NOT click** on links or attachments.
2. **📧 Report** the email to your IT/Security team immediately.
3. **🗑️ Delete** the email from your inbox and trash.
4. **🛡️ Run a full antivirus/EDR scan** to ensure nothing was executed.
5. **📚 Learn from it** — review the threat, ask questions, and help your team improve detection.

---

## 🔒 Tools to Analyze Phishing Emails

| Tool          | Use Case |
|---------------|----------|
| [Google Header Analyzer](https://toolbox.googleapps.com/apps/messageheader/) | Header structure |
| [VirusTotal](https://www.virustotal.com) | Check URLs/IPs/attachments |
| [Any.run](https://any.run) | Malware sandbox (attachments) |
| [URLscan.io](https://urlscan.io) | Analyze suspicious links |
| [PhishTool](https://phishtool.com) | Email analysis & case management |
| [MXToolbox](https://mxtoolbox.com) | Look up SPF/DKIM/DMARC records |

---

## 🧑‍💻 For Employees: What You Should Do

If you think you’ve received a phishing email:

🔁 **Don't respond** to the email  
👁️ **Hover over links**, don't click — inspect URLs  
📝 **Forward it** to your IT/security team with the subject line: `"Suspected Phishing"`  
🔌 **Disconnect your device** from the internet if you think you clicked something  
🔄 **Inform your manager** or team lead as a precaution

---

## 🧰 Proactive Measures

- ✅ Enable Multi-Factor Authentication (MFA)
- 🔐 Enforce Email Authentication (SPF, DKIM, DMARC)
- 📢 Conduct Regular Security Awareness Training
- 📈 Run Phishing Simulations
- 🚷 Block risky file types (.exe, .scr, .js, etc.)
- 💬 Keep open communication between IT and staff

---

## 📎 Related Docs

- 📄 [Phishing Incident Response Playbook](./playbooks/phishing-playbook.md)
- 🔑 [Password Policy](./docs/password-policy.md)
- 🛡️ [MFA Setup Guide](./docs/mfa-policy-guide.md)
- 📧 [Zero Trust Email Policy](./docs/zero-trust-policy.md)

---

> 💬 **Remember**: If something looks off, it probably is.  
> 📣 _“Think before you click!”_
