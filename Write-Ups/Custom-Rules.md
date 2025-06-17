# 🛃 Custom Rules in John the Ripper

## What are Custom Rules?

Custom rules in John the Ripper allow you to define personalized mangling patterns for generating password guesses dynamically. These rules are especially useful when you have knowledge about the typical password structures used by your target (e.g., password complexity policies).

---

## Why Use Custom Rules?

Organizations often enforce password complexity requirements like:

- At least one lowercase letter
- At least one uppercase letter
- At least one number
- At least one symbol

Users often comply with predictable patterns, such as:

```
Polopassword1!
```

These can be exploited using custom rules that dynamically append or prepend characters.

---

## Where to Define Custom Rules

Custom rules are written in the `john.conf` file:

- On TryHackMe AttackBox: `/opt/john/john.conf`
- Typical system install: `/etc/john/john.conf`

---

## Syntax Overview

A custom rule is defined like so:

```ini
[List.Rules:RuleName]
<rule modifiers>
```

### Common Modifiers

| Modifier | Function                                      |
|----------|-----------------------------------------------|
| `Az`     | Appends characters to the end of the word     |
| `A0`     | Prepends characters to the beginning of word  |
| `c`      | Capitalizes the first letter                  |

### Character Sets

| Pattern        | Description                                |
|----------------|--------------------------------------------|
| `[0-9]`        | Digits 0 through 9                         |
| `[A-Z]`        | Uppercase letters                         |
| `[a-z]`        | Lowercase letters                         |
| `[!£$%@]`      | Common symbols                            |
| `[a]`          | Specific character `a`                    |

---

## Example Rule

To generate variations of the password `Polopassword1!` from a base word `polopassword`, define:

```ini
[List.Rules:PoloPassword]
cAz"[0-9][!£$%@]"
```

This:
- Capitalizes the first letter (`c`)
- Appends a digit (`[0-9]`)
- Appends a symbol (`[!£$%@]`)

---

## Using Custom Rules

To apply a custom rule in John:

```bash
john --wordlist=[path to wordlist] --rule=PoloPassword [path to hash file]
```

---

## Tips

- Speak out the pattern as you define it—this helps clarify your logic.
- John’s jumbo version includes many built-in rules—check around line 678 in `john.conf` if you need examples or help troubleshooting your syntax.

---

## Quick Questions :
-❓ What do custom rules allow us to exploit?
  - Password complexity predictability

-❓ What rule would we use to add all capital letters to the end of the word?
  - Az"[A-Z]"

-❓ What flag would we use to call a custom rule called THMRules?
  - --rule=THMRules

---
<sub>🔗 References & Resources:
TryHackMe — John The Ripper | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/johntheripperbasics)</sub>
