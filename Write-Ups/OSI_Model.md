# 📚 OSI Model
The OSI (Open Systems Interconnection) model, created by the ISO (International Organization for Standardization), is a framework that explains how computers communicate over a network. It breaks the process into 7 layers, making complex networking easier to understand. A fun way to remember the layers is with the mnemonic: 'Please Do Not Throw Spinach Pizza Away.' 🍕

1. Physical (⚡)
> “Cables and electricity.”
The actual stuff — wires, fiber, Wi-Fi, definition of the binary digits 0 and 1, even blinking lights.
It’s all about transmitting raw bits.

2. Data Link (🔗)
> “Name tags for devices.”
Adds device-specific information like MAC addresses; it describes an agreement between the different systems on the same network segment on how to communicate. This layer ensures error detection and correction.
Examples of layer 2 include Ethernet, i.e., 802.3, and WiFi, i.e., 802.11.

3. Network (🌐)
> “Find the destination.”
Chooses the best path to send the data (like GPS for packets). Think IP addresses, routers, and navigation.
Examples of the network layer include Internet Protocol (IP), Internet Control Message Protocol (ICMP), and Virtual Private Network (VPN) protocols such as IPSec and SSL/TLS VPN.

4. Transport (🚚)
> “Reliable delivery guy.”
Ensures data is delivered correctly and in the right order; i.e. it enables end-to-end communication between running applications on different hosts. 
> Examples - Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) — reliable or fast, your choice.

5. Session (🕒)
> “Let’s start and manage the chat.”
It handles opening, maintaining, and closing communication between two devices. Like a host of a Zoom call.
Examples of the session layer are Network File System (NFS) and Remote Procedure Call (RPC).

6. Presentation (🎨)
> “Translator & decorator.”
It makes sure the data is in the right format — encryption, compression, and encoding happen here. Think of it as prepping the data for the party.

7. Application (💻)
> “What the user sees.”
This is where your apps live — web browsers, email, Zoom, etc. It's the layer that talks to humans.
Examples of Layer 7 protocols are HTTP, FTP, DNS, POP3, SMTP, and IMAP.

---

# Quick Summary 🌐 OSI Model – Layer-by-Layer Overview

| 🔢 Layer Number | 🧱 Layer Name       | 🛠️ Main Function                                | 📡 Example Protocols and Standards                |
|----------------|---------------------|--------------------------------------------------|--------------------------------------------------|
| 7              | Application Layer   | Providing services and interfaces to applications | HTTP, FTP, DNS, POP3, SMTP, IMAP                |
| 6              | Presentation Layer  | Data encoding, encryption, and compression        | Unicode, MIME, JPEG, PNG, MPEG                  |
| 5              | Session Layer       | Establishing, maintaining, and synchronizing sessions | NFS, RPC                                   |
| 4              | Transport Layer     | End-to-end communication and data segmentation    | UDP, TCP                                        |
| 3              | Network Layer       | Logical addressing and routing between networks   | IP, ICMP, IPSec                                 |
| 2              | Data Link Layer     | Reliable data transfer between adjacent nodes     | Ethernet (802.3), WiFi (802.11)                 |
| 1              | Physical Layer      | Physical data transmission media                  | Electrical, optical, and wireless signals       |

---

<sub>🔗 References & Resources:
TryHackMe — Networking Concepts | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/networkingconcepts)</sub>
