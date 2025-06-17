# 🎩 Introducing John the Ripper (Jumbo John): A Powerful Password Cracking Tool

In the realm of cybersecurity and ethical hacking, password cracking is a critical skill for testing system defenses and recovering lost credentials. Among the many tools available, **John the Ripper (JtR)** stands out as one of the most versatile and widely-used password cracking utilities.

Originally developed for Unix-based systems, John the Ripper has evolved to support a wide range of platforms and hash types, making it a go-to tool for penetration testers and security professionals.

Today, we'll go through the practical use of John the Ripper - Jumbo John across several real-world scenarios, including:

- [Basic installation]()
- Cracking **Windows authentication hashes** extracted from SAM files.
- Attacking **Linux `/etc/shadow` hashes** to reveal user passwords.
- Breaking into **password-protected ZIP and RAR archives**, a common challenge in forensic investigations.
- Cracking encrypted **SSH private keys**, useful when access control testing or recovering access to locked-down systems.

---

## 🛠️ John the Ripper Versions

There are two main types of John the Ripper:

| Version       | Description                                           |
|---------------|-------------------------------------------------------|
| Core          | Standard version with basic features                  |
| Jumbo John    | Community-enhanced version with extended functionality (includes tools like `zip2john`, `rar2john`) |

---

## ✅ Installation Guide

### 🔒 Pre-installed Environments

| Platform         | Status              | Notes                                      |
|------------------|---------------------|--------------------------------------------|
| Kali Linux       | ✅ Already Installed | Includes Jumbo John                        |
| Other Pentest VMs| ✅ Most include it   | Run `john` in terminal to confirm version  |

> To check version:  
> ```bash
> john
> ```
> Output should include something like:  
> `John the Ripper 1.9.0-jumbo-1+bleeding-ffd18e6b5d 2024-09-29 04:20:54 +0200 OMP [linux-gnu 64-bit x86_64 AVX2 AC]
Copyright (c) 1996-2024 by Solar Designer and others
Homepage: https://www.openwall.com/john/`

---

### 🐧 Installing on Linux

| OS         | Command                        | Notes                                         |
|------------|---------------------------------|-----------------------------------------------|
| Ubuntu     | `sudo apt install john`         | May lack Jumbo-specific tools                 |
| Fedora     | `sudo dnf install john`         | Same limitations as above                     |
| Other Distros | Build from source (recommended) | Follow official Jumbo John install guide      |

> ✅ **Building from source is recommended** if you need tools like `zip2john`, `rar2john`, etc.

### 🪟 Installing on Windows

- Download pre-compiled **Jumbo John binaries**:
  - [64-bit version](https://www.openwall.com/john/)
  - [32-bit version](https://www.openwall.com/john/)

Unzip the archive and follow the included instructions to run JtR.

---

## 📚 Wordlists

A **wordlist** is essential for dictionary-based password attacks.

| Source               | Location/Download                           | Notes                                       |
|----------------------|----------------------------------------------|---------------------------------------------|
| Kali/AttackBox       | `/usr/share/wordlists`                      | Pre-installed                               |
| SecLists Repository  | `/Passwords/Leaked-Databases`              | Includes `rockyou.txt.tar.gz`               |
| rockyou.txt          | Extract using: `tar xvzf rockyou.txt.tar.gz`| Widely used password list from 2009 breach  |

---

# 🔓 Cracking Hashes with John the Ripper

## 🧰 Basic Syntax

```bash
john [options] [file path]
```

| Component   | Description                                                  |
|-------------|--------------------------------------------------------------|
| `john`      | Invokes John the Ripper                                      |
| `[options]` | Various flags to specify behavior                            |
| `[file]`    | File containing hashes (no path needed if in same directory) |

---

## ⚙️ Automatic Cracking

Use this if you’re unsure about the hash format:

```bash
john --wordlist=[path to wordlist] [path to file]
```

📌 **Example:**
```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt
```

| Option         | Description                          |
|----------------|--------------------------------------|
| `--wordlist=`  | Enables dictionary attack mode       |
| `rockyou.txt`  | Common password list used for attack |

---

## 🔍 Identifying Hash Types

Sometimes John can't automatically detect the hash format. You can identify it using:

### 🔧 Tool: `hash-identifier`

1. Download:
   ```bash
   wget https://gitlab.com/kalilinux/packages/hash-identifier/-/raw/kali/master/hash-id.py
   ```
2. Run:
   ```bash
   python3 hash-id.py
   ```

🎯 This tool will return possible hash types like:
```
[+] MD5
[+] Domain Cached Credentials - MD4(MD4(($pass)).(strtolower($username)))
```
![image](https://github.com/user-attachments/assets/4c55dd58-cc25-48ab-9f86-f79290cad127)
![image](https://github.com/user-attachments/assets/7a7fe4cd-3ffd-44af-9694-13e7ea33d60d)
![image](https://github.com/user-attachments/assets/6e1f09b0-1cbe-4ef1-bfd2-5e6a4750462a)

---

## 🎯 Format-Specific Cracking

Once the hash format is identified, use:

```bash
john --format=[format] --wordlist=[path] [hash_file]
```

📌 **Example:**
```bash
john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt
```

| Option         | Description                                              |
|----------------|----------------------------------------------------------|
| `--format=`    | Specifies exact hash type                                |
| `raw-md5`      | Format identifier for raw MD5 hashes                     |
| `rockyou.txt`  | Password list used for the dictionary attack             |

> ⚠️ **Note**: Prefix common hash types with `raw-` (e.g., `raw-md5`, `raw-sha1`).  
> Use `john --list=formats` to view all supported formats.

```bash
john --list=formats | grep -iF "md5"
```

---

## ✅ Summary Table

| Task                             | Command Example                                                                 |
|----------------------------------|----------------------------------------------------------------------------------|
| Auto-crack unknown hash          | `john --wordlist=rockyou.txt hash.txt`                                          |
| Identify hash type               | `python3 hash-id.py` (after downloading)                                        |
| Crack specific hash format       | `john --format=raw-md5 --wordlist=rockyou.txt hash.txt`                         |
| List supported hash formats      | `john --list=formats`                                                           |
