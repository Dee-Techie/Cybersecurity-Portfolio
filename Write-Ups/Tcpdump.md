# 🧪 Tcpdump: The Basics

A lightning overview of `tcpdump`, a powerful CLI packet capture tool (built on `libpcap`), widely used in cybersecurity for network-level forensics :contentReference[oaicite:1]{index=1}.

---

## 🎯 Why Use It?

- Capture and inspect live network traffic
- Save packets to `.pcap` files for deeper analysis (e.g., in Wireshark)
- Filter traffic by interface, IP, port, protocol, or packet attributes

---

## 🔧 Basic Commands

| Option        | Description |
|---------------|-------------|
| `-i INTERFACE` | Choose capture interface (`any` = all) |
| `-w FILE`      | Save capture to `.pcap` file |
| `-r FILE`      | Read packets from a `.pcap` file |
| `-c COUNT`     | Stop after capturing COUNT packets |
| `-n`           | Do not resolve IPs to hostnames |
| `-nn`          | Also avoid port name resolution |
| `-v`, `-vv`, `-vvv` | Increase output verbosity :contentReference[oaicite:2]{index=2} |
| `man` | To access tcpdump's manual (e.g. man pcap-filter |

---

## 🖥️ Display Options

- `-q`: concise output
- `-e`: show link-layer (MAC) headers
- `-A`: ASCII output
- `-xx`: Hex dump
- `-X`: Combined ASCII + Hex

---

## 📌 Common Usage Examples

- Capture 50 packets on Ethernet with verbose output:  
```bash
sudo tcpdump -i eth0 -c 50 -v
```
  
- Log Wi‑Fi traffic to file until stopped:
```bash
sudo tcpdump -i wlo1 -w data.pcap
```

- Capture across all interfaces, no name resolution:
```bash
sudo tcpdump -i any -nn
```

- View the first 5 packets of a .pcap, numeric-only:
```bash
tcpdump -r traffic.pcap -c 5 -n
```
---

## 🧩 Filtering Traffic
- Host
```bash
tcpdump host example.com
tcpdump src host 10.0.0.5
tcpdump dst host 10.0.0.5
```
- Port
```bash
tcpdump port 53
tcpdump src port 80
tcpdump dst port 22
```

- Protocol
```bash
tcpdump tcp
tcpdump udp
tcpdump icmp
tcpdump arp
```

- Combining Filters (and, or, not)
```bash
tcpdump host 1.1.1.1 and tcp
tcpdump udp or icmp
tcpdump not tcp
```

Example: capture SSH on all interfaces:
```bash
sudo tcpdump -i any tcp port 22
```

## 🌐 Advanced Filtering

- Packet length
greater <bytes> / less <bytes>

- TCP flag checks (bitwise filtering)
```bash
tcpdump "tcp[tcpflags] == tcp-syn"
tcpdump "tcp[tcpflags] & tcp-syn != 0"
tcpdump "tcp[tcpflags] & (tcp-syn|tcp-ack) != 0"
```

## 🧮 Binary Operations

Before proceeding, it is worth revisiting binary operations. A binary operation works on bits (i.e., 0s and 1s). These operations take one or two bits and return a single bit as the output.
We will cover three basic binary operations: `&`, `|`, and `!`.

### ✅ AND (`&`)

The `&` (AND) operator takes **two bits** and returns `1` only if **both inputs are 1**.

| Input 1 | Input 2 | Input1 & Input2 |
|---------|---------|----------------|
| 0       | 0       | 0              |
| 0       | 1       | 0              |
| 1       | 0       | 0              |
| 1       | 1       | 1              |

---

### ✅ OR (`|`)

The `|` (OR) operator takes **two bits** and returns `1` if **at least one input is 1**.

| Input 1 | Input 2 | Input1 &#124; Input2 |
|---------|---------|---------------------|
| 0       | 0       | 0                   |
| 0       | 1       | 1                   |
| 1       | 0       | 1                   |
| 1       | 1       | 1                   |

---

### ✅ NOT (`!`)

The `!` (NOT) operator takes **one bit** and inverts it. `0` becomes `1` and `1` becomes `0`.

| Input 1 | !Input1 |
|---------|---------|
| 0       | 1       |
| 1       | 0       |

---

- Header-byte filters
  - Inspect raw header bytes using offsets:
```bash
ether[0] & 1 != 0    # multicast MAC
ip[0] & 0xf != 5     # IP packets with options
```
  - Using pcap-filter, Tcpdump allows us to refer to the contents of any byte in the header using the following syntax <ins>proto[expr:size]</ins>, where:
    - proto refers to the protocol. For example, arp, ether, icmp, ip, ip6, tcp, and udp refer to ARP, Ethernet, ICMP, IPv4, IPv6, TCP, and UDP respectively.
    - expr indicates the byte offset, where 0 refers to the first byte.
    - size indicates the number of bytes that interest us, which can be one, two, or four. It is optional and is one by default.

  - Use <ins>tcp[tcpflags]</ins> to refer to the TCP flags field. The following TCP flags are available to compare with:tcp-syn TCP SYN (Synchronize)
    - tcp-ack TCP ACK (Acknowledge)
    - tcp-fin TCP FIN (Finish)
    - tcp-rst TCP RST (Reset)
    - tcp-push TCP Push
---

## Quick Questions :
#### ❓ How many packets in traffic.pcap use the ICMP protocol? </br>
    26
  ```bash
  sudo tcpdump -r traffic.pcap icmp -n | wc
  ```
![image](https://github.com/user-attachments/assets/21af09b0-5e36-424e-ac70-d9887fa48b3f)

#### ❓ What is the IP address of the host that asked for the MAC address of 192.168.124.137?</br>
    192-168-124-148
  ```bash
  sudo tcpdump -r traffic.pcap arp and host 192.168.124.137
  ```
![image](https://github.com/user-attachments/assets/896f083c-5486-42fb-ba82-8e34685932fd)

#### ❓What hostname (subdomain) appears in the first DNS query?</br>
    mirrors.rockylinux.org
  ```bash
  sudo tcpdump -r traffic.pcap port 53
  ```
![image](https://github.com/user-attachments/assets/b3eefcbe-a32b-454d-88e4-cfb18f63834e)

---
## 🔍 Practical Tips
- Always specify an interface (-i)—running without it only checks installation.
- Use -n/-nn to speed up output and avoid clutter.
- -w files let you review traffic later using tools like Wireshark.
- Filters are your best friend—especially during issues or active analysis.
- Use -r and | wc -l to answer “how many” questions quickly.
- Combining filters (host + port + protocol) makes captures laser-focused.

---

## 🧠 Room Insights (TryHackMe)
- Understand the fundamental role of libpcap
- Capture, save, and replay packets
- Use filters to isolate traffic by type or packet attributes
- Apply bitwise logic for deep TCP-level filtering

---
<sub>🔗 References & Resources:
TryHackMe — Tcpdump Basics | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/tcpdump)</sub>



