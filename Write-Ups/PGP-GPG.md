# 📝 PGP and GPG: Encrypting and Signing Made Simple

## What is PGP and GPG?

🦋 **PGP (Pretty Good Privacy)** is a software suite that enables secure communication through encryption and digital signatures. It’s commonly used to protect files and emails.

📖 **GPG (GnuPG)** is the open-source implementation of the OpenPGP standard. It provides similar functionality to PGP and is widely used because it’s free and open-source.

## What Can GPG Do?

- Encrypt messages or files to keep them confidential
- Sign messages or files to verify their integrity and authenticity
- Decrypt received messages using your private key
- Verify signed messages using the sender's public key

## GPG and Email Security

GPG is often used in email to ensure:
- **Confidentiality**: Only the intended recipient can read the email
- **Integrity**: The message hasn’t been tampered with
- **Authentication**: The sender of the email is who they claim to be

## Generating a GPG Key Pair

To start using GPG, you first generate a key pair: a public key and a private key.

```bash
gpg --full-gen-key
```

### Key Generation Process
You will be prompted to:
1. **Choose the type of key** (e.g., RSA, DSA, ECC)
2. **Choose the elliptic curve** if you select ECC (e.g., Curve25519)
3. **Set a key expiration date** (or set to never expire)
4. **Enter personal info** like your name and email
5. **Create a passphrase** (recommended to protect your private key)

### Example Output
```bash
pub   ed25519 2024-08-29 [SC]
      AB7E6AA87B6A8E0D159CA7FFE5E63DBD5F83D5ED
uid                      Strategos <strategos@tryhackme.thm>
sub   cv25519 2024-08-29 [E]
```

- **SC** = Signing & Certification
- **E** = Encryption

## Securing Your Private Key

Your private key should be stored securely and **never shared**. If the private key is compromised, attackers can impersonate you.

Like SSH keys, you can protect your GPG private key with a passphrase. If the key is not protected, anyone who gains access can decrypt your messages.

> 🔐 Always back up your private key to a secure location (e.g., encrypted USB drive or password manager).

## Using GPG in Real Life

### Share Your Public Key
Your contacts need your public key to encrypt messages to you. You can export and share it using:

```bash
gpg --armor --export your_email@example.com > public_key.asc
```

### Decrypting a Message

When you receive a `.gpg` encrypted file:

```bash
gpg --decrypt confidential_message.gpg
```

You will be prompted for your passphrase if one is set.

### Importing Keys on a New System

If you move to a new computer, you can import your backed-up key using:

```bash
gpg --import backup.key
```

## Cracking GPG Keys (CTF Context)

In Capture The Flag (CTF) competitions, you may encounter GPG keys without passphrases. If a passphrase is set, tools like **gpg2john** (from John the Ripper suite) can be used to crack it.

## Summary Table

| Feature               | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| Public Key            | Shared with others to allow encrypted communication                         |
| Private Key           | Kept secret, used for decryption and signing                                |
| Passphrase            | Protects the private key from unauthorized access                           |
| Signing               | Confirms the identity of the sender and the integrity of the message        |
| Encryption            | Ensures that only the intended recipient can read the content               |
| Backup                | Should be stored securely and separately from the working environment       |
| Usage in Email        | Protects messages from being intercepted or tampered with                   |

## Final Notes

GPG and PGP are essential tools in the world of digital security. Whether you're a privacy enthusiast, system administrator, or penetration tester, knowing how to generate, use, and manage GPG keys is a critical skill.

📚 Explore the GPG man page: `man gpg` or visit [https://gnupg.org](https://gnupg.org) for more.
