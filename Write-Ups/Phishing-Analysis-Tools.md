# 🛠️ Phishing Analysis Tools

In this section, we’ll explore tools that assist in analyzing phishing emails, including headers, URLs, and attachments. Proceed with caution—some samples originate from real phishing campaigns.

---

## 📋 Email Header Analysis

### Information to Collect:
- Sender email address
- Sender IP address
- Reverse lookup of the sender IP
- Subject line
- Recipient email address (To/CC/BCC)
- Reply-To email address (if any)
- Date and Time

### 🔍 Tools to Analyze Email Headers:
- [Google Messageheader Tool](https://toolbox.googleapps.com/apps/messageheader/analyzeheader)
- [Microsoft Message Header Analyzer](https://mha.azurewebsites.net/)
- [MailHeader.org](https://mailheader.org)

### 📌 Additional Reading:
- [MTA (Message Transfer Agent)](https://en.wikipedia.org/wiki/Message_transfer_agent)
- [MUA (Mail User Agent)](https://en.wikipedia.org/wiki/Mail_user_agent)

---

## 🌐 Email Body Analysis

### Information to Collect:
- URLs (expanded from shorteners)
- Attachment names
- Attachment hash (SHA256 preferred)

### URL & Link Tools:
- [IPinfo.io](https://ipinfo.io/)
- [urlscan.io](https://urlscan.io/)
- [Talos Reputation Center](https://talosintelligence.com/reputation)
- [URL Extractor](https://www.convertcsv.com/url-extractor.htm)
- [CyberChef (Extract URLs Recipe)](https://gchq.github.io/CyberChef/)

### ⚠️ Pro Tip:
Always defang URLs before sharing (e.g., `hxxp[:]//domain[.]com` instead of `http://domain.com`).

---

## 📎 Attachment Analysis

### Steps:
1. Safely save the attachment (e.g., using Thunderbird)
2. Obtain SHA256 hash:  
   ```bash
   sha256sum filename.pdf
   ```
3. Check reputation:
   - [Cisco Talos File Reputation](https://talosintelligence.com/talos_file_reputation)
   - [VirusTotal](https://www.virustotal.com/gui/)

---

## 🧪 Malware Sandbox Environments

Use these to detonate attachments safely and observe behavior:

- [Any.Run](https://app.any.run/)
- [Hybrid Analysis](https://www.hybrid-analysis.com/)
- [Joe Sandbox](https://www.joesecurity.org/)

---

## 🧠 PhishTool

### Overview:
PhishTool is a powerful phishing analysis platform. It combines:
- Threat Intelligence
- OSINT
- Email metadata
- Auto-analysis features

👉 [PhishTool Community Edition](https://www.phishtool.com/)

### Key Features:
- Parse headers, body, and attachments
- Connects with VirusTotal API
- View HTML/text views of emails
- Extract hashes, sender details, and more
- Tag and resolve threats with classification codes

> Note: Not all phishing emails target the same audiences. Use classification codes (e.g., Whaling, Credential Harvesting) for tagging.

---

🔚 End of tools summary. Always proceed with caution when analyzing emails or attachments.
