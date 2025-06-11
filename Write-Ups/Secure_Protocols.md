# 🔐 Securing the Internet: From Plaintext to Encrypted Protocols

Welcome to the next part of my cybersecurity learning journey! In this writeup, we’re diving into how **SSL/TLS** (Secure Sockets Layer / Transport Layer Security) transforms everyday, plaintext protocols into secure communication channels. 🌍💬

The internet wasn’t built with security in mind — protocols like **HTTP**, **SMTP**, **POP3**, **IMAP**, and **Telnet** originally sent data in **plaintext**, meaning anyone sniffing the traffic could read your credentials, emails, or private data. 😱 Not ideal, right?

That’s where [**TLS**]() comes in — it wraps these existing protocols with **encryption**, **integrity checks**, and **authentication**, giving rise to:

- 🛡 **HTTPS** – [Secure Web Browsing](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Secure_Protocols.md#-http-vs--https--whats-the-difference)
- 📤 **SMTPS** – [Secure Mail Sending](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Secure_Protocols.md#-securing-email--web-protocols-with-tls)
- 📬 **POP3S** – [Secure Mail Download](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Secure_Protocols.md#-securing-email--web-protocols-with-tls)
- 📧 **IMAPS** – [Secure Mail Retrieval](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Secure_Protocols.md#-securing-email--web-protocols-with-tls)
- 💻 **SSH** – [Secure Remote Access Replacing Telnet](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Secure_Protocols.md#%EF%B8%8F-ssh-a-secure-telnet-replacement)
- 📑 **SFTP vs FTPS** - [Secure File Transfer](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Secure_Protocols.md#-sftp-vs-ftps--secure-file-transfers-explained)
- 🌍 **VPNs** – [Secure Tunnels over Insecure ](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Secure_Protocols.md#-vpn-virtual-private-network-explained)

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


### 🔒 HTTPS – Secure Browsing with TLS
- **HTTPS = HTTP over TLS** (default port: **443**).
- Steps involved:
  1. 🔄 TCP handshake
  2. 🤝 TLS session establishment
  3. 📄 Encrypted HTTP communication

🛡️ With TLS in place, the same HTTP data is now **fully encrypted** — preventing anyone from reading or tampering with it.

🧠 Note: In packet captures (like in Wireshark), HTTPS traffic shows up as **“Application Data”**, because the actual contents are **unreadable without the decryption key**.


### 🗝️ Decrypting HTTPS (If You Have the Key)
- Normally, you **can't see HTTPS data** unless you **own the server** or **have the session’s private key**.
- When decrypted:
  - You’ll see the familiar HTTP requests (e.g., `GET`, `POST`) as if TLS wasn’t there.
  - The underlying HTTP layer is **intact**, just **wrapped in encryption**.

---

## 📬 Securing Email & Web Protocols with TLS

Just like HTTP becomes **HTTPS** when wrapped in TLS, the same applies to common email protocols:

- **SMTP → SMTPS**
- **POP3 → POP3S**
- **IMAP → IMAPS**

These secure versions operate over **TLS**, providing 🔒 **confidentiality**, 📦 **integrity**, and 🧾 **authenticity** — the same benefits we discussed with HTTPS.


### 📊 Core Protocols vs. Secure Versions

| 📡 Protocol | 🔓 Default Port | 🔐 Secure Protocol | 🔐 TLS Port(s) |
|------------|----------------|--------------------|----------------|
| HTTP       | 80             | HTTPS              | 443            |
| SMTP       | 25             | SMTPS              | 465, 587       |
| POP3       | 110            | POP3S              | 995            |
| IMAP       | 143            | IMAPS              | 993            |
| TELNET     | 23             | SSH                | 22             |


### 💡 Important:
> - TLS only secures data in transit. It doesn’t protect data at rest or guard against weak authentication. Always combine TLS with strong password policies and MFA for complete security.
> - TLS 1.0 and 1.1 are deprecated due to security flaws; most services now require TLS 1.2 or higher, with TLS 1.3 preferred for its enhanced security and performance.
> TLS enhances HTTP **without changing TCP/IP** or the HTTP protocol itself. It adds a **security wrapper** around existing communications — making the internet safer without breaking what already works.

✅ No changes to your browser.  
✅ No changes to the server’s content.  
🔐 Just **secure-by-default** communication.

---

## 🛡️ SSH: A Secure TELNET Replacement

TELNET was once the go-to protocol for remote system access — but it had a major flaw: **everything was transmitted in plain text**, including usernames and passwords 😬. This made it easy for attackers to intercept credentials.

To fix this, **Tatu Ylönen** created the **SSH (Secure Shell)** protocol in 1995, offering encrypted communication 🧪🔐. A year later, **SSH-2** was released with stronger security, and in 1999, **OpenSSH** — the widely used open-source implementation — became the standard.


## 🔑 Key Benefits of SSH

- **Secure Authentication**: Supports password, public key, and even two-factor auth.
- **Confidentiality**: End-to-end encryption blocks eavesdropping.
- **🛡Integrity**: Ensures data hasn’t been tampered with.
- **Tunneling**: Routes other protocols securely through SSH, like a mini VPN.
- **X11 Forwarding**: Run remote GUI apps over SSH (e.g., launching Wireshark remotely).


## 📡 Usage & Ports

- **Command**: `ssh username@hostname`  
  *(Or just `ssh hostname` if the username matches your local one)*
- **Secure Port**: SSH uses **port 22**  
  *(TELNET used the insecure **port 23**)*

🧠 Extra Note:
SSH is not just for remote logins — it's also used in:
- Secure file transfer (SFTP)
- 🛠Git over SSH
- Port forwarding
- VPN-like secure tunnels

---

## 📁 SFTP vs FTPS – Secure File Transfers Explained

### 🔐 SFTP (SSH File Transfer Protocol)
- Built into the SSH protocol suite
- Uses port 22 (same as SSH)
- Provides secure file transfers over an encrypted SSH connection
- SFTP commands are Unix-like and differ from FTP
  - ✅ Simple to set up via OpenSSH – just enable SFTP in the SSH server config.

### 🔐 FTPS (File Transfer Protocol Secure)
- Adds TLS encryption to traditional FTP
- Uses port 990 by default
- Requires a TLS certificate and setup is more complex
- Not firewall-friendly due to separate control/data connections
- Similar to HTTPS, SMTPS, etc., which use TLS for security

🧠 Additional Note:
SFTP and FTPS are not the same:
  - SFTP is SSH-based
  - FTPS is TLS-based

When choosing between them:
- Use SFTP for simplicity, strong encryption, and firewall-friendliness
- Use FTPS when required for legacy systems or specific compliance standards

---

## 🌐 VPN (Virtual Private Network) Explained

## What is a VPN?  
A VPN connects multiple company offices or remote users to the main branch **virtually**, allowing devices to access shared resources as if physically on the main network. The Internet is used as the underlying infrastructure, making VPNs a cost-effective solution.  
- **V = Virtual:** Connects networks over the Internet virtually  
- **P = Private:** Encrypts data to keep it secure and private  

## 👁️‍🗨️ Why VPNs Are Needed  
- The **Internet protocols (TCP/IP)** focus on reliable packet delivery but **do not protect data confidentiality or integrity**.  
- VPNs provide **secure, encrypted tunnels** that protect data from interception or tampering during transit.  
- Ideal for companies that need **private information exchange** across distributed locations.

## ⚠️ How VPN Works  

### Company Branches  
- Remote branches run a **VPN client** that connects to a **VPN server** in the main office.  
- Traffic between branches travels through an **encrypted VPN tunnel**, while decrypted traffic flows within the private network.  

##  🧑‍💻 VPN and Internet Traffic  
- When connected, **all Internet traffic can be routed through the VPN tunnel**.  
- External websites see the **VPN server’s IP address, not the user's real IP**.  
- This helps bypass **geographical restrictions** and hides activity from the local ISP, preventing censorship or monitoring.  

---

## 👨‍💻 Important Considerations  
- Some VPNs only provide access to private networks **without routing all Internet traffic**.  
- VPN **IP leaks** and **DNS leaks** can expose your real location—use leak tests to verify.  
- VPN usage is **illegal or restricted in some countries**; always check local laws before using VPNs, especially when traveling.  

## **Types of VPNs:**  
  - **Site-to-site VPN:** Connects entire networks (offices) together.  
  - **Remote-access VPN:** Connects individual devices to a network remotely.

📲 **Encryption protocols:** Common VPN protocols include **OpenVPN, IKEv2/IPSec, WireGuard**, offering varying speeds and security levels.  
❗ **Split tunneling:** Some VPNs allow you to choose which traffic goes through the VPN and which uses the regular Internet connection, balancing privacy and performance.

*Use VPNs responsibly and always ensure your VPN provider follows strict no-logs policies to protect your privacy!* 🔒

---
<sub>🔗 References & Resources:
TryHackMe — Networking Core Protocols | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/networkingcoreprotocols)</sub>ey help secure your digital world.



