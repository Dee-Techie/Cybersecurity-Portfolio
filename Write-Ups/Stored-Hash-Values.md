# 🔍 Recognising Password Hashes

Understanding how to recognize and analyze password hashes is key from an **offensive security** perspective. When starting with a hash, you need to determine:

- ✅ What type of hash it is
- 🔓 Whether it can be cracked
- 🧠 What tools and context can help identify it

---

## 🛠️ Hash Recognition Tools

- Tools like [`hashID`](https://pypi.org/project/hashID/) exist for **automated hash recognition**.
- ⚠️ However, they are **unreliable for some formats** — especially hashes without prefixes.
- Use both:
  - 🔧 **Tools**
  - 🧠 **Context clues** (e.g., where the hash was found)

---

## 🐧 Linux Password Hashes

- Stored in: `/etc/shadow` (previously in `/etc/passwd`)
- File format: `username:$prefix$options$salt$hash:...`
- Prefix indicates the **hashing algorithm** used.

### 🔑 Common Linux Prefixes and Algorithms

| Prefix   | Algorithm Description |
|----------|------------------------|
| `$y$`    | yescrypt (default/recommended) |
| `$gy$`   | gost-yescrypt |
| `$7$`    | scrypt |
| `$2a$`, `$2b$`, `$2y$` | bcrypt (Blowfish-based) |
| `$6$`    | sha512crypt |
| `$md5`   | SunMD5 |
| `$1$`    | md5crypt |

### 📌 Example Entry in `/etc/shadow`

```bash
strategos:$y$j9T$76UzfgEM5PnymhQ7TlJey1$/OOSg64dhfF.TigVPdzqiFang6uZA4QA1pzzegKdVm4:...
```

- `$y$` → Algorithm: yescrypt
- `j9T` → Options/parameters
- `76UzfgEM5PnymhQ7TlJey1` → Salt
- `/OOSg64dhfF.TigVPdzqiFang6uZA4QA1pzzegKdVm4` → Hashed value

---

## 🪟 Windows Password Hashes

- Stored in: `SAM (Security Accounts Manager)`
- Hashing algorithm: **NTLM** (based on MD4)
- Context is crucial: NTLM hashes look like MD4/MD5
- Tools like `mimikatz` can extract these hashes

🔑 Windows uses:
- **NT Hashes**
- **LM Hashes**

---

## 🧠 Additional Notes

- Use [Hashcat Example Hashes](https://hashcat.net/wiki/doku.php?id=example_hashes) to look up specific formats and modes.
- Context, length, prefix, and structure help identify hash types.
- 🔍 Don’t underestimate **manual research** for unknown or proprietary hashes.

---

## 🧩 Quiz Answers

| Question                                                       | Answer    |
|----------------------------------------------------------------|-----------|
| What is the hash size in yescrypt?                             | `256`. The hash size in yescrypt is 256 bits. This is because yescrypt relies on SHA-256 as a core component of its cryptographic security. Specifically, yescrypt uses SHA-256, HMAC, and PBKDF2 for its password hashing and key derivation.     |
| What’s the Hash-Mode listed for Cisco-ASA MD5?                 | `2410`. The Hash-Mode for Cisco-ASA MD5 in hashcat is 2410. It's also listed as cisco_asa in Passlib and asa-md5 in John the Ripper.     |
| What hashing algorithm is used in Cisco-IOS if it starts with $9$? | `scrypt`. If a Cisco-IOS password hash begins with \(9\), it indicates that the scrypt algorithm was used to generate the hash. This algorithm is considered more secure than older algorithms like MD5 and has been implemented in later Cisco operating systems. The scrypt algorithm uses an 80-bit salt and is not NIST (National Institute of Standards and Technology)-approved.  |
