# 🔑 Diffie-Hellman Key Exchange: Sharing Secrets Securely

One of the core challenges of **symmetric encryption** is how to securely share the key. If Alice wants to send Bob an encrypted file, how can she safely share the password without risking it being intercepted?

This is where the **Diffie-Hellman Key Exchange (DHKE)** comes into play. It allows two parties to **establish a shared secret key over an insecure channel**—without having exchanged any secrets beforehand and without anyone eavesdropping being able to deduce the key.

---

## 🔁 How Diffie-Hellman Works (Simple Version)

Imagine Alice and Bob want to generate a shared key. Here's the basic idea:

1. **Public agreement** on two numbers:
   - A large prime number `p`
   - A base `g` (called the generator), such that `1 < g < p`

2. **Private secrets**:
   - Alice picks a secret number `a`
   - Bob picks a secret number `b`

3. **Exchange public keys**:
   - Alice computes `A = g^a mod p` and sends `A` to Bob
   - Bob computes `B = g^b mod p` and sends `B` to Alice

4. **Compute shared secret**:
   - Alice computes `s = B^a mod p`
   - Bob computes `s = A^b mod p`

Because of the properties of modular arithmetic, **both values of `s` are the same**: `s = g^(ab) mod p`.

This `s` becomes the shared secret key, which they can now use for symmetric encryption.

### Variables:
- `p`: A large **prime number** (public)
- `g`: A **generator** or base (public), where `1 < g < p`
- `a`: Alice’s private key (secret)
- `b`: Bob’s private key (secret)
- 
---

## 🔢 Numerical Example

To make it concrete:

- Public values: `p = 29`, `g = 3`
- Alice’s private key: `a = 13`
- Bob’s private key: `b = 15`

1. Alice computes `A = 3^13 mod 29 = 19`
2. Bob computes `B = 3^15 mod 29 = 26`

They exchange their public keys:

- Alice receives `B = 26`  
- Bob receives `A = 19`

Then they compute the shared secret:

- Alice: `s = 26^13 mod 29 = 10`
- Bob: `s = 19^15 mod 29 = 10`

✅ Both get the same shared secret: `10`

*Note: These values are tiny and insecure. Real implementations use primes of 2048+ bits for safety.*

---

## 🔐 Why It’s Secure

The security of DHKE depends on the difficulty of the **Discrete Logarithm Problem**—given `g^a mod p`, it's extremely hard to determine `a`, especially with very large `p`.

An eavesdropper who intercepts `g`, `p`, `A`, and `B` cannot compute the shared secret `s = g^(ab) mod p` without knowing either `a` or `b`.

---

## 🚫 Limitations

| Limitation | Description |
|------------|-------------|
| ❌ **No Authentication** | Alone, DHKE doesn’t verify identities. Vulnerable to **Man-in-the-Middle (MitM)** attacks unless combined with RSA/digital signatures. |
| ⚠️ **Performance Overhead** | Involves heavy computation, especially with large keys. |

---

## 🧠 Real-World Use

Diffie-Hellman is often combined with RSA in practice:

- **DHKE**: Establishes a secure session key
- **RSA**: Provides authentication and digital signatures

Together, they prevent attacks like **Man-in-the-Middle (MitM)** by verifying identities and encrypting session data.

### 📦 Protocols That Use DHKE
- TLS/SSL (web security)
- SSH (secure remote login)
- IPsec (VPNs)

---

## 📌 TL;DR

> **Diffie-Hellman lets two people create a shared secret over an insecure line—without ever sending the secret itself.** It's simple in concept, powerful in practice, and essential for secure communication on the internet.

---

## 📚 Related Concepts
- **RSA**: Often used alongside DHKE for authentication and key transport
- **Elliptic Curve Diffie-Hellman (ECDH)**: A more efficient variation using elliptic curves

---
<sub>🔗 References & Resources:
TryHackMe — Cryptography Public Key | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/publickeycrypto)</sub>
