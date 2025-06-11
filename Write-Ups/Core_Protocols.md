# 🕹⚓ Networking Core Protocols

# 🗂️ Quick Index

- [🌐 DNS: The Internet's Phonebook!](#-dns-the-internets-phonebook--)
- [🔑 Domain Name Registration](#-domain-name-registration-owning-your-corner-of-the-internet)
- [🗣️ HTTP – The Web's Plain Talk](#-http-the-webs-plain-talk--)
- [🔒 HTTPS – The Web's Secure Chat](#-https--web-commands-methods-what-your-browser-asks-for-)
- [📬 SMTP – Simple Mail Transfer Protocol](#-smtp--simple-mail-transfer-protocol)
- [📥 POP3 – Post Office Protocol v3](#-pop3--post-office-protocol-v3)
- [📧 IMAP – Internet Message Access Protocol](#-imap--internet-message-access-protocol)

## 🌐 DNS: The Internet's Phonebook! 📚 </br>
Instead of memorizing complicated IP addresses (like 172.17.2.172), DNS lets you use easy-to-remember names like google.com. When you type a website name into your browser, DNS works behind the scenes to find the correct IP address so your computer knows where to go.

### How DNS Works (Quickly!): 🏃‍♀️ </br>
DNS primarily uses UDP port 53 for its lookups. Think of it like a quick, single question and answer. If it needs to send larger information, it can use TCP port 53 as a backup.

### Common DNS Record Types (The "Entries" in the Phonebook): 📝
DNS stores different types of information, called "records," for each domain name. Here are the most common ones:

- A Record (Address): This is the most basic entry. It simply maps a website name (like example.com) to its IPv4 address (the standard internet address we're all familiar with).
Example: example.com → 172.17.2.172

- AAAA Record (Quad-A Address): Just like the A record, but for IPv6 addresses. IPv6 is the newer, much larger set of internet addresses designed for all the billions of new devices coming online.
Example: example.com → 2001:0db8:85a3:0000:0000:8a2e:0370:7334

- CNAME Record (Canonical Name): This record lets you point one domain name to another domain name. It's like having an alias!
Example: www.example.com could point to example.com. So, if you type www.example.com, DNS first tells your computer to look up example.com instead.

- MX Record (Mail Exchange): This one is special for email! When you send an email to test@example.com, your mail server uses the MX record to find out which specific server handles emails for example.com.
Example: It tells your mail server, "Send emails for example.com to mail.example.com." 📧

### Putting it Together:
When you type example.com in your browser, DNS helps it find the A record (or AAAA record) to get the IP address. But when you send an email, it looks for the MX record to find the right mail server.

> Command Line Lookup: nslookup 💻
If you're curious and want to look up this information yourself, you can use a command-line tool like nslookup. For instance, typing nslookup example.com will show you its IP address right in your terminal!

---

## 🔑 Domain Name Registration: Owning Your Corner of the Internet!
We've learned how DNS translates easy-to-remember website names (like example.com) into IP addresses. But who gets to decide what IP address example.com points to? And how do you get your own yourwebsite.com?

### Owning a Domain Name: Your Internet Authority! ✨
When you register a domain name (like example.com), you essentially "buy" the right to use that name for a period (usually one or more years). This grants you the authority to set up all its DNS records – like the A records (which IP address the website lives on), AAAA records (for IPv6 addresses), and MX records (for email servers), among others. It's like getting the official deed to your internet property! 🏡

### The "Who Is" Behind the Website: WHOIS Records 🕵️‍♀️
Part of registering a domain means providing accurate contact information about yourself or your organization. This info is then stored in something called WHOIS records.

> What is WHOIS? It's pronounced "who-is," and it's a publicly accessible database that contains details about who owns a domain name. Think of it as a public registry for domain ownership.

### What info does it show? A WHOIS record typically includes:

- The registrant's name (the owner).
- Their address.
- Their phone number.
- Their email address.
- When the domain was created and last updated.
- When it's set to expire.
- The domain registrar (the company you bought the domain from, like GoDaddy or Namecheap).

#### Privacy Options: </br>
Worried about your personal details being public? Don't fret! Most domain registrars offer privacy services. For a small fee, they can hide your personal contact information from the public WHOIS records, replacing it with their own generic contact details. This is great for privacy-conscious individuals or small businesses. 🤫

### How to Look Up WHOIS Records:
You can easily look up WHOIS information for almost any registered domain name.
- Online Services: Many websites offer free WHOIS lookup tools. Just search for "WHOIS lookup" online.
- Command Line: If you're using a Linux system, you can use the whois command directly in your terminal. For example, whois example.com would show you its details. 💻
So, while DNS makes it easy to remember website names, domain registration and WHOIS records are the foundational pieces that ensure accountability and ownership of those names on the vast internet.

---

## 🗣️ HTTP: The Web's Plain Talk 💬 </br>
HTTP (HyperText Transfer Protocol) is the web's basic language for your browser and web servers to chat. It's like talking in plain text – everyone can understand. The big catch? No encryption, so data sent over HTTP isn't private. 🚫🔒

## 🔒 HTTPS: The Web's Secure Chat 🤫 </br>
HTTPS (HyperText Transfer Protocol Secure) is simply HTTP with a security upgrade using SSL/TLS encryption. It's like talking in a secret code – only your browser and the server understand. This protects sensitive info like passwords and credit cards. Look for the padlock icon! ✅

### 🎯 Web "Commands" (Methods): What Your Browser Asks For </br>
When your browser talks HTTP/S, it uses these "commands" to tell the server what to do:

- GET ➡️: Retrieve data. "Give me this webpage!" (e.g., loading a website).
- POST ✍️: Send data to create/process. "Here's a new comment to add." (e.g., submitting a form, creating a user).
- PUT 🔄: Update/replace data completely. "Replace this whole file with my new version." (e.g., updating an entire profile).
- DELETE 🗑️: Remove data. "Delete this picture." (e.g., deleting a photo).
- PATCH ✂️: Partially update data. "Just change my email address." (e.g., changing only one field).
- HEAD 📋: Get only headers. "Just tell me the page's info, don't send the whole page." (e.g., checking if a file exists).

---

## 📁 FTP: The File Transfer Workhorse 🚀
While HTTP is built for Browse webpages, FTP (File Transfer Protocol) is specifically designed for efficiently moving files around. It can often transfer files faster than HTTP because it's optimized for that single job.

### 🛠️ How FTP Works: Commands & Ports
FTP uses a set of specific commands to manage file transfers:
- USER: Enter username.
- PASS: Enter password.
- RETR (retrieve): Download a file from the FTP server to your computer.
- STOR (store): Upload a file from your computer to the FTP server.

> An FTP server typically "listens" for commands on TCP Port 21. But here's a neat trick: the actual file data is transferred over a separate connection, often using other ports.

### 🧪 FTP in Action: A Quick Example

Imagine you want to grab a file from an FTP server:
Using a terminal FTP client:

```bash
ftp 10.10.110.98       # Connect to FTP server  
Name: anonymous         # Login with anonymous user  
Password: (leave blank)  
ls                     # List available files  
type ascii             # Set transfer mode for text files  
get flag.txt         # Download the file  
```
<img src="https://github.com/user-attachments/assets/5749216b-b80f-406b-b7f0-115474f73991" alt="FTP in action" width="600" />

---

## 📬 SMTP – Simple Mail Transfer Protocol

Just like sending a package at the post office 📦, sending an email follows a process — and that process is handled by **SMTP**.

SMTP (Simple Mail Transfer Protocol) defines how:
- 💻 Mail clients communicate with mail servers
- 📡 Mail servers talk to one another

By default, **SMTP uses TCP port 25**.

#### 🛠️ Common SMTP Commands:
- `HELO` / `EHLO` – 👋 Start the session
- `MAIL FROM:` – 🧑‍💻 Specify sender’s email address
- `RCPT TO:` – 📥 Specify recipient’s email address
- `DATA` – ✍️ Start writing the email message
- `.` – ✅ End of the email message

#### 🧪 Example (via `telnet`):
You can simulate sending an email by connecting to an SMTP server using Telnet:
```bash
telnet smtp.example.com 25
HELO yourdomain.com
MAIL FROM:<you@example.com>
RCPT TO:<friend@example.com>
DATA
Subject: Hello!
This is a test email.
.
QUIT
```
<img src="https://github.com/user-attachments/assets/30f966c7-29e8-4137-81b5-d2983a73f7d8" alt="SMTP in action" width="600" />

 #### ⚠️ Note: SMTP does not encrypt your message by default. Use SMTPS (port 465) or STARTTLS (port 587) for secure transmission 🔐.

---

## 📥 POP3 – Post Office Protocol v3

Received an email and want to download it to your local device? 🖥️ That’s what **POP3** is for!

**POP3 (Post Office Protocol v3)** is used by email clients to **retrieve messages** from a mail server. Think of it like checking your home mailbox 🏠 for new letters 📫.

- ✉️ **SMTP** = You send your mail to the post office.
- 📬 **POP3** = You pick up new mail from your personal mailbox.

By default, **POP3 uses TCP port 110**.

---

#### 🛠️ Common POP3 Commands:
- `USER <username>` – 🧑 Identify yourself
- `PASS <password>` – 🔐 Enter your password
- `STAT` – 🧮 See how many messages you have
- `LIST` – 📄 List all messages with sizes
- `RETR <msg#>` – ⬇️ Retrieve a specific message
- `DELE <msg#>` – 🗑️ Mark a message for deletion
- `QUIT` – 🚪 Exit the session (applies deletions)

---

#### 🧪 Example (via Telnet):
```bash
telnet 10.10.110.98 110
USER your_username
PASS your_password
STAT
LIST
RETR 1
DELE 1
QUIT
```
<img src="https://github.com/user-attachments/assets/eb8c2567-0f71-4d1a-98ec-57852ec5116a" alt="POP3 in action" width="600" />

#### 🧠 Tip: POP3 is simple and great for offline access, but it usually removes messages from the server after download, unlike IMAP.

---

## 📧 IMAP – Internet Message Access Protocol

Do you check your email on multiple devices — like your 📱 smartphone, 💻 laptop, or 🖥️ work computer?

**IMAP (Internet Message Access Protocol)** is designed exactly for that!

While **POP3** is great for downloading mail to a single device (and often deletes it from the server afterward), **IMAP** keeps your email **synchronized across all your devices** 📲🖥️📩.

---

#### 🔄 Why Use IMAP?

POP3 works fine when using a single device, like your desktop 🖥️. But if you want to access your inbox from your office computer, phone, or laptop — you need a better system.

✅ IMAP keeps messages on the server  
✅ Tracks what’s read, moved, or deleted across devices  
✅ Keeps your inbox updated everywhere you check it  
✅ Great for using email clients on **multiple devices**

By default, **IMAP listens on TCP port 143**, or **993** if using encryption (IMAPS 🔐).

---

### 🧠 IMAP vs POP3:

| Feature           | IMAP 📧                        | POP3 📥                       |
|------------------|--------------------------------|-------------------------------|
| Storage          | Emails stay on the server ☁️   | Emails downloaded & removed   |
| Synchronization  | Across multiple devices 🔄     | Local device only             |
| Suitable For     | Phones, tablets, multiple PCs  | Single desktop or laptop      |
| Default Port     | 143 (993 secure)               | 110 (995 secure)              |

---

#### 🛠️ Common IMAP Commands:

- `LOGIN <username> <password>` – 🔐 Authenticates the user
- `SELECT <mailbox>` – 📂 Opens a mailbox (e.g., Inbox)
- `FETCH <msg#> body[]` – ⬇️ Retrieves a specific email
- `MOVE <msg#> <folder>` – 📁 Moves email to another folder
- `COPY <msg#> <folder>` – 🗂️ Copies email to another folder
- `LOGOUT` – 🚪 Ends the session

---

#### 🧪 Example IMAP Session via Telnet:

Using telnet to connect to an IMAP server on **port 143** and retrieve a message:

```bash
user@TryHackMe$ telnet 10.10.41.192 143
Trying 10.10.41.192...
Connected to 10.10.41.192.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 ...] Dovecot (Ubuntu) ready.

A LOGIN strategos
A OK Logged in

B SELECT inbox
* 4 EXISTS
B OK [READ-WRITE] Select completed

C FETCH 3 body[]
* 3 FETCH (BODY[] {
Return-path: <user@client.thm>
To: strategos@server.thm
Subject: Telnet email

Hello. I am using telnet to send you an email!
})
C OK Fetch completed

D LOGOUT
* BYE Logging out
D OK Logout completed
Connection closed by foreign host.
```
#### ⚠️ Note: IMAP may use **more server storage**, so be mindful of storage limits with your email provider.

---
<sub>🔗 References & Resources:
TryHackMe — Networking Core Protocols | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/networkingcoreprotocols)</sub>

