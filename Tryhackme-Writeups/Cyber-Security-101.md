# Room Name: Introduction to Cyber Security 101 🔐🛡️

**Platform:** TryHackMe 💻  
**Difficulty:** Beginner 🟢  
**Number of Labs completed:** 54 ⏳

---

## 📝 Summary

### This room introduces fundamental cybersecurity concepts such as 
- 🔐 Computer networking and cryptography
- 🐧 MS Windows, Active Directory, and Linux basics
- 🧨Offensive security tools and system exploitation (Hydra, Gobuster, OWASP, Burp Suite, SQL)
- 🛠️ Defensive security solutions and tools (CAPA, CyberChef, REMnux, FlareVM)

---

## 🔍 Objectives Covered

- 🛡️ Gain a strong foundation in core cybersecurity principles, including the CIA Triad, and develop essential skills in Linux, Windows, and Active Directory administration.
- 🌐 Deepen understanding of networking concepts and protocols, and get hands-on with tools such as Wireshark, Tcpdump, and Nmap.
- 🔐 Explore the fundamentals of cryptography, including public key encryption, hashing, and password cracking tools like John the Ripper.
- 💥 Learn exploitation techniques, including topics like Moniker Link abuse, Metasploit, and common Windows vulnerabilities (e.g., BlueKeep).
- 🕸️ Practice web application hacking, covering JavaScript vulnerabilities, SQL injection, and using tools like Burp Suite and frameworks such as OWASP Top 10.
- ⚔️ Understand both offensive and defensive security concepts to better assess and secure systems.
- 🧰 Get introduced to key security solutions such as SIEM tools, firewalls, intrusion detection systems (IDS), and vulnerability scanners.

---

## ⚙️ Tools Used

- TryHackMe virtual environment for both Linux & Windows 🖥️  
- Networking Tools : Wireshark, Tcpdump & Nmap
- Cryptography : Jack the Ripper
- Exploitation : Moniker Link, Metasploit, Blue
- Web Hacking : Burp Suite, OWASP Top 10
- Offensive : Hydra, Gobuster, SQL Map
- Defensive : CyberChef, CAPA, REMNux, FlareVM
  
---

## 📝 Write Up - Windows Command Line

### 🔐 Basic System Information
- ver: Shows the operating system version.
- systeminfo: Provides detailed system info like OS, processor, and memory.
- driverquery | more: Lists installed drivers, showing one page at a time.
- help: Displays help for specific commands.
- cls: Clears the command prompt screen.

### 🌐 Network Configuration
- ipconfig: Shows basic network info like IP address and subnet mask.
- ipconfig /all: Displays detailed network info, including DNS servers and DHCP status.
  
### 📡 Network Troubleshooting
- ping [target_name]: Tests network connectivity by sending ICMP packets.
- tracert [target_name]: Traces the network route to a target, showing each hop along the way.
  
### 📢 More Networking Commands
- nslookup [domain]: Finds the IP address for a domain name.
- netstat -abon: Displays current network connections, listening ports, and the associated programs/process IDs.

### 🎫 File and Disk Management

#### 🧾 Working With Directories
- cd: Displays the current directory or changes directories.
- dir: Lists the files in a directory.
- dir /a: Shows hidden files.
- dir /s: Lists files in the current directory and subdirectories.
- mkdir [directory_name]: Creates a new directory.
- rmdir [directory_name]: Removes a directory.
- tree: Shows a visual representation of directories and subdirectories.

#### 📄 Working With Files
- type [file]: Displays the contents of a text file.
- more [file]: Shows a file's content one page at a time.
- copy [file] [destination]: Copies a file to a new location.
- move [file] [destination]: Moves a file to a new location.
- **del [file] or erase [file]: Deletes a file.
- copy *.md [destination]: Copies all files with the .md extension to the destination folder.

#### 📑 Task and Process Management
- tasklist: Displays a list of running processes.
- tasklist /FI "imagename eq [process_name]": Filters the tasklist for a specific process (e.g., notepad.exe).
- taskkill /PID [pid]: Terminates a process by its process ID (PID).
