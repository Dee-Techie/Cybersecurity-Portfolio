# 🔐 Hashing for Integrity Checking

## ✅ Purpose of Hashing in Integrity

Hash functions are used not only for password storage but also for **verifying file integrity**. This ensures that:

- A file hasn’t been altered or corrupted.
- The file downloaded is identical to the original source.

### 🔁 How It Works

- Hash functions are **deterministic**: the same input always produces the same output.
- A **tiny change** in the input will cause a **drastically different** hash.
- By comparing a known hash (e.g., from the developer) with a computed hash (from your download), you can verify the file’s integrity.

### 🧪 Example: Fedora ISO File Verification

```bash
# Sample SHA256 checksums for Fedora ISOs:
SHA256 (Fedora-Workstation-Live-osb-40-1.14.x86_64.iso) = 8d3cb4d99f27eb932064915bc9ad34a7529d5d073a390896152a8a899518573f
SHA256 (Fedora-Workstation-Live-x86_64-40-1.14.iso) = dd1faca950d1a8c3d169adf2df4c3644ebb62f8aac04c401f2393e521395d613
```

- Run `sha256sum` on your downloaded file.
- If it matches the official hash: ✅ File is verified and unaltered.

![image](https://github.com/user-attachments/assets/77b70264-218a-4b9d-81ef-7dca2e713366)

---

## 🧮 Hashing for Duplicate File Detection

- Identical files produce the same hash.
- Use this technique to find and remove **duplicate documents**.

---

## 🔐 HMAC: Keyed-Hash Message Authentication Code

### 📌 What is HMAC?

HMAC combines a **hash function** and a **secret key** to verify:

- **Integrity**: The data hasn’t been tampered with.
- **Authenticity**: The sender is legitimate.

### 🔄 How HMAC Works (Simplified Steps)

1. Pad the secret key to match the block size of the hash function.
2. XOR the padded key with an inner constant (ipad).
3. Concatenate the result with the message and hash it.
4. XOR the key with an outer constant (opad).
5. Concatenate this with the result from step 3 and hash again.

### 📐 HMAC Formula

```
HMAC(K, M) = H((K ⊕ opad) || H((K ⊕ ipad) || M))
```

Where:
- `K` = secret key
- `M` = message
- `H` = hash function
- `⊕` = XOR
- `||` = concatenation

---

Use HMACs when both **data integrity** and **authentication** are required — such as in secure APIs, communications, or file transfer systems.

---

- ❓What is SHA256 hash of libgcrypt-1.11.0.tar.bz2 found in ~/Hashing-Basics/Task-7?
  - 09120c9867ce7f2081d6aaa1775386b98c2f2f246135761aae47d81f58685b9c
    - sha256sum ~/Hashing-Basics/Task-7/libgcrypt-1.11.0.tar.bz2

- ❓What’s the hashcat mode number for HMAC-SHA512 (key = $pass)?
  - 1750
    - Use[Hashcat Wiki](https://hashcat.net/wiki/doku.php?id=example_hashes)
        ![image](https://github.com/user-attachments/assets/664d0562-cbaf-45bc-97ef-3984f64cb6ce)

---

<sub>🔗 References & Resources: TryHackMe — Hashing Basics | Cyber Security 101 (THM) TryHackMe</sub>
