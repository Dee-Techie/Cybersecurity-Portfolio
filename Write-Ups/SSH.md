# SSH Authentication Explained (Simplified)

## 🔐 What is SSH?

**SSH (Secure Shell)** is a cryptographic protocol used to securely connect to remote machines. It encrypts the communication between the client (you) and the server (remote machine), ensuring privacy and security even over insecure networks.

---

## 🧾 Authenticating the **Server**

When you first connect to a server via SSH, your client verifies if the server is trustworthy. You'll see a message like this:

```bash
$ ssh 10.10.244.173
The authenticity of host '10.10.244.173' can't be established.
ED25519 key fingerprint is SHA256:...
Are you sure you want to continue connecting (yes/no)? yes
```

### What’s Happening?

- The **server sends its public key fingerprint** to identify itself.
- Your **SSH client checks** if it has seen this key before.
- If it’s the **first time**, the key is unknown, and you must **manually verify** its authenticity.
- Once you accept, the key is saved to your `~/.ssh/known_hosts` file. Future connections will skip this prompt **unless the key changes** (which could signal an attack).

### Why This Matters

Without checking this fingerprint, you could fall victim to a **man-in-the-middle attack**, where a malicious server pretends to be the legitimate one.

---

## 🙋 Authenticating the **Client**

Once the server is verified, it needs to verify **you**.

### 🔑 Common Methods

1. **Username and password** – Not very secure and vulnerable to brute force attacks.
2. **SSH key-based authentication** – Preferred and more secure.

---

## 🔐 SSH Key-Based Authentication

### What Are SSH Keys?

- **SSH keys** are a pair of cryptographic keys:
  - **Public key** – Shared with the server.
  - **Private key** – Kept secret on your machine.

### How It Works

1. You generate a key pair with `ssh-keygen`.
2. You **keep the private key** on your machine.
3. You **copy the public key** to the remote server's `~/.ssh/authorized_keys` file.
4. When connecting, the server uses the public key to **verify your private key**.

---

## 🛠️ Generating SSH Keys

Use the `ssh-keygen` command:

```bash
$ ssh-keygen -t ed25519
```

- `-t` specifies the type of key. Options include:
  - `rsa`
  - `dsa`
  - `ecdsa`
  - `ed25519` (modern, secure, and smaller)

You’ll be prompted to:

- Save the key to a file (default: `~/.ssh/id_ed25519`)
- Enter a **passphrase** (adds extra security)

### Example Key Output

- **Public Key** (`id_ed25519.pub`):
  ```bash
  ssh-ed25519 AAAAC3Nz... strategos@g5000
  ```

- **Private Key** (`id_ed25519`):
  ```
  -----BEGIN OPENSSH PRIVATE KEY-----
  ...
  -----END OPENSSH PRIVATE KEY-----
  ```

⚠️ **NEVER share your private key.** It grants full access to any system that trusts the matching public key.

---

## 🧠 Additional Key Types Explained (For Awareness)

| Key Type     | Description                                                                 |
|--------------|-----------------------------------------------------------------------------|
| `DSA`        | Old algorithm, less secure, rarely used now                                 |
| `ECDSA`      | Uses elliptic curves, faster, but requires care in implementation           |
| `ECDSA-SK`   | Same as ECDSA, but backed by hardware security keys (e.g., YubiKey)         |
| `ED25519`    | Fast, small, secure — recommended for most use cases                        |
| `ED25519-SK` | ED25519 with hardware security key support                                  |

---

## 🔒 Security Best Practices

- Use **strong passphrases** to encrypt your private key.
- Do **not share** private keys.
- Set proper **file permissions** on your key files:
  ```bash
  chmod 600 ~/.ssh/id_ed25519
  ```

- To specify a private key during SSH login:
  ```bash
  ssh -i ~/.ssh/id_ed25519 user@host
  ```

---

## 📂 Where Keys Are Stored

| Location                     | Purpose                                    |
|------------------------------|--------------------------------------------|
| `~/.ssh/id_ed25519`          | Your private key                           |
| `~/.ssh/id_ed25519.pub`      | Your public key                            |
| `~/.ssh/authorized_keys`     | Server-side file listing allowed public keys |
| `~/.ssh/known_hosts`         | Client-side list of known servers          |

Use `ssh-copy-id` to install your public key on a remote server:

```bash
ssh-copy-id -i ~/.ssh/id_ed25519.pub user@host
```

---

## 🛡️ Extra Tip: Using SSH Keys for “Better Shells”

During Capture The Flag (CTF), penetration testing, or red teaming:

- You can use SSH keys to **upgrade a reverse shell** to a more stable one (with tab completion, Ctrl+C support, etc.).
- If you have access to a user account, add your public key to `~/.ssh/authorized_keys`.
- SSH in using your private key and enjoy a fully interactive shell.

⚠️ Not all users (e.g., `www-data`) have SSH access by default.

---

## ⚠️ Summary of Security Considerations

| Action                        | Risk/Warning                                                       |
|-------------------------------|---------------------------------------------------------------------|
| Sharing private keys          | 🔥 Never do this!                                                   |
| Using no passphrase           | 🔐 Insecure unless temporary or isolated usage                      |
| Not verifying server fingerprint | 🎯 Vulnerable to MITM attacks                                      |
| Improper file permissions     | 🚫 SSH may refuse to use the key (must be 600 or stricter)          |

---

## ✅ TL;DR

- SSH allows **secure remote login** using encrypted channels.
- Server identity is verified via its **public key fingerprint**.
- Client identity is verified via **username/password** or (better) **SSH keys**.
- Always protect your **private key**, and **use a passphrase**.
- Use `ssh-copy-id` to install public keys on remote servers.
- SSH keys are the **preferred secure method** of remote authentication.

---
<sub>🔗 References & Resources:
TryHackMe — Cryptography Public Key | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/publickeycrypto)</sub>
