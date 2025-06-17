# 🐧🐧 Linux Commands for a Level 1 SOC Analyst (Top 50)

A Level 1 SOC Analyst primarily focuses on monitoring, detection, and initial response. Their command usage will lean heavily on navigating the system, viewing logs, and understanding basic network activity.

![IpfsInterPlanetaryFileSystemGIF](https://github.com/user-attachments/assets/b317c53f-51dc-44ba-8978-ea8c2c82daf4)

## File System & Navigation:

- ls: Lists files and directories in the current location.
- cd: Changes the current directory.
- cd ../directoryx: To go to directoryx 
- pwd: Prints the full path of the current working directory.
- cat: Displays the content of a file.
- less: Views file content page by page, allowing scrolling.
- more: Similar to less, views file content page by page.
- head: Displays the first few lines of a file (useful for logs).
- tail: Displays the last few lines of a file (essential for live log monitoring).
- grep: Searches for patterns (text) within files or command output.
- find: Searches for files and directories based on various criteria (name, size, type, etc.).
- cp: Copies files and directories.
- mv: Moves or renames files and directories.
- rm: Removes files or directories (use with extreme caution!).
- mkdir: Creates a new directory.
- touch: Creates an empty file or updates a file's timestamp.

## System Information & Monitoring:

- whoami: Displays the current username.
- id: Displays user and group information for the current user.
- ps: Displays a snapshot of current processes.
- top: Provides a dynamic, real-time view of running processes and system resources.
- df: Reports disk space usage of file systems.
- du: Estimates file space usage.
- free: Displays amount of free and used memory in the system.
- uptime: Shows how long the system has been running, number of users, and load averages.
- history: Displays previously executed commands.
- dmesg: Displays the kernel ring buffer messages (boot messages, hardware issues).
- journalctl: Queries and displays messages from the systemd journal (modern log viewing).

## Network Basics:

- ping: Tests network connectivity to a host.
- ip a (or ifconfig on older systems): Displays IP addresses and network interface information.
- netstat: Displays network connections, routing tables, and interface statistics (being deprecated by ss and ip).
- ss: Displays socket statistics, faster alternative to netstat.
- traceroute: Traces the route packets take to a network host.
- dig: A flexible tool for querying DNS name servers.
- nslookup: Queries internet domain name servers (DNS lookup).

## Permissions & Ownership:

- chmod: Changes file permissions.
- chown: Changes file owner and group.

## Basic Security & Utilities:

- sudo: Executes a command as the superuser (root) or another user.
- man: Displays the manual page for a command (e.g., man ls).
- date: Displays or sets the system date and time.
- passwd: Changes a user's password.
- ssh: Securely connects to a remote server.
- scp: Securely copies files between hosts using SSH.
- wget: Non-interactive network downloader.
- curl: Transfers data from or to a server using various protocols.
- tar: Archives and extracts files (often used for backups/log bundles).
- gzip: Compresses files.
- gunzip: Decompresses files.
- unzip: Extracts files from ZIP archives.
- apt (Debian/Ubuntu) / yum (CentOS/RHEL): Package managers for installing/removing software.
- who: Shows who is logged on.
- last: Shows a listing of last logged in users.

# More Advanced Linux Commands for Cybersecurity Professionals (Beyond SOC L1)

As you progress in cybersecurity, especially into roles like incident response, penetration testing, security engineering, or forensics, you'll need a deeper understanding and wider array of commands.

## Advanced System & Process Management:

- htop: An interactive process viewer, more user-friendly than top.
- lsof: Lists open files and the processes that opened them (critical for understanding system activity).
- kill: Sends a signal to terminate a process by PID.
- pkill: Kills processes by name.
- nice / renice: Changes the scheduling priority of processes.
- bg / fg: Moves processes to the background or foreground.
- systemctl: Manages systemd services (start, stop, enable, disable services).
- service: Controls SysVinit scripts (older way to manage services).
- crontab: Schedules commands to run periodically.
- chroot: Changes the root directory for a process and its children (useful for forensics, isolation).
- strace: Traces system calls and signals (debugging and understanding program behavior).
- ltrace: Traces library calls (debugging and understanding program behavior).

## Advanced Network & Security Tools:

- tcpdump: Command-line packet analyzer; captures network traffic.
- wireshark: GUI-based network protocol analyzer (often used with tcpdump for capture, then wireshark for analysis).
- nmap: Network discovery and security auditing tool (port scanning, OS detection, service version detection).
- iptables / nftables: Configures kernel firewall rules.
- ufw: Uncomplicated Firewall, a user-friendly interface for iptables.
- route: Shows/manipulates the IP routing table.
- arp: Displays or modifies the Address Resolution Protocol (ARP) cache.
- whois: Retrieves domain registration information.
- host: Simple utility for performing DNS lookups.
- openssl: Versatile command-line tool for SSL/TLS, certificates, cryptography.
- gpg: GNU Privacy Guard, for encryption and digital signatures (similar to PGP).
- john (John the Ripper): Password cracking tool.
- hydra: Brute-force login cracker.
- aircrack-ng: Suite of tools for auditing wireless networks.
- netcat (nc): A versatile networking utility for reading/writing to network connections (often called the "TCP/IP Swiss Army knife").
- socat: A more advanced netcat, often used for complex network redirections and tunnels.
- sshd_config (file, not command): The configuration file for the SSH daemon, essential for securing SSH.
- sysctl: Configures kernel parameters at runtime (e.g., enabling/disabling IP forwarding).

## Log & File Analysis (Advanced):

- awk: Powerful text processing tool for pattern scanning and processing language.
- sed: Stream editor for filtering and transforming text.
- cut: Removes sections from each line of files.
- sort: Sorts lines of text files.
- uniq: Reports or omits repeated lines.
- wc: Prints newline, word, and byte counts for files.
- xargs: Builds and executes command lines from standard input (powerful for combining commands).
- find . -exec {} \;: Executes a command on each file found by find.
- grep -r: Recursive grep through directories.

## User Management & Forensics (Advanced):

- useradd / adduser: Creates new user accounts.
- userdel / deluser: Deletes user accounts.
- usermod: Modifies user account properties.
- groupadd / addgroup: Creates new groups.
- groupdel / delgroup: Deletes groups.
- groups: Prints the names of the primary and any supplementary groups for each given USER.
- logrotate: Manages automatic rotation, compression, and removal of log files.
- strings: Finds printable strings in files (useful for binary analysis).
- file: Determines file type.
- dd: Converts and copies a file (useful for disk imaging in forensics).
- mount / umount: Mounts and unmounts file systems.

This list provides a solid foundation. The true power comes from understanding how to combine these commands using pipes (|), redirection (>, >>), and scripting (Bash, Python) to automate tasks and build more complex analysis workflows. Continuous learning and hands-on practice are key in cybersecurity!
