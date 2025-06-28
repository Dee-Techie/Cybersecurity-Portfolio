## 🐷 What is Snort? (WIP 🚧🚧🚧)

Snort is an open-source, **rule-based** **Network IDS/IPS** developed by **Martin Roesch** and maintained by the **Cisco Talos** team.

### 🔧 Snort Capabilities:
- Live traffic analysis
- Attack detection
- Packet logging & sniffing
- Protocol & payload analysis
- Real-time alerting
- Rule-based logic
- Cross-platform (Linux/Windows)

### 🧰 Snort Modes:
- 👀 [**Sniffer Mode**](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Snort.md#-snort-sniffer-parameters) – Displays live packet data.
- 🗂️ **Packet Logger Mode** – Saves packet logs for later analysis.
- 🧱 **NIDS/NIPS Mode** – Logs/drops malicious packets using predefined rules.

### 📄 Official Description
> “Snort can be deployed inline to stop packets... It can be used as a sniffer, a logger, or a full-blown network intrusion prevention system.”

---

# 🧪 First Interaction with Snort

Before diving deep into packet analysis, let’s perform some essential **setup and verification tasks** for Snort! 🐽

---

## 📦 Step 1: Check Snort Version

Use the following command to verify Snort is installed and to check its version:

```bash
snort -V
```

✅ Output:
```
   ,,_     -*> Snort! <*-
  o"  )~   Version 2.9.7.0 GRE (Build XXXXX)
   ''''    By Martin Roesch & The Snort Team: http://www.snort.org/contact#team
```

🔍 This gives you:
- Version number
- Copyright
- Libraries in use (libpcap, PCRE, ZLIB)

---

## ⚙️ Step 2: Test Configuration File

Use the `-T` (test mode) and `-c` (config file) flags to verify the configuration file is correct.

```bash
sudo snort -c /etc/snort/snort.conf -T
```

🔄 Output (truncated):
```
--== Initializing Snort ==--
Initializing Output Plugins!
Initializing Preprocessors!
...
Snort successfully validated the configuration!
Snort exiting
```

This ensures:
- ✔️ Snort is reading the correct configuration file.
- ⚙️ Preprocessors and plugins are initializing correctly.
- 📋 Your rules and setup are valid.

---

## 🧠 What’s in the Configuration File?

The configuration file (`snort.conf`) is the **brain** of Snort. It defines:

- 🧾 Rules
- 🔌 Plugins & Preprocessors
- 🚦 Detection mechanisms
- 🎯 Default actions
- 📤 Output settings

📌 You can maintain **multiple config files** for different use cases but **only one can be active at a time**.

---

## 🔇 Want Less Noise?

To suppress the startup banner and initialization messages, use the **quiet mode** flag:

```bash
snort -q -c /etc/snort/snort.conf
```

---

## 🔑 Common Snort CLI Parameters

| Parameter | Description |
|-----------|-------------|
| `-V` or `--version` | Shows Snort version |
| `-c <file>` | Specifies configuration file |
| `-T` | Self-test mode to validate configuration |
| `-q` | Quiet mode – suppress banner and logs |

---

🚀 **Next Step:** With your configuration validated and Snort ready, we're now set to start using Snort in different modes (Sniffer, Logger, or NIDS/NIPS)! 💪

# 🕵️‍♂️ Snort Sniffer Mode Cheat Sheet

Before diving into advanced detection, let’s explore Snort’s **Sniffer Mode** — where it acts like `tcpdump` and lets you inspect packet data in detail.

---

## 🧰 Snort Sniffer Parameters

| Parameter | Description |
|----------|-------------|
| `-v` | Verbose mode — shows TCP/IP output in the console |
| `-d` | Dumps packet payload |
| `-e` | Shows link-layer headers (e.g., TCP/UDP/ICMP) |
| `-X` | Full packet in HEX view |
| `-i` | Specify network interface (e.g., `eth0`) |

> ⚠️ For best results, simulate network traffic (like ICMP/HTTP) using a traffic-generator script.

---

## 🕸️ Sniffing by Interface (`-i`)
```bash
sudo snort -v -i eth0
```
Sniffs on the `eth0` interface with verbosity. If only one interface is present, Snort uses it by default.

---

## 👁️ Verbose Sniffing (`-v`)
```bash
sudo snort -v
```
Shows basic TCP/IP headers. Use a traffic generator to see real-time updates.

📌 Output:
```
UDP TTL:64 TOS:0x0 ID:23826 IpLen:20 DgmLen:64 DF
```

---

## 📦 Dump Packet Data (`-d`)
```bash
sudo snort -d
```
Adds packet payload (ASCII view) on top of verbose data.

📌 Output:
```
99 A5 01 00 00 01 00 00 ... google.com...
```

---

## 🧵 Dump + Link Layer Headers (`-de`)
```bash
sudo snort -de
```
Combines payload data + Ethernet (MAC) headers.

📌 Output:
```
00:0C:29:A5:B7:A2 -> 00:50:56:E1:9B:9D type:0x800 len:0x46
```

---

## 🧾 Full HEX Dump (`-X`)
```bash
sudo snort -X
```
Displays the **entire packet in HEX format**.

📌 Output:
```
0x0000: 01 00 5E 7F FF FA ...
0x0040: 48 54 54 50 2F 31 ...
```

---

## 🔄 Combine Parameters
You can mix and match:
```bash
snort -v
snort -vd
snort -de
snort -v -d -e
snort -X
```

---

## 📝 Summary

Snort's Sniffer Mode is incredibly useful for:

- 📊 Inspecting packet-level traffic
- 🔍 Debugging network issues
- 🎯 Validating live traffic in real-time

Use the right combination of flags to get the view you need!

