# 🧩 Cracking Hashes from `/etc/shadow`

## 📁 What is `/etc/shadow`?

Linux systems store user password hashes in the `/etc/shadow` file. This file also holds:
- Last password change date
- Password expiration data
- One entry per user account

> 🔐 **Access Note:**  
Only the **root** user typically has permission to read `/etc/shadow`.

---

## 🔄 Unshadowing the Files

John the Ripper requires `/etc/passwd` and `/etc/shadow` to be **merged** into a readable format using the `unshadow` tool.

### 🛠️ Unshadow Syntax
```bash
unshadow [path to passwd] [path to shadow] > unshadowed.txt
```

| Command Component | Description |
|------------------|-------------|
| `unshadow`       | John tool to merge password and shadow files |
| `passwd`         | `/etc/passwd` or a copied line from it |
| `shadow`         | `/etc/shadow` or a copied line from it |
| `> unshadowed.txt` | Output redirected to a file |

### 📄 Example Files

**local_passwd**
```
root:x:0:0::/root:/bin/bash
```

**local_shadow**
```
root:$6$2nwjN454g.dv4HN/$m9Z/r2xVfweYVkrr.v5Ft8Ws3/YYksfNwq96UL1FX0OJjY1L6l.DS3KEVsZ9rOVLB/ldTeEL/OIhJZ4GMFMGA0:18576::::::
```

---

## 🔓 Cracking the Hashes

Once the merged file (`unshadowed.txt`) is ready, you can crack the hashes using:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt unshadowed.txt
```

- `--wordlist`: Path to your password list (e.g., `rockyou.txt`)
- `--format=sha512crypt`: (Optional) Specify if auto-detection fails

> ⚠️ Note: You may not always need to specify `--format` if John detects it correctly.

---


## Single Crack Mode

John the Ripper also supports **Single Crack Mode**, an alternative to wordlist mode. This mode uses the **username** and other available data to generate likely password guesses through a technique called **word mangling**.

### Word Mangling

Given a username like `Markus`, John may try variations such as:

- Markus1, Markus2, Markus3
- MArkus, MARkus, MARKus
- Markus!, Markus$, Markus*

This process is known as **word mangling**, and John applies a set of mutation rules to transform the initial word into plausible passwords.

### GECOS Field

John can also extract information from the **GECOS field** in UNIX-like systems, which includes the user's full name, office number, and other personal details. This is helpful for creating more targeted password guesses.

### Syntax

```bash
john --single --format=[format] [path to file]
```

- `--single`: Use single crack mode
- `--format=[format]`: Set the hash format

**Example**:

```bash
john --single --format=raw-sha256 hashes.txt
```

### Input Format for Single Crack Mode

You must prepend the username to the hash in the input file, using a colon separator.

**Example:**

Before:
```
1efee03cdcb96d90ad48ccc7b8666033
```

After:
```
mike:1efee03cdcb96d90ad48ccc7b8666033
```


---

- <sup>Refer to https://www.youtube.com/watch?v=MZuzwBDNPQw&ab_channel=DjalilAyed</sup>
- <sup>Refer to https://greenorangge1.medium.com/john-the-ripper-f157699593d5</sup>
