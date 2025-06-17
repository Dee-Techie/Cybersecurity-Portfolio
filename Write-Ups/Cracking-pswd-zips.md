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

### Cracking

Use John to crack the password:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt
```
---

## 🧭 Step-by-Step Guide (extracting pswd for zip file):
- 📁 1. Navigate to the directory
  ```bash
  cd ~/John-the-Ripper-The-Basics/Task09/
  ```

- 🧱 2. Extract the hash from the ZIP file using zip2john
  ```bash
  zip2john secure.zip > zip_hash.txt
  ```
  - This command:
    - Converts secure.zip into a hash format John understands.
    - Stores it in zip_hash.txt.

- 🔍 3. Check the contents of the hash file (optional)
  ```bash
  cat zip_hash.txt
  ```
  
- 🔨 4. Run John with the rockyou wordlist
  ```bash
  john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt
  ```
  
   🧔‍♂️ John will now try cracking the hash using the rockyou.txt wordlist.

- ⏳ 5. Wait until cracking is complete
  John will test each password from the wordlist. If successful, it will stop and show the result.

- 🔑 6. Display the cracked password
  ```bash
  john --show zip_hash.txt
  ```
  This will output something like:
  ```bash
  secure.zip:supersecret123
  ```
  
- 🎉 Now you know the password for the secure.zip file!

- 💡 Tips
  If rockyou.txt isn't found, extract it:
  ```bash
  sudo gzip -d /usr/share/wordlists/rockyou.txt.gz
  ```
You can use other custom wordlists by replacing the --wordlist value.

![image](https://github.com/user-attachments/assets/4cffb8a2-a8ec-40e6-8968-09617f7d2ee6)

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

### 🧙‍♂️Example Steps :

```bash
/opt/john/rar2john secure_1605054844670.rar > rar_hashtest.txt
cat rar_hashtest.txt
john --wordlist=/usr/share/wordlists/rockyou.txt rar_hashtest.txt
john --show rar_hashtest.txt
```
Reveals the password

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
