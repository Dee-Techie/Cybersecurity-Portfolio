# 🔐 Public Key

Imagine a private conversation over coffee—only - you and your partner can hear each other, trust each other's identity, and know the message isn't being altered. In cybersecurity, this maps to four goals:

- **Authentication**: You're talking to the right person.  
- **Authenticity**: The message is really from them.  
- **Integrity**: The message hasn't been changed/tampered with.  
- **Confidentiality**: No one else can hear it.

---

# 🔏 RSA: Cracking the Code of Secure Communication

**RSA** is a widely-used public key cryptographic algorithm designed to securely transmit data over insecure channels—where eavesdropping is assumed.

## 💡 Why RSA is Secure

RSA’s strength lies in the **mathematical challenge of factoring large numbers**. While multiplying two large primes is easy, reversing the process i.e. factoring that product back into its original primes (finding the original primes from their product) is extremely difficult—especially when using 300+ digit numbers in real-world RSA systems.

Example:
- Prime 1: 982451653031  
- Prime 2: 169743212279  
- Product: 166764499494295486767649  


## 🔐 How RSA Works

RSA uses **asymmetric encryption**:
- **Public Key (n, e)**: Used for encryption; shared openly.
- **Private Key (n, d)**: Used for decryption; kept secret.

### 🧮 Simplified Example

1. Bob picks two primes:  
   `p = 157`, `q = 199`  
   → `n = p × q = 31243`

2. Compute φ(n):  
   `φ(n) = (p-1)(q-1) = 30888`

3. Choose `e = 163`, such that it’s relatively prime to φ(n)  
   Compute `d = 379`, where `e × d ≡ 1 mod φ(n)`

   - Public Key: `(n, e) = (31243, 163)`
   - Private Key: `(n, d) = (31243, 379)`

4. Encrypt message `m = 13`:  
   `c = m^e mod n = 13^163 mod 31243 = 16341`

5. Decrypt ciphertext:  
   `m = c^d mod n = 16341^379 mod 31243 = 13`

*In real scenarios, primes are 300+ digits long, making brute-force factorization infeasible.*

## 🔍 RSA in CTFs

RSA often shows up in Capture the Flag (CTF) challenges. You may be asked to:
- Derive missing values
- Decrypt ciphertext
- Reverse-engineer weak keys

### 🧰 Common CTF RSA Tools
- [**RsaCtfTool**](https://github.com/RsaCtfTool/RsaCtfTool) – Swiss Army knife for RSA exploitation
- [**rsatool**](https://github.com/ius/rsatool) – Useful for key parsing and inspection

### 🔢 Key RSA Variables to Know
| Variable | Meaning                      |
|----------|------------------------------|
| `p, q`   | Large prime numbers          |
| `n`      | Product of `p × q`           |
| `e`      | Public exponent (part of key)|
| `d`      | Private exponent             |
| `m`      | Original message (plaintext) |
| `c`      | Encrypted message (ciphertext)|

CTF tasks often provide a subset of these values. 

---

> 📌 RSA underpins much of modern secure communication—and with the right tools and insight, even the math becomes manageable.

---
<sub>🔗 References & Resources:
TryHackMe — Cryptography Public Key | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/publickeycrypto)</sub>




