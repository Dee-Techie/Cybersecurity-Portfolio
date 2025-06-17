# Cracking Password-Protected Archives and SSH Keys with John the Ripper

## Cracking Zip File Passwords

Yes! You read that right. We can use John to crack the password on password-protected Zip files. We'll use a tool from the John suite to convert the Zip file into a format that John understands.

### Zip2John

Use the `zip2john` tool to convert a Zip file into a hash format for John.

**Syntax:**

```bash
zip2john [options] [zip file] > [output file]
```

- `[options]`: Specific checksum options (rarely needed)
- `[zip file]`: Path to the Zip file
- `>`: Redirects output
- `[output file]`: File to store the output

**Example Usage:**

```bash
zip2john zipfile.zip > zip_hash.txt
```

### Cracking

Use John to crack the password:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt
```

---

## Cracking RAR File Passwords

RAR archives are compressed files like Zip. Use a similar process as Zip cracking.

### Rar2John

Use `rar2john` to convert the RAR file into a hash format.

**Syntax:**

```bash
rar2john [rar file] > [output file]
```

**Example Usage:**

```bash
/opt/john/rar2john rarfile.rar > rar_hash.txt
```

### Cracking

Feed the output into John:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt rar_hash.txt
```

---

## Cracking SSH Key Passwords

John can also crack SSH private key passwords (`id_rsa` files). These keys are used for key-based SSH authentication.

### SSH2John

Use `ssh2john` (or the Python script) to convert `id_rsa` into a crackable format.

**Syntax:**

```bash
ssh2john [id_rsa private key file] > [output file]
```

Or, if using the Python script:

```bash
python3 /opt/john/ssh2john.py id_rsa > id_rsa_hash.txt
```

**Example Usage:**

```bash
/opt/john/ssh2john.py id_rsa > id_rsa_hash.txt
```

Now you can crack the SSH key password using:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa_hash.txt
