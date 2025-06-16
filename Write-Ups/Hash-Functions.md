# 🧮 What is a Hash Function?

A **hash function** is a cryptographic function that takes an input of arbitrary size and produces a **fixed-size output**, known as a **hash value** or **digest**. Unlike encryption, there is **no key** involved, and it is designed to be **irreversible**—meaning you cannot reconstruct the original input from the output.

## Key Properties of Hash Functions

- **Deterministic**: Same input always gives the same output.
- **Fixed Output Size**: Regardless of input size, the output hash length is constant.
- **Pre-image Resistance**: It's computationally hard to derive the input from the hash.
- **Avalanche Effect**: A small change in input (even 1 bit) causes a drastically different hash.
- **Collision Resistance**: It’s unlikely two different inputs will produce the same hash.

---

## 🧪 Practical Example

Consider two text files:

- `file1.txt` contains the character `T` (hex: `54`, binary: `01010100`)
- `file2.txt` contains the character `U` (hex: `55`, binary: `01010101`)

They differ by only **1 bit**, yet their hash values (using MD5, SHA1, and SHA-256) are **completely different**:

```bash
# MD5 (md5sum file1.txt & md5sum file2.txt)
file1.txt: b9ece18c950afbfa6b0fdbfa4ff731d3  
file2.txt: 4c614360da93c0a041b22e537de151eb

# SHA1 (cmd : sha1sum file1.txt & sha1sum file2.txt)
file1.txt: c2c53d66948214258a26ca9ca845d7ac0c17f8e7  
file2.txt: b2c7c0caa10a0cca5ea7d69e54018ae0c0389dd6

# SHA256 (cmd : sha256sum file1.txt & sha256sum file2.txt)
file1.txt: e632b7095b0bf32c260fa4c539e9fd7b852d0de454e9be26f24d0d6f91d069d3  
file2.txt: a25513c7e0f6eaa80a3337ee18081b9e2ed09e00af8531c8f7bb2542764027e7
```

These outputs are displayed in **hexadecimal**, where each byte is represented by two hex digits.

---

## 🔑 Why is Hashing Important?

Hashing is **widely used in cybersecurity** and often happens behind the scenes. Its primary uses include:

- **Password Security**: Systems store the hash of your password, not the actual password.
- **Data Integrity**: Ensures a file hasn’t been tampered with during transmission or storage.
- **Digital Signatures**: Hashes are used in verifying authenticity and integrity.

Example: When logging into a website like TryHackMe, your password is hashed and compared to the stored hash. If they match, access is granted.

---

## 🚀 What is a Hash Collision?

A **collision** occurs when two different inputs produce the **same hash output**.

Because there are **infinite possible inputs** and only a **finite number of hash values**, **collisions are inevitable** (this is known as the **pigeonhole principle**). However, good hash functions make it **computationally infeasible** to intentionally generate a collision.

### Visual Analogy: Pigeonhole Principle
If there are 21 pigeons and 16 pigeonholes, some pigeonholes will contain more than one pigeon. Similarly, with hash functions, multiple inputs may lead to the same output.

---

## ❌ Insecure Hash Functions

### MD5 and SHA1
- Both have known vulnerabilities and are considered **insecure**.
- Attackers can engineer collisions in these algorithms.
- **Do not use MD5 or SHA1 for passwords or sensitive data.**

**Examples of known attacks**:
- [MD5 Collision Demo](https://www.mscs.dal.ca/~selinger/md5collision/)
- [SHA1 “SHAttered” Attack](https://shattered.io/)

Instead, use more secure hash functions like:
- **SHA-256**
- **SHA-3**
- **BLAKE2**

---

## 🎯 Summary

| Concept             | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| Hash Function        | One-way function producing fixed-length output from variable-length input. |
| Hash Value           | The resulting string (digest) from a hash function.                        |
| Collision            | When two different inputs produce the same hash output.                    |
| Avalanche Effect     | Small input change → drastically different hash.                           |
| Use in Security      | Password storage, data integrity, digital signatures.                      |
| Unsafe Algorithms    | MD5, SHA1 (due to known collision attacks).                                |

Hash functions are fundamental in ensuring the integrity and authenticity of digital information in cybersecurity.
