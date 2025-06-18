# Metasploit Common Commands
## Launching Metasploit
Once launched, the Metasploit prompt changes to `msf6>` (or `msf5>` depending on version). You can use standard Linux commands like `ls`, `ping`, and `clear`, though features like output redirection (e.g., `help > help.txt`) are not supported.

```bash
msf6 > ls
msf6 > ping -c 1 8.8.8.8
msf6 > clear
```

## Help and History
- `help`: View available commands or get help on a specific command.
- `history`: Lists previously entered commands.
- Tab completion is supported for commands and module names.

## Modules and Context
Metasploit operates in contexts. When you use a module (e.g., an exploit), your prompt changes to reflect that context:

```bash
msf6 > use exploit/windows/smb/ms17_010_eternalblue
msf6 exploit(...) >
```

All module settings (like `RHOSTS`, `LPORT`) are contextual unless set globally using `-g`.

To view required settings:
```bash
msf6 exploit(...) > show options
```

To return to the global context:
```bash
msf6 exploit(...) > back
```

## Showing and Using Modules
- `show payloads`, `show exploits`, etc., lists modules within the current context.
- `use <index>` or `use <full_module_path>` to load a module from search results.
- `info <module>` or `info` within context provides detailed info on the selected module.

## Searching for Modules
Use `search` to find modules by:
- Name (e.g., `search eternalblue`)
- CVE ID (e.g., `search CVE-2017-0144`)
- Type/platform (e.g., `search type:auxiliary telnet`)

Example:
```bash
msf6 > search ms17-010
```

## EternalBlue Example
Using the `exploit/windows/smb/ms17_010_eternalblue` module:
```bash
msf6 > use exploit/windows/smb/ms17_010_eternalblue
msf6 exploit(...) > show options
msf6 exploit(...) > info
```

This exploit, leaked by Shadow Brokers, targets SMBv1 vulnerabilities and was used in the WannaCry ransomware attack. The `show options` command reveals required fields like `RHOSTS`, `RPORT`, `LHOST`, and `LPORT`.

## Post-Exploitation Modules
Modules like `post/windows/gather/enum_domain_users` require a valid session:
```bash
msf6 > use post/windows/gather/enum_domain_users
msf6 post(...) > show options
```

## Module Info Example Output
```bash
msf6 exploit(...) > info
# Displays:
# - Description
# - Authors
# - Disclosure date
# - Required/optional settings
# - References (CVEs, docs)
```

## Key Commands Summary

| Command             | Description                                      |
|---------------------|--------------------------------------------------|
| `search <term>`     | Search for modules                               |
| `use <module>`      | Load a module                                    |
| `show options`      | View configurable options for a module           |
| `set <option> <val>`| Set a module option                              |
| `setg <option> <val>`| Set global module option (applies across all modules) |
| `unset <option> <val>`| Resets a module option                         |
| `unset all`          | Resets all the settings                         |
| `run` or `exploit`  | Execute the loaded module                        |
| `back`              | Exit module context                              |
| `info`              | View detailed module info                        |
| `history`           | View command history                             |
| `help`              | Display command help                             |

---

**Note:** Module rankings (e.g., Excellent, Great, Normal, Average) indicate reliability and stability. See the [Metasploit Wiki - Exploit Ranking](https://github.com/rapid7/metasploit-framework/wiki/Exploit-Ranking) for more details.

---

## Quick Questions

- ❓How would you set the LPORT value to 6666?
  - set LPORT 6666

- ❓How would you set the global value for RHOSTS to 10.10.19.23 ?
  - setg RHOSTS 10.10.19.23

- ❓What command would you use to clear a set payload?
  - unset PAYLOAD

- ❓What command do you use to proceed with the exploitation phase?
  - exploit
