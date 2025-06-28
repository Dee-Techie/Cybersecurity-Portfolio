# 🛡️ Phishing Prevention and Email Security

## 📬 Defender Actions

There are various actions a defender can take to help protect users from falling victim to a malicious email. Here are some key preventive measures:

- ✅ **Email Security** (SPF, DKIM, DMARC)
- 🧱 **SPAM Filters** – Flags or blocks incoming emails based on reputation
- 🏷️ **Email Labels** – Alerts users that an incoming email is from an outside source
- 🚫 **Email Address/Domain/URL Blocking** – Based on reputation or explicit denylist
- 📎 **Attachment Blocking** – Based on the extension of the attachment
- 🧪 **Attachment Sandboxing** – Detonates email attachments in a sandbox environment to detect malicious activity
- 🧠 **Security Awareness Training** – Conduct internal phishing campaigns

## 🧠 MITRE ATT&CK Insight

According to the [**MITRE ATT&CK Framework**](https://attack.mitre.org/techniques/T1598/#mitigations), "Phishing for Information" is described as an attempt to trick targets into divulging information. It has **three sub-techniques** - 	Application Log Content, Network Traffic Content, Network Traffic Flow.

---

## 📌 SPF (Sender Policy Framework)
![image](https://github.com/user-attachments/assets/90fd473e-6a12-4b9c-9e0b-d549add6de50)

### ❓ What is SPF?

According to [dmarcian](https://dmarcian.com/spf-survey/):

> "Sender Policy Framework (SPF) is used to authenticate the sender of an email. With an SPF record in place, Internet Service Providers can verify that a mail server is authorized to send email for a specific domain."

An SPF record is a **DNS TXT record** that lists the IP addresses authorized to send email for your domain.

---

### 🔄 SPF Workflow (Visual)
*(Image credit: dmarcian – not included in this summary)*

---

### 🔤 Example SPF Record

```txt
v=spf1 ip4:127.0.0.1 include:_spf.google.com -all
```

#### 💡 Explanation:
- `v=spf1` → Indicates the start of the SPF record
- `ip4:127.0.0.1` → Authorized sender IP (IPv4)
- `include:_spf.google.com` → Authorized sender domain
- `-all` → Reject all non-authorized senders

🧩 Refer to:
- [SPF Record Syntax Guide](https://dmarcian.com/spf-syntax-table/)
- [How to Create SPF Records](https://dmarcian.com/how-to-create-spf-record/)

---

### 🧪 Real-World SPF Record Example

Using dmarcian’s **SPF Surveyor Tool**, you can inspect domains like Twitter’s SPF setup.

---

### 🔍 SPF Check via Google Admin Toolbox

Using **Google Admin Toolbox Messageheader**, we can check SPF validation status for emails.

Example result:
> SPF Status: `softfail`

---

### ⚠️ Note:
Though this example uses **dmarcian**, there are many other tools and providers available for SPF checking and validation.

---
