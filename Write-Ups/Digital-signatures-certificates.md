# ![WaiverSighnGIF](https://github.com/user-attachments/assets/30fae190-6160-4246-9905-2c62c3b4b1f4)
# Digital Signatures and Certificates

## Introduction

Just like signing a paper in the physical world helps prove identity and agreement, in the digital world we use **digital signatures**. These ensure authenticity (who created it) and integrity (hasn't been tampered with) of data or documents.

---

## What is a Digital Signature?

A **digital signature** uses asymmetric encryption (public/private keys) to validate the authenticity and integrity of a message or document.

- You sign a message using **your private key**.
- Others verify the signature using **your public key**.

Since only you have the private key, this confirms that the data came from you. This mechanism has legal validity in many jurisdictions similar to handwritten signatures.

### Example Workflow:

1. Bob hashes his message and encrypts the hash using his private key.
2. Bob sends the original message and the encrypted hash (signature) to Alice.
3. Alice:
   - Hashes the received message.
   - Decrypts the encrypted hash using Bob’s **public key**.
   - Compares the two hashes. If they match, the message is authentic and unaltered.

> ⚠️ Digital signatures are not just pasted images of a signature! Those can be copied and do not prove document integrity.

---

## What is a Certificate?

A **digital certificate** binds a public key to an identity (e.g., a domain or person). It proves **who you are** in digital communications.

Certificates are used widely, especially for securing websites via HTTPS.

---

## How Do Certificates Work?

Certificates rely on a **chain of trust** model.

- A **Certificate Authority (CA)** is a trusted entity that issues certificates.
- Your computer or browser comes preloaded with trusted root CAs.
- If a certificate for a website is signed by a CA that is trusted (or by an intermediate CA that is in the chain of trust from a trusted root), the browser trusts it.

### Example:

1. You access `https://tryhackme.com`.
2. The server presents a certificate saying "I am tryhackme.com", signed by an intermediate CA.
3. That intermediate CA is trusted by a Root CA known to your browser.
4. Result: Your browser trusts the certificate.

---

## Getting a Certificate

- **Paid Certificates**: Available from providers like DigiCert, GoDaddy, etc.
- **Free Certificates**: [Let’s Encrypt](https://letsencrypt.org) provides free TLS certificates for your domain.

Any modern website **must** use HTTPS to secure communications.

---

## SSL Certificates vs SSH Certificates

| Feature                        | SSL Certificate                          | SSH Certificate                         |
|-------------------------------|-------------------------------------------|------------------------------------------|
| Purpose                        | Secure web communications (HTTPS)         | Secure shell access to servers (SSH)     |
| Protocol                       | TLS (formerly SSL)                        | SSH                                       |
| Authentication Method         | Server authentication via CA-signed cert | User/server authentication via public keys |
| Key Use                        | Encrypt web traffic                       | Authenticate user or host during SSH     |
| Certificate Authority (CA)    | Required (Root/Intermediate CAs)          | Optional (can use internal CA or key-pairs) |
| Common Tools/Use Cases        | Web servers, browsers                     | Terminal sessions, DevOps, sysadmin tasks |
| Lifetime                      | Typically 90 days to 2 years              | Often short-lived (e.g., hours/days for security) |
| Revocation                    | CRL/OCSP                                 | Manual key removal or CA key expiry      |

---

## Conclusion

Digital signatures and certificates are core to modern cybersecurity. Digital signatures ensure data authenticity and integrity, while certificates help establish trusted identities over the internet. Understanding these tools helps build secure systems and protects against spoofing and tampering.
