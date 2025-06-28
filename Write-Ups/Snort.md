## 🐷 What is Snort?

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
- 👀 **Sniffer Mode** – Displays live packet data.
- 🗂️ **Packet Logger Mode** – Saves packet logs for later analysis.
- 🧱 **NIDS/NIPS Mode** – Logs/drops malicious packets using predefined rules.

### 📄 Official Description
> “Snort can be deployed inline to stop packets... It can be used as a sniffer, a logger, or a full-blown network intrusion prevention system.”

---

# 🧪 First Interaction with Snort

Before diving deep into packet analysis, let’s perform some essential **setup and verification tasks** for Snort! 🐗

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
