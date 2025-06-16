# ♟️ Cryptography Basics

Page index
- [📌 Importance of Cryptography](#-importance-of-cryptography)
- [🧩 Key Terms](#-key-terms)
- [🕰️ Historical Ciphers](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Cryptography_Basics.md#%EF%B8%8F-historical-ciphers)
- [🔐 Symmetric vs Asymmetric Encryption](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Cryptography_Basics.md#%EF%B8%8Fsymmetric-vs-asymmetric-encryption)

## 📌 Importance of Cryptography
Cryptography is essential for ensuring secure communication in environments where adversaries may attempt to intercept or manipulate data. At its core, cryptography safeguards the confidentiality, integrity, and authenticity (CIA triad) of information by preventing unauthorized access or tampering.

### 🔐 Everyday Applications
Cryptography is seamlessly embedded into daily digital activities:
- Login Credentials: Encrypted during transmission (e.g., logging into TryHackMe).
- Secure Sessions: SSH connections create encrypted tunnels to prevent eavesdropping.
- Online Banking: SSL/TLS certificates authenticate banking servers and protect data.
- File Verification: Hash functions confirm the integrity of downloaded files.

Even though users may not interact with cryptographic algorithms directly, these technologies are deeply integrated into systems to ensure trust and security.

### 🧾 Regulatory Compliance
Certain industries mandate cryptographic standards to ensure sensitive data is protected:
- Finance: [PCI DSS](https://listings.pcisecuritystandards.org/documents/PCI_DSS_for_Large_Organizations_v1.pdf) requires encryption of credit card data at rest and in transit.
- Healthcare: Data protection laws like [HIPAA](https://www.ncbi.nlm.nih.gov/books/NBK500019/) (US), [GDPR](https://gdpr-info.eu/) (EU), and [DPA](https://www.gov.uk/data-protection) (UK) mandate encryption of personal health information (PHI) to maintain privacy and security.

These frameworks highlight that cryptography is not optional—it's a regulatory and ethical necessity in data-sensitive environments.

---

## 🧩 Key Terms

| **Term**      | **Definition**                                                                 |
|---------------|---------------------------------------------------------------------------------|
| **Plaintext** | The original readable message/data before encryption.                          |
| **Ciphertext**| The encrypted, unreadable version of the plaintext.                            |
| **Cipher**    | The algorithm used to encrypt and decrypt data.                                |
| **Key**       | A secret value used by the cipher to transform data.                           |
| **Encryption**| The process of converting plaintext into ciphertext using a cipher and key.    |
| **Decryption**| The process of converting ciphertext back into plaintext using the cipher and key. |

---

## 🕰️ Historical Ciphers

Before the digital age, cryptography was already being used to protect secrets—especially in times of war and diplomacy. These **classical ciphers** laid the foundation for modern cryptographic methods. Let’s explore a few of the most influential historical ciphers.

---

### 🔠 Caesar Cipher

One of the earliest known encryption techniques, the **Caesar Cipher** is a substitution cipher used by Julius Caesar to send confidential military messages.

- **How it works**: Each letter in the plaintext is shifted a fixed number of positions down the alphabet. For example, with a shift of 3, `A` becomes `D`, `B` becomes `E`, and so on.
- **Example**:
  - **Plaintext**: `HELLO`
  - **Key**: `3`
  - **Ciphertext (Shift 3)**: `KHOOR`
- **Weakness**: It’s easy to break using brute force (only 25 possible shifts).
- **Try it yourself**:  
  🔗 [https://cryptii.com/pipes/caesar-cipher](https://cryptii.com/pipes/caesar-cipher)


### 🔤 Vigenère Cipher

The **Vigenère Cipher** improves upon the Caesar Cipher by using a **keyword** to determine the shift for each letter.

- **How it works**: Each letter of the plaintext is shifted according to the corresponding letter in a repeating keyword. The shift value is based on the letter's position in the alphabet.
- **Example**:
  - **Plaintext**: `ATTACKATDAWN`
  - **Keyword**: `LEMON`
  - **Ciphertext**: `LXFOPVEFRNHR`
- **Strength**: More resistant to frequency analysis than Caesar Cipher.
- **Weakness**: Still vulnerable to cryptanalysis techniques like the Kasiski examination once the key length is known.
- **Try it yourself**:  
  🔗 [https://www.dcode.fr/vigenere-cipher](https://www.dcode.fr/vigenere-cipher)


### ⚙️ Enigma Machine

Used by Nazi Germany during WWII, the **Enigma Machine** was a complex electromechanical cipher device used to encrypt military communications.

- **How it works**:
  - Substitution cipher implemented with **rotating mechanical rotors**, **plugboards**, and **reflectors**.
  - Each key press scrambled the letter based on rotor settings that changed with every key press, making the cipher dynamic and hard to predict.
- **Breaking Enigma**:
  - Cracked by Polish mathematicians and later by British cryptanalysts at **Bletchley Park**, most notably **Alan Turing**.
- **Try it yourself**:  
  🔗 [https://cryptii.com/pipes/enigma-machine](https://cryptii.com/pipes/enigma-machine)  
  🔗 [https://www.101computing.net/enigma-machine-emulator/](https://www.101computing.net/enigma-machine-emulator/)

---

## ‼️Symmetric vs Asymmetric Encryption

Cryptography relies on two major types of encryption methods: **symmetric** and **asymmetric** encryption. Understanding their differences is essential to grasp how secure communication is established in modern systems.

---

### 🔏 Symmetric Encryption

Symmetric encryption (also known as **private key encryption**) uses the **same key** for both encryption and decryption.

- **How it works**: 
  - The sender encrypts the data using a secret key.
  - The recipient uses the **same secret key** to decrypt the data.
- **Challenge**: 
  - Securely sharing the key is difficult—especially if multiple recipients or untrusted networks are involved.
- **Real-life example**: 
  - Sending an encrypted document via email but needing to share the password in person or over a separate, secure channel.

#### 🔍 Examples of Symmetric Ciphers:
| Algorithm | Key Size | Notes |
|-----------|----------|-------|
| **DES**   | 56-bit   | Insecure today; cracked in under 24 hours in 1999. |
| **3DES**  | 168-bit (effective ~112-bit) | Triple encryption of DES; now deprecated. |
| **AES**   | 128, 192, or 256-bit | Modern standard; secure and widely used. |

> 💡 Symmetric encryption is **fast and efficient**, making it ideal for encrypting large amounts of data—but not ideal for key exchange.

---

### 🔐 Asymmetric Encryption

Asymmetric encryption (or **public key cryptography**) uses a **pair of keys**: one for encryption and another for decryption.

- **How it works**:
  - The sender uses the **recipient’s public key** to encrypt the data.
  - Only the **recipient’s private key** can decrypt it.
- **Benefit**: 
  - No need to share a secret key beforehand.
  - Supports secure key exchange and digital signatures.

#### 🔍 Examples of Asymmetric Algorithms:
| Algorithm         | Key Size (Recommended) | Notes |
|------------------|------------------------|-------|
| **RSA**           | 2048–4096 bits         | Commonly used for secure communication. |
| **Diffie-Hellman**| 2048–4096 bits         | Used for secure key exchange. |
| **Elliptic Curve (ECC)** | 256-bit ECC ≈ 3072-bit RSA | Efficient and strong security with shorter keys. |

> 🔐 Your **public key** is shared openly, while your **private key** must be kept secret.

---

### 🧠 Key Differences Summary

| Feature            | Symmetric Encryption             | Asymmetric Encryption               |
|--------------------|----------------------------------|-------------------------------------|
| 🔑 Keys Used        | One shared secret key            | Public and private key pair         |
| 🔄 Speed            | Fast                             | Slower                              |
| 📦 Data Encryption  | Ideal for large data volumes     | Often used for small data or key exchange |
| 🔐 Key Sharing      | Difficult and risky              | Easier and secure                   |
| 📚 Examples         | AES, DES, 3DES                   | RSA, ECC, Diffie-Hellman            |

---

> 📝 **In practice**: Many secure systems (like HTTPS) use **both** types of encryption—**asymmetric encryption** to exchange a shared key, then **symmetric encryption** for fast, efficient data transfer.

---

<sub>🔗 References & Resources:
TryHackMe — Cryptography Basics | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/cryptographybasics)</sub>
