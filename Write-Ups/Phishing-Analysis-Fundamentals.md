# 📧 Introduction to Spam & Phishing Emails

Spam and phishing are two of the most common **social engineering** attacks, with email being a primary vector. 🛡️

### 🚫 Spam vs. 🎣 Phishing
- **Spam**: Unwanted or unsolicited emails — you've seen them in your inbox!
- **Phishing**: Malicious emails meant to trick users into clicking links or downloading attachments to gain a foothold into a system. 🐟

> ❗ Even with a solid security infrastructure, one wrong click from an unsuspecting user can open the doors to attackers.

---

## 📬 A Bit of History

- The **first spam email** was sent in **1978**.
- **Ray Tomlinson** is credited with inventing email in the 1970s via **ARPANET** (pre-Internet era).
- Email address format:  
  `username@domain.com` → e.g. `billy@johndoe.com`

---

## ✉️ Email Delivery Protocols

Three main protocols enable the flow of emails across networks:

| Protocol | Role | Description |
|---------|------|-------------|
| **SMTP** | Outgoing | Sends emails from sender to recipient 📤 |
| **POP3** | Incoming | Downloads emails to a single device 📥 |
| **IMAP** | Incoming | Syncs emails across multiple devices 🔄 |

### 🔄 POP3 vs IMAP

| Feature | POP3 📥 | IMAP 🔄 |
|--------|----------|--------|
| Storage | Local device only | Server-based |
| Access | One device only | Multiple devices |
| Sent Emails | Stored locally | Stored on server |
| Sync | No | Yes |
| Server Retention | Optional | Always |

---

## 🛣️ How an Email Travels (Simplified)

1. **Alexa** writes an email to `billy@johndoe.com` and hits SEND.
2. Her **SMTP server** queries **DNS** to find the IP of `johndoe.com`.
3. **DNS** replies with the destination info.
4. Alexa’s **SMTP server** sends the email over the Internet.
5. The message passes through intermediate SMTP servers.
6. Email arrives at **johndoe.com's SMTP server**.
7. Email is placed in **POP3/IMAP** server, waiting for Billy.
8. **Billy’s email client** checks for new messages.
9. The email is either **copied** (IMAP) or **downloaded** (POP3) to Billy's inbox.
10. 
![image](https://github.com/user-attachments/assets/0e43a5f8-77bf-4cb0-9fdd-fc46b4c3a0cd)

---

## 📌 Default Email Ports

| Protocol | Port |
|----------|------|
| SMTP     | 25   |
| POP3     | 110  |
| IMAP     | 143  |

> 🔗 For deeper technical understanding, refer to [official documentation](https://help.dreamhost.com/hc/en-us/articles/214918038-Email-client-configuration-overview) or RFCs.

---
# 📧 Understanding Email Components for Threat Analysis

Great! Now that we know how an email travels from point A to point B ✉️➡️📥 and all the protocols involved, it's time to break down the anatomy of an email once it lands in our inbox. This knowledge is essential when manually analyzing potentially malicious emails 🕵️‍♂️.

## 🧩 Parts of an Email

There are two main parts of an email:

- **Email Header**: Contains metadata about the email (e.g., the servers that relayed the message)
- **Email Body**: The actual content of the email (text and/or HTML)

The structure follows the **Internet Message Format (IMF)** 📜 ([RFC 5322](https://datatracker.ietf.org/doc/html/rfc5322)).

## 📬 Email Header Fields

When investigating a suspicious email, examine the following fields:

- **From**: The sender’s email address 👤
- **Subject**: The subject line of the email 📝
- **Date**: The date the email was sent 🕒
- **To**: The recipient’s email address 📮

Additional fields of interest:

- **X-Originating-IP**: Reveals the IP address of the sender 🌐
- **Smtp.mailfrom / header.from**: Indicates the sending domain 🌍
- **Reply-To**: Where responses will be sent, which may differ from the "From" address 🔁

🧠 _Pro Tip_: If the "Reply-To" address differs significantly from the "From" address, this could be a phishing red flag 🚩.

🔗 [Guide on Understanding Email Headers (Media Temple - Archived)](https://web.archive.org/web/20221219232959/https://mediatemple.net/community/products/all/204643950/understanding-an-email-header)

## 🧾 Email Body

This is the part of the message the sender wants you to see. It comes in two formats:

### 🔤 Plain Text Example

A simple body with no formatting.

### 🌐 HTML Formatted Email

HTML allows enhanced formatting like images, links, and buttons. These can be embedded within the body and viewed via:

- "View Source" or "View Raw Email" (varies by client)
- Optionally toggle between raw HTML and rendered view (e.g., "View Rendered HTML" in ProtonMail)

⚠️ Be cautious of HTML emails with links and hidden forms. These are often used for phishing!

## 📎 Email Attachments

Emails can include attachments, such as PDFs or Office documents. These can be inspected via email headers too.

Example email headers for an attachment:

- `Content-Type: application/pdf`
- `Content-Disposition: attachment`
- `Content-Transfer-Encoding: base64`

🧪 _Pro Tip_: Base64 encoded attachments can be extracted and decoded for further analysis using tools such as [CyberChef](https://gchq.github.io/CyberChef/).

⚠️ Always inspect suspicious attachments in a secure, sandboxed environment.

## ✅ TL;DR so far

Understanding how to inspect both the header and body of an email is key to detecting threats 🎯. Watch out for:

- Suspicious sender and reply-to addresses
- Embedded links or attachments with hidden code
- Unexpected base64-encoded data

---

# 📧 Malicious Email Types & Threats Overview

Now that we understand how emails work and travel from sender to recipient, let's explore how emails are misused for nefarious purposes. 🚨

## 🧨 Types of Malicious Emails

- **Spam**: Unsolicited junk emails sent in bulk.  
- **MalSpam**: A more dangerous form of spam that carries malicious intent.  
- **Phishing**: Emails pretending to be from trusted entities to steal sensitive info.  
- **Spear Phishing**: Targeted phishing toward specific individuals or organizations.  
- **Whaling**: Spear phishing aimed at C-level executives (CEO, CFO, etc.).  
- **Smishing**: SMS-based phishing attacks targeting mobile devices.  
- **Vishing**: Voice call-based phishing attacks.

## 🎯 Phishing Tactics and Objectives

Phishing attacks usually aim to:

- Harvest user credentials (e.g., login info).
- Gain unauthorized access to computers/networks.

## 🕵️ Common Characteristics of Phishing Emails

- 🕶️ **Spoofed sender**: Masquerades as a trusted entity.
- ⚠️ **Urgent language**: "Invoice", "Suspended", "Urgent action required".
- 🏪 **Mimic trusted brands**: HTML designed to resemble real companies (e.g., Amazon).
- 🧱 **Poor formatting or grammar**: Often gives away malicious intent.
- 👤 **Generic greetings**: "Dear Sir/Madam", no personalization.
- 🔗 **Suspicious links**: Shortened URLs or obfuscated destinations.
- 📎 **Malicious attachments**: Often disguised as invoices, PDFs, or spreadsheets.

## 🚫 Hyperlink & Attachment Safety: Defanging

**Defanging** is a technique used to safely share suspicious links or email addresses without risk of accidental clicks.

### 🔧 Defanging Example:
- `http://www.suspiciousdomain.com` → `hxxp[://]www[.]suspiciousdomain[.]com`

🛠️ Use [CyberChef](https://gchq.github.io/CyberChef/) to safely defang URLs before sharing them with your SOC team.

## 🕵️‍♀️ Business Email Compromise (BEC)

**BEC** occurs when an attacker gains control over an employee's legitimate email account and uses it to:

- 📤 Impersonate the user
- 💰 Convince others to perform unauthorized or fraudulent actions (e.g., wire transfers, data leaks)

---

> ⚠️ Stay vigilant and always analyze emails carefully—when in doubt, do not click!
