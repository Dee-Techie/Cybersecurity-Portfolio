# 🌍 Introduction to IP Addressing and Routing

When you hear the term **IP address**, you might picture something like `192.168.0.1` or maybe `172.16.159.243`. Both are correct — these are **IPv4 addresses** (Internet Protocol version 4), which are still the most commonly used type of IP addresses today.

An **IP address** serves as a **unique identifier** for every device (or "host") connected to a network. Without this unique address, it would be impossible to locate or communicate with devices reliably.

## 📬 IP Address Analogy

Think of an IP address like your **home postal address**. It allows others to send you information (like mail or parcels), and ensures it reaches **only you**. Just like a postal address helps couriers find your home, an IP address lets data packets find your device in a network.

## 📘 IPv4 Basics

An IPv4 address consists of **four octets** (also called bytes), each 8 bits in size. So an IP address is **32 bits** total. Each octet can represent a number from `0` to `255`.

Example: 192.168.1.1 → 4 octets → 192 | 168 | 1 | 1

> ⚠️ IP addresses ending in `.0` and `.255` are typically reserved:
> - `.0` is used as the **network address**
> - `.255` is used as the **broadcast address**

This means the usable host addresses are the ones **in between**.

---

## 🔍 Checking Your IP Address

You can find your IP address using the following terminal commands:

- 🖥️ MS Windows command line using the command ipconfig
- 🐧 Linux and UNIX-based systems using ifconfig or ip a s (ip address show)

---
## 🌐 IPv4 vs IPv6 — What’s the Difference?

We’ve talked a lot about IPv4 — the most common type of IP address. But there’s also **IPv6**, which is increasingly being adopted to address limitations of IPv4.

### 📦 What is IPv6?

IPv6 (Internet Protocol version 6) is the **newer version of IP**, developed to overcome the shortage of IPv4 addresses. While IPv4 uses **32-bit** addresses, IPv6 uses **128-bit** addresses — allowing for a massive number of unique IPs.


### 🔍 Key Differences: IPv4 vs IPv6

| Feature                  | IPv4                            | IPv6                                      |
|--------------------------|----------------------------------|-------------------------------------------|
| 📏 Address Length        | 32 bits                         | 128 bits                                  |
| 🔢 Format                | Decimal (4 octets)              | Hexadecimal (8 blocks)                    |
| 📘 Example               | `192.168.1.1`                   | `2001:0db8:85a3:0000:0000:8a2e:0370:7334`  |
| 🌐 Total Addresses       | ~4.3 billion                    | 340 undecillion+ (that’s 10³⁸!)           |
| 🔄 NAT Required?         | Yes (for private IPs)           | No (end-to-end connectivity by design)     |
| 🔐 Built-in Security     | Optional (with IPsec)           | Required (IPsec is mandatory)             |
| ⚙️ Configuration         | Manual or DHCP                  | Auto-configuration via SLAAC              |
| 🚀 Performance           | Slightly less efficient routing | Streamlined routing & larger payloads     |


### 🤔 Why Do We Need IPv6?

- IPv4 address exhaustion — there simply aren’t enough IPv4s left.
- More devices than ever (phones, tablets, IoT, smart TVs).
- IPv6 offers better security, scalability, and simplified network configuration.


### 📘 TL;DR

- **IPv4** is still dominant but is running out of space.
- **IPv6** is the future — more secure, more scalable, and designed for modern internet use.
- You’ll encounter both in practice, so it's important to recognize and understand each format.

> 💡 **Pro Tip**: If you see an IP with lots of colons (`:`), it’s IPv6!

---

# 🏠 Public vs Private IP Addresses

There are two main types of IP addresses:

| Type    | Description                                                                 |
|---------|-----------------------------------------------------------------------------|
| 🌐 Public   | Reachable from the internet. Like your home's mailing address.             |
| 🔒 Private  | Only accessible within a local network (like your home's Wi-Fi network). Cannot access the internet directly without NAT. |

---

## 📦 Private IP Ranges (Defined by RFC 1918)

| Range                         | CIDR Notation |
|------------------------------|---------------|
| 10.0.0.0 – 10.255.255.255     | 10/8          |
| 172.16.0.0 – 172.31.255.255   | 172.16/12     |
| 192.168.0.0 – 192.168.255.255 | 192.168/16    |

> 🧠 **Tip:** Memorize these ranges! You'll often see IPs like `10.1.33.7` or `172.31.33.7` in internal networks.

---

# 📬 What is Routing?

A router is like a postal sorting facility. You hand it a package (data), and it knows how to forward it to the next destination — even if it’s not directly connected.

---

## 🔁 Routers

- Operate at **Layer 3 (Network Layer)** of the OSI model.
- Inspect **IP addresses** and determine the **best path** for the data.
- Help data travel through **multiple networks or routers** before reaching its destination.

> 💡 **Tip:** Some routers may act as **default gateways** — the main door out of your local network into the wider internet.

---

# 🧠 Summary
IP addresses uniquely identify devices on a network.

IPv4 uses 32-bit addresses divided into 4 octets.

Use ipconfig, ifconfig, or ip a s to check your IP.

Understand the difference between public and private IPs.

Routers forward data using IP addresses and make communication possible across networks.

---

<sub>🔗 References & Resources:
TryHackMe — Networking Concepts | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/networkingconcepts)</sub>

