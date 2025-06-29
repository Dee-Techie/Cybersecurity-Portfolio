# 🧪 Lab Blog: Analyzing SMTP Traffic with Wireshark

## 📘 Scenario

In this lab, I examined a PCAP file containing SMTP traffic to identify email behaviors, understand SMTP status codes, and uncover potentially malicious activity. This exercise was performed using **Wireshark** only.

## 🧰 Tool Used

- 🖥️ **Wireshark** – for deep packet inspection and SMTP protocol analysis

---

## 🔎 Objective

The goal of this lab was to:
- Identify SMTP status codes within packet data
- Understand SMTP communication flows
- Investigate rejected/bounced email traffic
- Examine file attachments transferred via SMTP

---

## 📂 Filters & Insights

### 🔍 What Wireshark filter can you use to narrow down the packet output using SMTP status codes?

```bash
smtp.response.code
```

This filter helps you locate packets with specific SMTP response codes like 220 (Service Ready), 250 (Requested mail action okay), 550 (Mailbox unavailable), etc.

---

### 🧾 What was the text description for status code **220**?

```
Service ready
```

💡 This response code indicates the server is ready to proceed with the SMTP session.

![image](https://github.com/user-attachments/assets/1dee8acb-445d-480b-bb05-f96d4523c986)

---

### 🚫 What packet showed an email was blocked via **spamhaus.org**?

- **Packet Number & Status Code**:  
  ```
  156,553
  ```

- **Message**:  
  ```
  mailbox name not allowed
  ```

✉️ This indicates the message was rejected due to a policy block likely triggered by DNSBL (DNS-based Blackhole List).

![image](https://github.com/user-attachments/assets/d4d3c587-ee0e-4856-8855-2630ba1f11c4)

---

### 📤 What is the status code that typically precedes an SMTP `DATA` command?

This is typically **354**, which tells the client to start sending the message body.

---

### 🌐 What port was the SMTP traffic using?

```
25
```

Port 25 is the default for sending SMTP messages between servers.

---

### 🧮 How many packets are SMTP specifically?

```
512
```
![image](https://github.com/user-attachments/assets/3aa80912-e362-4ea0-bfb1-8f3161c4a7cd)

This shows a decent volume of email communication for further inspection.

---

### 🌐 What is the **source IP address** for all SMTP traffic?

```
10.12.19.101
```

This is likely the internal mail server or compromised host responsible for sending the SMTP traffic.

![image](https://github.com/user-attachments/assets/553ba761-64a7-4342-a972-7cf07f81e265)

---

## 📎 Attachments in SMTP Traffic

### 📄 What is the filename of the **third** file attachment?

```
attachment.scr
```

`.scr` files are often suspicious as they are associated with executable screen savers, commonly used in malware delivery.

![image](https://github.com/user-attachments/assets/cc008501-c674-461b-a83b-505e0fd4c9a9)


### 📄 What is the filename of the **last** file attachment?

```
.zip
```
![image](https://github.com/user-attachments/assets/c7d42ffa-6855-4a64-b531-e10d33a6298e)

---

## ✅ Outcome

- Gained hands-on experience analyzing **SMTP protocol** in network traffic
- Identified and interpreted **SMTP status codes**
- Investigated **blocked messages** and their reasons
- Retrieved and reviewed **file attachments** from email flows

---

### 🔗 References
- [THM Room](https://tryhackme.com/room/phishingemails4gkxh)
- [Wireshark: Display Filter Reference - Internet Message Format](https://www.wireshark.org/docs/dfref/i/imf.html)
- [Wireshark: Display Filter Reference: Simple Mail Transfer Protocol](https://www.wireshark.org/docs/dfref/s/smtp.html)
- [SMTP Codes](https://www.mailersend.com/blog/smtp-codes)
