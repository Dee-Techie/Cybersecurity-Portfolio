# 🧠 Some Common Protocols & Ports Cheat Sheet

> A quick-reference table of protocols and their ports—essential for SOC Analysts, Network Security beginners, and Security+ learners.

---

## 🔐 Authentication & Directory Services

| **Protocol** | **Port(s)**         | **Description**                                 |
|--------------|---------------------|-------------------------------------------------|
| LDAP         | 389 (TCP/UDP)       | Lightweight Directory Access Protocol           |
| LDAPS        | 636 (TCP)           | Secure LDAP over SSL/TLS                        |
| Kerberos     | 88 (TCP/UDP)        | Authentication protocol for domain environments |
| RADIUS       | 1812/1813 (UDP)     | Remote Authentication Dial-In User Service     |
| TACACS+      | 49 (TCP)            | Cisco authentication protocol                   |

---

## 📡 Web & Application Protocols

| **Protocol** | **Port(s)**         | **Description**                      |
|--------------|---------------------|--------------------------------------|
| HTTP         | 80 (TCP)            | Insecure web traffic                 |
| HTTPS        | 443 (TCP)           | Secure web traffic (TLS/SSL)        |
| HTTP Proxy   | 8080 (TCP)          | Common proxy or alternate web port  |
| DNS          | 53 (TCP/UDP)        | Domain Name System                   |
| Web Sockets  |TCP 80 (unencrypted via HTTP), TCP 443 (encrypted via HTTPS)  | Real-time, persistent connections           |

---

## 📨 Email Protocols

| **Protocol** | **Port(s)**         | **Description**                              |
|--------------|---------------------|----------------------------------------------|
| SMTP         | 25 (TCP)            | Sending email                                |
| SMTPS        | 465 (TCP)           | SMTP over SSL/TLS                            |
| POP3         | 110 (TCP)           | Downloading email (older protocol)           |
| POP3S        | 995 (TCP)           | Secure POP3                                  |
| IMAP         | 143 (TCP)           | Interactive email access                      |
| IMAPS        | 993 (TCP)           | Secure IMAP                                  |

---

## 💻 Remote Access & Management

| **Protocol** | **Port(s)**         | **Description**                              |
|--------------|---------------------|----------------------------------------------|
| SSH          | 22 (TCP)            | Secure remote login                          |
| Telnet       | 23 (TCP)            | Insecure remote access (deprecated)          |
| RDP          | 3389 (TCP/UDP)      | Windows Remote Desktop Protocol              |
| VNC          | 5900 (TCP)          | Virtual Network Computing                    |

---

## 🧰 File Transfer Protocols

| **Protocol** | **Port(s)**         | **Description**                              |
|--------------|---------------------|----------------------------------------------|
| FTP          | 21 (TCP)            | File Transfer Protocol (commands)            |
| FTP Data     | 20 (TCP)            | FTP data transfer                            |
| SFTP         | 22 (TCP)            | Secure file transfer via SSH                 |
| FTPS         | 990 (TCP)           | FTP over SSL/TLS                             |
| TFTP         | 69 (UDP)            | Trivial FTP — no auth                        |
| SMB          | 445 (TCP)           | Windows file and printer sharing             |
| NFS          | 2049 (TCP/UDP)      | Unix file sharing                            |

---

## 🛰️ Network Services

| **Protocol** | **Port(s)**         | **Description**                              |
|--------------|---------------------|----------------------------------------------|
| DHCP         | 67/68 (UDP)         | IP address assignment (Discover → Offer → Request → Acknowledge) |
| SNMP         | 161/162 (UDP)       | Monitoring network devices                   |
| ICMP         | *No port (uses IP)* | Diagnostics: Ping, Traceroute                |
| ARP          | *No port (Layer 2)* | IP → MAC address resolution                  |

---

## 🧱 Security Monitoring & Logging

| **Tool/Protocol** | **Port(s)**         | **Description**                              |
|-------------------|---------------------|----------------------------------------------|
| Syslog            | 514 (UDP)           | Logging server messages                      |
| SIEM (Splunk etc.)| 9997 (TCP), 514 (UDP)| Ingest logs and network events               |
| NetFlow           | 2055 / 9555 (UDP)   | Flow data export from routers/switches       |

---

## 🧪 Lab & Penetration Testing Tools

| **Tool/Service**  | **Port(s)**         | **Description**                              |
|-------------------|---------------------|----------------------------------------------|
| Metasploit RPC    | 55553–55555 (TCP)   | Metasploit control services                  |
| MS RPC            | 135 (TCP)           | Microsoft Remote Procedure Call              |
| MySQL             | 3306 (TCP)          | MySQL database service                       |
| MSSQL             | 1433 (TCP)          | Microsoft SQL Server                         |
| PostgreSQL        | 5432 (TCP)          | PostgreSQL database                          |
| Elasticsearch     | 9200 (TCP)          | Search engine — often a vulnerable target    |

---

## 🧠 Tips for Memorizing Ports

- 🔢 Focus first on **well-known ports (0–1023)**.
- 🃏 Use flashcards (Anki) or quiz yourself regularly.
- 🧪 Practice with tools like **nmap**, **Wireshark**, **TryHackMe**, or **Hack The Box**.

---

> 💾 Save this list as a cheat sheet in your GitHub repo, Notion, or print it for your desk!
