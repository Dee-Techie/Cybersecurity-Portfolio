# 🌐 TCP/IP Model Explained

**TCP/IP** stands for **Transmission Control Protocol / Internet Protocol**. It was developed in the **1970s** by the **U.S. Department of Defense (DoD)**. 

> 💡 **Why the DoD?**  
> One of TCP/IP's strengths is its **resilience** — it was designed to ensure a network could still function even if parts were disabled (e.g., during a military attack). This robustness comes from its **adaptive routing protocols**, which can re-route traffic as the network topology changes.

---

## 🔁 OSI vs TCP/IP: Top-Down View

Previously, we discussed the OSI model from **bottom to top** (Layer 1 to Layer 7). Now, let's flip things around and go **top-down**, mapping the OSI layers to the TCP/IP model.

### 🔝 Top-to-Bottom Breakdown

- **Application Layer** (TCP/IP)  
  ↳ Combines OSI **Layers 5, 6, and 7**: Application, Presentation, Session  
  📎 *Protocols*: HTTP, HTTPS, FTP, POP3, SMTP, IMAP, Telnet, SSH

- **Transport Layer** (TCP/IP)  
  ↳ Matches OSI **Layer 4**  
  📎 *Protocols*: TCP, UDP

- **Internet Layer** (TCP/IP)  
  ↳ Matches OSI **Layer 3** (Network Layer)  
  📎 *Protocols*: IP, ICMP, IPSec

- **Link Layer** (TCP/IP)  
  ↳ Combines OSI **Layers 1 and 2** (Data Link + Physical)  
  📎 *Technologies*: Ethernet (802.3), Wi-Fi (802.11)

---

## 🧭 TCP/IP vs OSI Model Comparison

| 🌐 ISO OSI Model (Layers) | 🔀 TCP/IP Model | 📎 Protocols / Technologies |
|---------------------------|----------------|-----------------------------|
| 7 - Application <br> 6 - Presentation <br> 5 - Session | Application Layer | HTTP, HTTPS, FTP, POP3, SMTP, IMAP, Telnet, SSH |
| 4 - Transport             | Transport Layer | TCP, UDP |
| 3 - Network               | Internet Layer  | IP, ICMP, IPSec |
| 2 - Data Link <br> 1 - Physical | Link Layer | Ethernet (802.3), WiFi (802.11) |

---

## 📚 Five-Layer Variation

Many modern textbooks (e.g., *Computer Networking: A Top-Down Approach* by Kurose & Ross) describe a **five-layer Internet protocol stack**, which includes the **Physical Layer** separately:

1. Application  
2. Transport  
3. Network  
4. Link  
5. Physical
