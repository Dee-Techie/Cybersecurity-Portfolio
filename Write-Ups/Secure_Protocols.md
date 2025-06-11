# 🔐 Securing the Internet: From Plaintext to Encrypted Protocols

Welcome to the next part of my cybersecurity learning journey! In this writeup, we’re diving into how **SSL/TLS** (Secure Sockets Layer / Transport Layer Security) transforms everyday, plaintext protocols into secure communication channels. 🌍💬

The internet wasn’t built with security in mind — protocols like **HTTP**, **SMTP**, **POP3**, **IMAP**, and **Telnet** originally sent data in **plaintext**, meaning anyone sniffing the traffic could read your credentials, emails, or private data. 😱 Not ideal, right?

That’s where [**TLS**]() comes in — it wraps these existing protocols with **encryption**, **integrity checks**, and **authentication**, giving rise to:

- 🛡 **HTTPS** – [Secure Web Browsing]()
- 📤 **SMTPS** – [Secure Mail Sending]()
- 📬 **POP3S** – [Secure Mail Retrieval]()
- 📧 **IMAPS** – [Secure Mail Retrieval]()
- 💻 **SSH** – [Secure Remote Access Replacing Telnet]()
- 🌍 **VPNs** – [Secure Tunnels over Insecure Networks]()

We’ll break down each protocol, show real examples, and explain the key benefits TLS brings to the table. 🔒🚀

---

## 🔐 TLS & Securing Plaintext Protocols

### 🔍 Before TLS (Transport Layer Security)
Back in the day, attackers could easily capture chats, emails, and passwords using packet sniffers 🗣️ in promiscuous mode. Credentials were often sent in plain text — no encryption, no protection. 🛑

### 🔐 Enter SSL/TLS
To fix this, Netscape introduced **SSL** in the '90s. Later, **TLS** replaced it — starting with TLS 1.0 (1999) and evolving into today's robust **TLS 1.3 (2018)**. TLS ensures:

- 🔒 **Confidentiality**: Data can't be read by third parties  
- 🧾 **Integrity**: Data can't be altered in transit  

### 🌐 Modern Web = Secure Web  
Many common protocols are now secured by TLS:

- `HTTP` → `HTTPS`  
- `SMTP` → `SMTPS`  
- `POP3` → `POP3S`  
- `IMAP` → `IMAPS`  
- `DNS` → `DoT` (DNS over TLS)  
- `MQTT` → `MQTTS`  
- `SIP` → `SIPS`

The added **“S”** stands for **Secure** thanks to TLS.

### 📜 Certificates & Trust  
To enable TLS, servers use **digital certificates** issued by trusted **Certificate Authorities (CAs)** 🏢:

- ✅ **CA-signed certificates**: Validated and trusted  
- 🚫 **Self-signed certificates**: Not trusted by default  
- 💸 Most CAs charge a fee, but **[Let’s Encrypt](https://letsencrypt.org)** offers free, trusted certificates

> These certificates verify identity and establish a trusted connection between clients and servers.

---
## 🌐 HTTP vs. 🔐 HTTPS – What’s the Difference?

### 🚧 HTTP – Unsecured by Default
- **HTTP (Hypertext Transfer Protocol)** runs over **TCP (port 80)**.
- All data is transmitted in **plaintext**, making it easy for attackers to **intercept** and **read** traffic using tools like **Wireshark** 🕵️.
- Steps in a typical HTTP request:
  1. 🔄 TCP three-way handshake
  2. 📄 HTTP request (e.g., `GET / HTTP/1.1`)
  3. 📤 Response received
  4. 🔚 TCP connection termination

⚠️ Without encryption, **login credentials, session data, and private messages** can be exposed to attackers sniffing the network.

---

### 🔒 HTTPS – Secure Browsing with TLS
- **HTTPS = HTTP over TLS** (default port: **443**).
- Steps involved:
  1. 🔄 TCP handshake
  2. 🤝 TLS session establishment
  3. 📄 Encrypted HTTP communication

🛡️ With TLS in place, the same HTTP data is now **fully encrypted** — preventing anyone from reading or tampering with it.

🧠 Note: In packet captures (like in Wireshark), HTTPS traffic shows up as **“Application Data”**, because the actual contents are **unreadable without the decryption key**.

---

### 🗝️ Decrypting HTTPS (If You Have the Key)
- Normally, you **can't see HTTPS data** unless you **own the server** or **have the session’s private key**.
- When decrypted:
  - You’ll see the familiar HTTP requests (e.g., `GET`, `POST`) as if TLS wasn’t there.
  - The underlying HTTP layer is **intact**, just **wrapped in encryption**.

---

### 🧩 Key Takeaway
> TLS enhances HTTP **without changing TCP/IP** or the HTTP protocol itself. It adds a **security wrapper** around existing communications — making the internet safer without breaking what already works.

✅ No changes to your browser.  
✅ No changes to the server’s content.  
🔐 Just **secure-by-default** communication.

---

## 📬 Securing Email & Web Protocols with TLS

Just like HTTP becomes **HTTPS** when wrapped in TLS, the same applies to common email protocols:

- **SMTP → SMTPS**
- **POP3 → POP3S**
- **IMAP → IMAPS**

These secure versions operate over **TLS**, providing 🔒 **confidentiality**, 📦 **integrity**, and 🧾 **authenticity** — the same benefits we discussed with HTTPS.

---

### 📊 Core Protocols vs. Secure Versions

| 📡 Protocol | 🔓 Default Port | 🔐 Secure Protocol | 🔐 TLS Port(s) |
|------------|----------------|--------------------|----------------|
| HTTP       | 80             | HTTPS              | 443            |
| SMTP       | 25             | SMTPS              | 465, 587       |
| POP3       | 110            | POP3S              | 995            |
| IMAP       | 143            | IMAPS              | 993            |

---

### 💡 Key Takeaway
> - TLS only secures data in transit. It doesn’t protect data at rest or guard against weak authentication. Always combine TLS with strong password policies and MFA for complete security.
> - TLS 1.0 and 1.1 are deprecated due to security flaws; most services now require TLS 1.2 or higher, with TLS 1.3 preferred for its enhanced security and performance.

---
<sub>🔗 References & Resources:
TryHackMe — Networking Core Protocols | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/networkingcoreprotocols)</sub>ey help secure your digital world.



