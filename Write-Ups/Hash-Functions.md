# What is a Hash Function?

A **hash function** is a cryptographic function that takes an input of arbitrary size and produces a **fixed-size output**, known as a **hash value** or **digest**. Unlike encryption, there is **no key** involved, and it is designed to be **irreversible**—meaning you cannot reconstruct the original input from the output.

## Key Properties of Hash Functions

- **Deterministic**: Same input always gives the same output.
- **Fixed Output Size**: Regardless of input size, the output hash length is constant.
- **Pre-image Resistance**: It's computationally hard to derive the input from the hash.
- **Avalanche Effect**: A small change in input (even 1 bit) causes a drastically different hash.
- **Collision Resistance**: It’s unlikely two different inputs will produce the same hash.

---

## Practical Example

Consider two text files:

- `file1.txt` contains the character `T` (hex: `54`, binary: `01010100`)
- `file2.txt` contains the character `U` (hex: `55`, binary: `01010101`)

They differ by only **1 bit**, yet their hash values (using MD5, SHA1, and SHA-256) are **completely different**:

```bash
# MD5
file1.txt: b9ece18c950afbfa6b0fdbfa4ff731d3  
file2.txt: 4c614360da93c0a041b22e537de151eb

# SHA1
file1.txt: c2c53d66948214258a26ca9ca845d7ac0c17f8e7  
file2.txt: b2c7c0caa10a0cca5ea7d69e54018ae0c0389dd6

# SHA256
file1.txt: e632b7095b0bf32c260fa4c539e9fd7b852d0de454e9be26f24d0d6f91d069d3  
file2.txt: a25513c7e0f6eaa80a3337ee18081b9e2ed09e00af8531c8f7bb2542764027e7
```

