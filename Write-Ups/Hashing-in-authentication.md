# 🔐 Insecure Password Storage for Authentication

In cybersecurity, hashing plays a crucial role in authentication systems. This summary focuses on how **poor password storage practices** can lead to serious security vulnerabilities.

> ⚠️ This discussion **does not apply to password managers**, which must retrieve passwords in plaintext. Authentication systems only need to **verify knowledge of a password**, not reveal it.

---

## 🧱 Common Insecure Password Storage Methods

Many web applications must verify user passwords. Unfortunately, **storing them improperly** has led to significant data breaches and exposure. Here are three insecure practices:

### 1. 📝 Storing Passwords in Plaintext

- Storing passwords directly without any protection is highly insecure.
- A famous example is **RockYou**, a company that stored all passwords in plaintext.
- After a breach, their entire password list was leaked—now known as `rockyou.txt`, used commonly in penetration testing.

#### 📁 Example (rockyou.txt from Kali Linux):
```bash
strategos@g5000 /usr/share/wordlists> wc -l rockyou.txt 
14344392 rockyou.txt      

strategos@g5000 /usr/share/wordlists> head -n7 rockyou.txt 
123456
12345
123456789
password
iloveyou
princess
1234567
```

### 2. 🗝️ Using Deprecated Encryption

- Adobe suffered a breach where passwords were stored using deprecated encryption, not secure hashing.
- Worse, password hints were stored in plaintext and often revealed the actual passwords.
- This made cracking the passwords extremely easy for attackers.

### 3. 🔄 Using Insecure Hashing Algorithms

- LinkedIn’s 2012 breach revealed passwords stored using SHA-1, a now-broken hash function.
- No password salting was applied.

Lack of salting made it trivial for attackers to use precomputed hash tables to crack passwords.

---

## 🛡️ Why Use Hashing for Password Storage?

Instead of storing passwords directly, store their **hash values** using secure hashing algorithms.

- ✅ If the database is leaked, attackers get only hashes, not actual passwords.
- ❗ But: if two users have the same password, they'll have the same hash — making mass attacks easier via **Rainbow Tables**.

---

## 🌈 What is a Rainbow Table?

A **Rainbow Table** is a precomputed list of hashes and their corresponding plaintext passwords. It's a **fast lookup** method for cracking hashes.

| Hash                                       | Password       |
|--------------------------------------------|----------------|
| 02c75fb22c75b23dc963c7eb91a062cc           | zxcvbnm        |
| b0baee9d279d34fa1dfd71aadb908c3f           | 11111          |
| c44a471bd78cc6c2fea32b9fe028d30a           | asdfghjkl      |
| d0199f51d2728db6011945145a1b607a           | basketball     |
| dcddb75469b4b4875094e14561e573d8           | 000000         |
| e10adc3949ba59abbe56e057f20f883e           | 123456         |
| e19d5cd5af0378da05f63f891c7467af           | abcd1234       |
| e99a18c428cb38d5f260853678922e03           | abc123         |
| fcea920f7412b5da7be0cf42b8c93759           | 1234567        |
| 4c5923b6a6fac7b7355f53bfe2b8f8c1           | inS3CyourP4$$  |

🔍 Sites like [**CrackStation**](https://crackstation.net/) and [**Hashes.com**](https://hashes.com/en/decrypt/hash) use these tables to crack passwords fast.

---

## 🧂 Protecting Against Rainbow Tables

To stop rainbow table attacks, use **salting**:

- A **salt** is a random string added to a password before hashing.
- This makes identical passwords generate **unique hashes**.
- Salts should be **unique per user** and **stored with the hash**.
- Salting is handled automatically in functions like **Bcrypt**, **Scrypt**, and **Argon2**.

🔐 Salts **don’t need to be kept secret**.

---

## ✅ Example of Secure Password Storage

Here’s how to securely hash and store passwords:

1. **Choose a strong hash function**: Argon2, Scrypt, Bcrypt, or PBKDF2.
2. **Generate a unique salt** per user: e.g., `Y4UV*^(=go_!`
3. **Concatenate password + salt**:  
   `AL4RMc10kY4UV*^(=go_!`
4. **Hash the result** using the selected algorithm.
5. **Store the hash + the salt** in the database.

---

## 🔒 Why Not Just Encrypt Passwords?

- Encryption requires storing a **decryption key**.
- If the key is compromised, **all passwords can be decrypted**.
- Hashing, especially with a salt, is **one-way** and far more secure for password storage.


## ‼️Important

- Use **secure hashing functions** with unique **salts** for each password.
- Avoid encryption for password storage due to key risks.
