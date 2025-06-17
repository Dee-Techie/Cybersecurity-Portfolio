# 🔓 Password Cracking

## 🌈 Cracking Unsalted vs. Salted Hashes

- **Hashing is not encryption** — you can't "decrypt" a hash.
- Passwords must be cracked by hashing potential inputs and comparing them to the target hash.
- **Rainbow Tables** work only on **unsalted** hashes.
- If a **salt** is used, you must:
  - Combine the password with the salt.
  - Hash the result and compare to the original hash.
- **Tools commonly used**:
  - 🧰 [Hashcat](https://hashcat.net/hashcat/)
  - 🪓 John the Ripper

---

## ⚡ Cracking Passwords with GPUs

- **GPUs** (Graphics Processing Units):
  - Have thousands of cores.
  - Accelerate specific hash functions extremely fast.
  - Ideal for cracking MD5, SHA-1, and similar fast hashes.
- ⚠️ **Bcrypt** is designed to **resist GPU-based cracking** by being slow on all hardware types.

---

## 🖥️ Running Cracking Tools in Virtual Machines (VMs)

- **GPUs are not natively accessible in most VMs**.
  - You’d need **GPU passthrough** (advanced setup).
- **VMs are slower** due to virtualisation overhead.
- Recommendations:
  - ✅ Run **Hashcat** on host OS for GPU access.
  - ✅ Run **John the Ripper** in a VM (CPU-based cracking).

---

## 🧪 Example: Cracking with Hashcat

- Basic Hashcat syntax:
  ```bash
  hashcat -m <hash_type> -a <attack_mode> <hashfile> <wordlist>
  -m: Numeric code for the hash type (e.g. 1000 for NTLM).
  -a: Attack mode (0 for straight wordlist attack).
  hashfile: File with the hash(es).
  wordlist: Wordlist file (e.g. rockyou.txt).
  ```
  
Example:
```bash
hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt
Cracks bcrypt hashes using rockyou.txt.
  ```

## Questions :

- ❓Use hashcat to crack the hash, $2a$06$7yoU3Ng8dHTXphAg913cyO6Bjs3K5lBnwq5FJyA6d01pMSrddr1ZG, saved in ~/Hashing-Basics/Task-6/hash1.txt.
  - 85208520
    - Method 1 : hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt
    - Method 2 : john --format=bcrypt --wordlist=rockyou.txt ~/Hashing-Basics/Task-6/hash1.txt

- ❓Use hashcat to crack the SHA2-256 hash, 9eb7ee7f551d2f0ac684981bd1f1e2fa4a37590199636753efe614d4db30e8e1, saved in saved in ~/Hashing-Basics/Task-6/hash2.txt.
  - halloween
    - Method 1 : hashcat -m 1400 -a 0 hash.txt /usr/share/wordlists/rockyou.txt
    - Method 2 : Use [CrackStation](https://crackstation.net/)
    ![image](https://github.com/user-attachments/assets/95c6a06a-64aa-4bc6-a077-e94e19868434)

- ❓Use hashcat to crack the hash, $6$GQXVvW4EuM$ehD6jWiMsfNorxy5SINsgdlxmAEl3.yif0/c3NqzGLa0P.S7KRDYjycw5bnYkF5ZtB8wQy8KnskuWQS3Yr1wQ0, saved in ~/Hashing-Basics/Task-6/hash3.txt.
  - spaceman
    - Method 1 : hashcat -m 1800 -a 0 hash.txt /usr/share/wordlists/rockyou.txt (It uses <ins>sha512crypt $6$, SHA512 (Unix) 2</ins> so the hash mode is 1800)
    - Method 2 : Use [Hashes.com](https://hashes.com/en/decrypt/hash)
     ![image](https://github.com/user-attachments/assets/394bdecc-1db7-4409-9cc2-f3e73b7eca7f)

- ❓Crack the hash, b6b0d451bbf6fed658659a9e7e5598fe, saved in ~/Hashing-Basics/Task-6/hash4.txt.
  - funforyou
    - Method 1 : Use [CrackStation](https://crackstation.net/)
     ![image](https://github.com/user-attachments/assets/8e2a1c3e-854e-4666-8967-303440c4b8fc)
    - Method 2 : Use [Hashes.com](https://hashes.com/en/decrypt/hash)</br>
     ![image](https://github.com/user-attachments/assets/9ac92961-ffa0-45c6-8657-4c2abffdb2a5)

---

<sub>🔗 References & Resources: TryHackMe — Hashing Basics | Cyber Security 101 (THM) TryHackMe</sub>

