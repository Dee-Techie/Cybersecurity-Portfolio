# 🛰️ Host Discovery with Nmap

## 🎯 Goal
Identify live hosts on a network using Nmap.

---

## [🎏 NMAP Cheat Sheet](https://cdn.comparitech.com/wp-content/uploads/2019/06/Nmap-Cheat-Sheet.pdf)
---

## 🧭 Target Specification
- **IP Range**: `192.168.0.1-10`
- **Subnet**: `192.168.0.1/24`
- **Hostname**: `example.thm`

---

## 🔍 Basic Host Discovery

### Ping Scan
```bash
nmap -sn 192.168.66.0/24
```
- Lists live hosts without port scanning.
- Requires sudo or root for full capabilities.


### 🖧 Local Network Scanning
- Sends ARP requests.
- Reveals MAC addresses and vendor info.
- Example Output:
```bash
nmap -sn 192.168.66.0/24
```
- Displays host IPs, latency, MAC, and vendor.


### 🌐 Remote Network Scanning
- Cannot use ARP (cross-router).
- Uses:
  - ICMP Echo (ping)
  - ICMP Timestamp
  - TCP SYN to port 443
  - TCP ACK to port 80
- Falls back to other probes if no response.
- Example Output:
- 
```bash
nmap -sn 192.168.11.0/24
```


### 🧪 Advanced Discovery Options
- PS[portlist]: TCP SYN ping</br>
- PA[portlist]: TCP ACK ping</br>
- PU[portlist]: UDP ping</br>


### 📋 List Scan (No Traffic)
```bash
nmap -sL 192.168.0.1/24
```
- Lists targets without scanning.

---

### 📡Port Scanning

### 1. TCP Connect Scan (`-sT`)
- Completes full 3-way TCP handshake.
- More detectable.
- Suitable when SYN scans are not permitted (e.g., non-root users).

### 2. TCP SYN Scan (`-sS`)
- Sends only SYN packet; does not complete handshake.
- Stealthier and generates fewer logs.
- Requires root privileges.

### UDP Port Scanning (`-sU`)
- Used for services like DNS, NTP, SNMP, etc.
- No connection setup—just sends UDP packets.
- Closed ports typically respond with ICMP "Port Unreachable".

| Flag | Description                                 |
|------|---------------------------------------------|
| `-sT` | TCP Connect scan (full handshake)           |
| `-sS` | TCP SYN scan (stealthy)                     |
| `-sU` | UDP port scan                               |
| `-F`  | Fast scan (top 100 ports)                   |
| `-p`  | Define specific port ranges or scan all     |

> If you run nmap 10.10.100.85 with local user privileges the scan will default to connect scan (-sT).

(Refer to the cheat sheet for more options.

## 🪄 Limiting Port Range

| Option      | Description                                      |
|-------------|--------------------------------------------------|
| `-F`        | Fast scan: top 100 common ports                  |
| `-p1-65535` | Scan all ports                                   |
| `-p-`       | Equivalent to scanning all ports (1-65535)       |
| `-p10-1024` | Scan ports from 10 to 1024                       |
| `-p-25`     | Scan ports from 1 to 25                          |

---

## 🔭 OS + Service & Version Detection

| Option | Explanation                                         |
|--------|-----------------------------------------------------|
| -O     | OS detection                                        |
| -sV    | Service and version detection                       |
| -A     | OS detection, version detection, and other additions|
| -Pn    | Scan hosts that appear to be down                   |

---

## ⏰ Timing & Performance options 

| Option                                                   | Explanation                                                                                  |
|----------------------------------------------------------|----------------------------------------------------------------------------------------------|
| -T<0-5>                                                  | Timing template – paranoid (0), sneaky (1), polite (2), normal (3), aggressive (4), insane (5) |
| --min-parallelism <numprobes> or/ --max-parallelism <numprobes> | Minimum and maximum number of parallel probes                                                |
| --min-rate <number> or/ --max-rate <number>               | Minimum and maximum rate (packets/second)                                                    |
| --host-timeout                                           | Maximum amount of time to wait for a target host                                             |

---

# 🏁 Nmap Output: Controlling What You See

## 📣 Verbosity and Debugging

### Verbosity `-v`
- Use `-v` to increase the level of detail shown during the scan.
- It displays real-time progress updates such as:
  - ARP ping scans
  - DNS resolution
  - Port scanning stages

#### Increasing Verbosity
- Add more `v` characters for higher levels (e.g., `-vv`, `-vvvv`).
- Alternatively, use numeric values (e.g., `-v2`, `-v4`).
- You can even press `v` during an ongoing scan to increase verbosity.

### Debugging `-d`
- Use `-d` for detailed debugging output.
- Increase levels by adding more `d` characters (e.g., `-dd`, `-ddd`) or use `-d0` to `-d9`.
- Be cautious: high levels (like `-d9`) produce thousands of lines of output.

---

## 💾 Saving Scan Reports

Nmap supports multiple output formats for saving scan results:

| Option           | Description                                    |
|------------------|------------------------------------------------|
| `-oN <filename>` | Normal (human-readable) output                |
| `-oX <filename>` | XML format                                     |
| `-oG <filename>` | Grep-able output for tools like `grep`/`awk`   |
| `-oA <basename>` | Outputs in all three formats: `.nmap`, `.xml`, `.gnmap` |

**Example:**
```bash
nmap -sS 192.168.1.0/24 -oA scan_report
```
#### This command will generate:
- scan_report.nmap
- scan_report.xml
- scan_report.gnmap

---

## 🕹️Basic Questions & Answers :

❓What is the last IP address that will be scanned when your scan target is 192.168.0.1/27?
  192.168.0.31

  ```bash
  nmap -sL 192.168.0.1/27
  ```
<img src="https://github.com/user-attachments/assets/5b5d4844-81c6-4b00-a9ff-12617c97dd83" alt="Question1" width="700"/></br>
</br>

---
❓How many TCP ports are open on the target system at 10.10.31.243?
  6

  ```bash
  nmap -sT 10.10.31.243
  ```
<img src="https://github.com/user-attachments/assets/d65cae59-4b85-4308-a70a-858bbfc4665a" alt="Question2" width="700" />

---

<sub>🔗 References & Resources:
- TryHackMe — Nmap Basics | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/nmap)</sub>
- [For Questions explanation](https://jebitok.hashnode.dev/networking-nmap-the-basics-tryhackme-cm2qp5hht000109lb7eq7aqu7)</sub>
