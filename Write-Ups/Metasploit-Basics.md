# 🚀 Metasploit Framework Summary

Metasploit is the most widely used exploitation framework, supporting all phases of a penetration testing engagement — from information gathering to post-exploitation.

---

## Versions of Metasploit

- **Metasploit Pro**: Commercial version with a GUI, automation, and task management.
- **Metasploit Framework**: Open-source CLI-based version. Focus of most training and penetration testing distributions.

---

## Key Features of Metasploit Framework

- Information gathering
- Scanning
- Exploitation
- Post-exploitation
- Exploit development
- Vulnerability research

---

## 💥 Main Components

### 1. `msfconsole`
Main CLI interface to interact with modules.

### 2. Modules
Each module performs a specific task (e.g., exploit a vulnerability, scan a system).

#### Key Concepts:
- **Vulnerability**: A flaw in the system.
- **Exploit**: Code to abuse a vulnerability.
- **Payload**: Code that runs after successful exploitation.

---

## 🧬 Module Categories

### Auxiliary
Supporting modules: scanners, fuzzers, crawlers, spoofers, etc.

Example structure:
```
auxiliary/
├── admin
├── analyze
├── scanner
├── voip
└── ...
```

### Encoders
Used to encode payloads to bypass signature-based antivirus detection.
```
encoders/
├── cmd
├── generic
├── x86
└── ...
```

### Evasion
Attempts to evade antivirus protections.
```
evasion/windows/
├── applocker_evasion_install_util.rb
├── windows_defender_exe.rb
└── ...
```

### Exploits
Organized by target OS and platforms.
```
exploits/
├── windows
├── linux
├── android
├── multi
└── ...
```

### ⏸️ NOPs
"Do-nothing" instructions used as padding (e.g., x86 NOP is `0x90`).
```
nops/
├── x64
├── x86
└── ...
```

### Payloads
Payloads run on the target system and can be:

- **Adapters**: Wrap payloads into different formats.
- **Singles**: Self-contained (e.g., add user, open calc.exe).
- **Stagers**: Setup connection channel.
- **Stages**: Downloaded by stagers, allow large payloads.

**Naming Tip**:  
- `windows/x64/shell/reverse_tcp`: Staged payload  
- `generic/shell_reverse_tcp`: Single payload

### Post
Post-exploitation modules used after a successful compromise.
```
post/
├── windows
├── linux
├── networking
└── ...
```

---

## Module Directory Location (on AttackBox)

```
/opt/metasploit-framework/embedded/framework/modules
```
Each category (e.g., exploits, payloads) has its own subfolder under this directory.
