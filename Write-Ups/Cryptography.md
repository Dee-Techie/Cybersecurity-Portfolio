# 🧠 Welcome to Cryptography Unlocked!

Ever wondered how your passwords stay safe, or how hackers crack encrypted messages? You're in the right place! This mini-series makes cryptography **fun**, **practical**, and totally **beginner-friendly**. No math degree required—just curiosity and a love for secrets. 🕵️‍♂️

Here we'll cover the basics of how digital secrets are kept (or broken), one post at a time. From locking data with keys to cracking passwords with tools, we're covering the good stuff. Ready? Let's go! 💥

---

## 🔍 Topics Covered

| 🔢 # | 🔐 Topic              | 📝 Description                                  |
|-----|------------------------|-----------------------------------------------|
| 1   | [Cryptography Basics](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Cryptography_Basics.md) | What it is, why it matters, and key terms.     |
| 2   | Cryptography - Basic Math           | [XOR](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Crypto-Basic-Math.md#-xor-exclusive-or-operation) + [Modulo](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Crypto-Basic-Math.md#-modulo-operation) |
| 3   | Public Key           | [RSA](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Public-Key-RSA.md) + [Diffie-Hellman Key Exchange](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Diffie-Hellman-Key.md) + [SSH](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/SSH.md)  + [Digital Signatures & Certificates](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Digital-signatures-certificates.md) + [PGP & GPG](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/PGP-GPG.md)|
| 4   | [Hashing Basics](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Hashing.md)         | What are hashes, and why they're unbreakable-ish. |
| 5   | [John the Ripper]()        | Learn how passwords get cracked (ethically!). |

--- 
# 50 Common Cryptography Terms in Cybersecurity

| Term                        | Explanation                                                                 |
|-----------------------------|-----------------------------------------------------------------------------|
| **Encryption**              | Converts readable data into unreadable format to protect it.               |
| **Decryption**              | Converts encrypted data back to its original readable form.                |
| **Cipher**                  | An algorithm used for encryption and decryption.                           |
| **Plaintext**               | The original readable message or data.                                     |
| **Ciphertext**              | The encrypted output that appears scrambled or unreadable.                 |
| **Symmetric Encryption**    | Uses the same key for both encryption and decryption.                      |
| **Asymmetric Encryption**   | Uses a pair of keys—public for encryption and private for decryption.      |
| **Public Key**              | Key shared publicly for encryption or signature verification.              |
| **Private Key**             | Secret key used to decrypt data or create digital signatures.              |
| **Hash Function**           | Maps data to a fixed-size value to ensure data integrity.                  |
| **Digital Signature**       | A cryptographic method of proving authenticity and integrity.              |
| **Certificate Authority (CA)** | Trusted entity that issues and verifies digital certificates.           |
| **Digital Certificate**     | Verifies the ownership of a public key issued by a CA.                     |
| **TLS (Transport Layer Security)** | Protocol that encrypts communications over networks like HTTPS.         |
| **SSL (Secure Sockets Layer)** | Predecessor of TLS for encrypting web traffic.                        |
| **PGP (Pretty Good Privacy)** | Software for email encryption and signing using hybrid cryptography.    |
| **GPG (GNU Privacy Guard)** | Open-source version of the PGP encryption system.                          |
| **Nonce**                   | A number used once to prevent replay attacks.                              |
| **Salting**                 | Adds random data to inputs like passwords before hashing.                  |
| **Key Exchange**            | Method to securely share cryptographic keys over an insecure channel.      |
| **Man-in-the-Middle Attack**| An attack where communication is intercepted and potentially altered.      |
| **Zero-Knowledge Proof**    | A way to prove knowledge of a secret without revealing it.                 |
| **Elliptic Curve Cryptography (ECC)** | Uses elliptic curves for strong encryption with smaller keys.          |
| **RSA (Rivest–Shamir–Adleman)** | A popular public key cryptosystem used in many protocols.            |
| **AES (Advanced Encryption Standard)** | A symmetric block cipher used worldwide for secure encryption.     |
| **DES (Data Encryption Standard)** | An older symmetric-key method now considered insecure.             |
| **Brute Force Attack**      | Trying all possible key combinations until the correct one is found.       |
| **Rainbow Table**           | A precomputed table used to reverse cryptographic hash functions.          |
| **Key Pair**                | The combination of a public and private key used in asymmetric encryption. |
| **Checksum**                | A simple hash used to verify the integrity of data.                        |
| **HMAC (Hash-Based Message Authentication Code)** | Ensures message integrity and authenticity using a shared key. |
| **Block Cipher**            | Encrypts data in fixed-size blocks (e.g., AES).                            |
| **Stream Cipher**           | Encrypts data one bit or byte at a time.                                  |
| **Key Management**          | Handling cryptographic keys securely throughout their lifecycle.           |
| **X.509 Certificate**       | A standard format for public key certificates.                             |
| **Diffie-Hellman**          | A method for two parties to securely share a secret over public channels.  |
| **Integrity**               | Ensures that data has not been altered during transmission.                |
| **Authentication**          | Confirms the identity of a user or device.                                |
| **Authorization**           | Grants permission to access specific resources.                           |
| **Replay Attack**           | Resending captured data to trick systems into granting access.             |
| **Key Rotation**            | Regularly changing cryptographic keys to reduce risk.                      |
| **Forward Secrecy**         | Ensures that session keys are not compromised even if private keys are.    |
| **Initialization Vector (IV)** | A random value used with a key to ensure uniqueness of encryption.       |
| **Padding**                 | Adds extra data to meet required block sizes in encryption.                |
| **Obfuscation**             | Making data difficult to understand, though not encrypted.                 |
| **Base64 Encoding**         | Converts binary data to ASCII text format, often for transmission.         |
| **Cryptanalysis**           | The study of analyzing and breaking cryptographic systems.                 |
| **Entropy**                 | Measure of randomness used in cryptographic keys.                          |
| **Steganography**           | Hiding information within other non-secret data (like images).             |
| **Side-Channel Attack**     | Exploiting physical data leaks (like timing or power usage) to break crypto.|
| **Root of Trust**           | A set of functions in a secure computing base that is trusted.  
