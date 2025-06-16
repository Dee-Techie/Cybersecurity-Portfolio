# 🧮 Basic Math in Cryptography

Modern cryptography is built on fundamental mathematical concepts. Two of the most important operations used across various cryptographic algorithms are the **XOR operation** and the **Modulo operation**.

---

### 🔄 XOR (Exclusive OR) Operation

The **XOR (⊕)** operation compares two binary bits:

- Returns `1` if the bits are different
- Returns `0` if the bits are the same

#### 🔢 XOR Truth Table

| A | B | A ⊕ B |
|---|---|--------|
| 0 | 0 |   0    |
| 0 | 1 |   1    |
| 1 | 0 |   1    |
| 1 | 1 |   0    |

#### 🧠 Key Properties of XOR:

- `A ⊕ A = 0` (XOR with itself is 0)
- `A ⊕ 0 = A` (XOR with 0 returns the original value)
- **Commutative**: `A ⊕ B = B ⊕ A`
- **Associative**: `(A ⊕ B) ⊕ C = A ⊕ (B ⊕ C)`

#### 🔐 XOR in Cryptography

XOR is a simple form of symmetric encryption:

- **Encryption**: `C = P ⊕ K` (Plaintext XOR Key = Ciphertext)
- **Decryption**: `P = C ⊕ K` (Ciphertext XOR Key = Plaintext)

This works because: C ⊕ K = (P ⊕ K) ⊕ K = P ⊕ (K ⊕ K) = P ⊕ 0 = P

> ⚠️ In practice, XOR encryption requires a key as long as the plaintext and is used in combination with more secure systems.

---

### ➗ Modulo Operation

The **modulo operation**, often written as `%` or `mod`, gives the **remainder** after division.

#### 🧮 Examples:

- `25 % 5 = 0` → 25 ÷ 5 = 5 with remainder 0
- `23 % 6 = 5` → 23 ÷ 6 = 3 with remainder 5
- `23 % 7 = 2` → 23 ÷ 7 = 3 with remainder 2

> The result of `a % n` is always in the range `0` to `n - 1`.

#### 🧠 Important Notes:

- Modulo is **not reversible**: Knowing `x % 5 = 4` means there are infinite values of `x` that satisfy the equation (e.g., 4, 9, 14...).
- Modulo arithmetic is used in many cryptographic algorithms like **RSA**, **Diffie-Hellman**, and **Elliptic Curve Cryptography (ECC)**.
- Modulo helps keep numbers within fixed bounds, even when working with very large values.

> 💡 **Tip**: For cryptography challenges with large numbers, use tools like [Python](https://python.org), [WolframAlpha](https://www.wolframalpha.com), or big integer libraries.

---

These two operations form the mathematical backbone of many cryptographic processes. Mastering them provides a strong foundation for understanding encryption and secure communication.

---

### 🙋‍♀️ Quick Questions:
- ❓ What’s 1001 ⊕ 1010?
  - 0011
- ❓ What’s 118613842%9091?
  - 3565
- ❓ What’s 60%12?
  - 0

---

<sub>🔗 References & Resources:
TryHackMe — Cryptography Basics | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/cryptographybasics)</sub>
