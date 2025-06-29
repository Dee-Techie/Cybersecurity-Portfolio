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

### ❓ What is SPF?

According to [dmarcian](https://dmarcian.com/spf-survey/):

> "Sender Policy Framework (SPF) is used to authenticate the sender of an email. With an SPF record in place, Internet Service Providers can verify that a mail server is authorized to send email for a specific domain."

An SPF record is a **DNS TXT record** that lists the IP addresses authorized to send email for your domain.

---

### 🔄 SPF Workflow
<img src="https://github.com/user-attachments/assets/8531c504-67cf-475d-8994-dab3a453166c" alt="SPF" width="800" />

> Note:  Credit to dmarcian for the above image.
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

## 📧 What is DKIM?

**DKIM (DomainKeys Identified Mail)** is an open standard for **email authentication**, used to ensure that an email has not been tampered with in transit and truly comes from the sender's domain. It works by using **cryptographic signatures** linked to domain name records.

> 📝 _"DKIM is used for the authentication of an email that’s being sent... it can survive forwarding, which makes it superior to SPF."_ — [dmarcian](https://dmarcian.com)

### 🔐 DKIM Record Example
```
v=DKIM1; 
k=rsa; 
p=MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxTQIC7vZAHHZ7WVv/5x/qH1RAgMQI+y6Xtsn73rWOgeBQjHKbmIEIlgrebyWWFCXjmzIP0NYJrGehenmPWK5bF/TRDstbM8uVQCUWpoRAHzuhIxPSYW6k/w2+HdCECF2gnGmmw1cT6nHjfCyKGsM0On0HDvxP8I5YQIIlzNigP32n1hVnQP+UuInj0wLIdOBIWkHdnFewzGK2+qjF2wmEjx+vqHDnxdUTay5DfTGaqgA9AKjgXNjLEbKlEWvy0tj7UzQRHd24a5+2x/R4Pc7PF/y6OxAwYBZnEPO0sJwio4uqL9CYZcvaHGCLOIMwQmNTPMKGC9nt3PSjujfHUBX3wIDAQAB
```

### 🔍 Record Breakdown:
- **`v=DKIM1`** → DKIM version (optional)
- **`k=rsa`** → Key type used (RSA is default and most common)
- **`p=`** → Public key (matches with private key from your mail server)

📚 Resources:
- [What is DKIM](https://dmarcian.com/dkim-selectors/)
- [Validity Guide](https://knowledge.validity.com/s/articles/DKIM-DNS-record-overview?language=en_US)

---

## 📂 DKIM in Action

🔍 A snippet of an email header (flagged as spam) can show whether **DKIM passed or failed**. You’ll often find this info in fields like:
```
Authentication-Results: dkim=pass (or fail)
```

---

## 🔐 What is DMARC?

**DMARC (Domain-based Message Authentication, Reporting, & Conformance)** builds on SPF and DKIM by providing a **policy framework** and **feedback mechanism** for domain owners. It ensures alignment between email headers and sender domains to prevent spoofing.

> 🧠 _"DMARC uses alignment to tie SPF and DKIM results to the actual content of the email."_ — [dmarcian](https://dmarcian.com)

### 📘 DMARC Record Example
```
v=DMARC1; p=quarantine; rua=mailto:postmaster@website.com
```

### 📌 Record Breakdown:
- **`v=DMARC1`** → Must be in all caps and is **not optional**
- **`p=quarantine`** → If checks fail, send email to spam
- **`rua=mailto:...`** → Send **aggregate reports** to this address

📚 Helpful Links:
- [DMARC Overview](https://dmarc.org/overview/)
- [DMARC Record Guide](https://dmarcian.com/what-is-a-dmarc-record/)
- [DMARC Alignment](https://dmarcian.com/alignment/)

---

## 🧪 Domain Health Checker Example (Microsoft)

Using [dmarcian's Domain Health Checker](https://dmarcian.com/domain-checker/), we can evaluate Microsoft’s domain:

✅ Microsoft **passed** all major checks — SPF, DKIM, and DMARC!

### 🔍 DMARC Result:
```text
Policy: reject
```
📤 Emails that fail DMARC validation will be **rejected**, not just sent to spam — a strong posture against spoofing.

---
## 📧 What is S/MIME?

Per Microsoft: **"S/MIME (Secure/Multipurpose Internet Mail Extensions) is a widely accepted protocol for sending digitally signed and encrypted messages."**

### ✨ Key Features
- **Digital Signatures**: Ensures integrity and authenticity.
- **Encryption**: Protects message confidentiality.

### 🔐 How it Works
1. Bob obtains a **digital certificate** containing his public key.
2. Bob signs an email with his **private key**.
3. Mary uses **Bob’s public key** to decrypt and verify the message.
4. Mary replies with her certificate; both can now securely communicate.

![27cb0b439d172324f453e57c9cbf7ac0](https://github.com/user-attachments/assets/f23e9c8e-9690-4d82-ae05-dc1a140297b1)


🧠 **Nonrepudiation**: The uniqueness of a signature prevents the owner of the signature from disowning the signature.

---

## 🖋️ S/MIME in Exchange Online

S/MIME supports:
- **Encryption**: Keeps message content secure.
- **Digital Signatures**: Verifies sender’s identity.

### 🛡️ Digital Signatures Provide:
- **Authentication**: Validates sender identity.
- **Nonrepudiation**: Prevents sender from denying their message.
- **Data Integrity**: Ensures message hasn't been tampered with.

⚠️ Note: Digital signatures **do not** provide confidentiality alone.

---

## 🔒 S/MIME Encryption

Encryption solves information disclosure and ensures:
- **Confidentiality**: Only the intended recipient can read the message.
- **Data Integrity**: Verifies that content hasn’t changed.

⚠️ Encryption **does not** authenticate the sender or provide nonrepudiation.

---

## 🔗 Related Technologies

- **TLS**: Encrypts communication routes.
- **BitLocker**: Encrypts data on disk.
- **Microsoft Purview Message Encryption**:
  - Policy-based
  - Doesn’t rely on certificates
  - Admin-configurable and brand-customizable

---

## 🔑 Public Key Cryptography

Public key cryptography (aka asymmetric encryption) uses **RSA** and consists of:

- **Public Key**: Shared openly.
- **Private Key**: Kept secret.

### 💡 Enables:
- **Encryption & Decryption**: Secure message exchange.
- **Nonrepudiation**: Prevents sender from denying message origination.

🔁 Use public key to encrypt; private key to decrypt.
✍️ Use private key to sign; public key to verify.

⚠️ Public key encryption is **computationally expensive** and is typically used to **transmit symmetric keys**, which are then used for bulk encryption.

---

## 📚 References
- [Microsoft S/MIME Guide](https://learn.microsoft.com/en-us/exchange/policy-and-compliance/smime)
- [dmarcian on DKIM](https://dmarcian.com/dkim-selectors/)
- [dmarcian on DMARC](https://dmarcian.com/what-is-a-dmarc-record/)
- [Public Key Cryptography - Microsoft](https://learn.microsoft.com/en-us/windows/win32/seccrypto/public-key-cryptography)

---

## ✅ Summary of Email Security Protocols

- **SPF (Sender Policy Framework)** 🧾  
  Verifies that the sending mail server is authorized to send emails on behalf of your domain. Helps prevent spoofing based on IP address.

- **DKIM (DomainKeys Identified Mail)** 🔏  
  Authenticates the integrity of email content by attaching a digital signature linked to your domain. The signature is validated via a public key in DNS. Survives email forwarding.

- **DMARC (Domain-based Message Authentication, Reporting & Conformance)** 🧠  
  Aligns SPF and DKIM results to define policies (none, quarantine, reject). Provides reporting and enforces action against emails failing authentication.

- **S/MIME (Secure/Multipurpose Internet Mail Extensions)** ✉️🔐  
  Uses public key cryptography for end-to-end **encryption** and **digital signing** of emails. Ensures message **confidentiality**, **authenticity**, and **non-repudiation** between sender and recipient.

---

💡 When combined, these protocols create a **robust email security posture** that protects users, prevents impersonation, and builds trust in your communications.

🛡️ **Best Practices**:  
✔️ Implement all four protocols correctly  
✔️ Monitor with DMARC reports  
✔️ Regularly audit DNS records and encryption settings  
✔️ Train users to recognize secure (and suspicious) email behavior

🛡️ Stay secure. Configure properly. Verify regularly!
