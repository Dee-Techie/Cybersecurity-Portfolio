# 🏎 Windows PowerShell

PowerShell is designed for task automation and configuration management. It combines a command-line interface and a scripting language built on the .NET framework. Unlike older text-based command-line tools, PowerShell is object-oriented, which means it can handle complex data types and interact with system components more effectively. Its designed to run on Windows, macOS, and Linux.

---

## 🌋The Power in PowerShell
To fully grasp the power of PowerShell, we first need to understand what an object is in this context.

In programming, an object represents an <ins> item with properties (characteristics) and methods (actions) </ins>. For example, a car object might have properties like Color, Model, and FuelLevel, and methods like Drive(), HonkHorn(), and Refuel().

Similarly, in PowerShell, objects are fundamental units that encapsulate data and functionality and can contain file names, usernames or sizes as data (properties), and carry functions (methods) such as copying a file or stopping a process. When a <ins>**cmdlet (pronounced command-let)**</ins> is run in PowerShell, it returns objects that retain their properties and methods. This allows for more powerful and flexible data manipulation since these objects do not require additional parsing of text.

---
> CMD vs PowerShell:

- CMD is text-based (like dir, echo).
- PowerShell returns objects (e.g., Get-ChildItem, Write-Output).

---

## 🧪PowerShell Basics

PowerShell uses cmdlets (command-lets), which follow a consistent Verb-Noun naming convention, making commands easier to understand - the Verb describes the action, and the Noun specifies the object on which action is performed.

### ⚓Common Commands:

- <ins>Set-Location</ins> (change directory) – similar to cd in CMD/Linux. E.g. <ins>Set-Location C:\Users\XYZ</ins> to change directory
- <ins>Get-Command</ins> (list all commands) – helps discover available cmdlets. E.g. <ins>Get-Command -Name Remove*</ins> retrieves a list of commands that start with the verb Remove.
- <ins>Get-Help</ins> - it provides detailed information about cmdlets, including usage, parameters, and examples. E.g. <ins>Get-Help New-LocalUser -examples</ins> retrieves some example usage for the cmdlet New-LocalUser
- <ins>Get-Alias</ins> - lists all aliases available (lists alternative names for cmdlets— for many traditional Windows commands).
- <ins>Get-ChildItem</ins> (list directory contents) – like dir in CMD or ls in Linux. E.g. <ins>Get-ChildItem -Path C:\Users</ins> displays the content of the "C:\Users" directory.
- <ins>Set-Location</ins> (navigate directories) – like cd in CMD/Linux.
- <ins>New-Item</ins> (create a file or directory) – similar to mkdir or touch.
- <ins>Remove-Item</ins> (delete file/directory) – like del or rmdir in CMD.
- <ins>Get-Content</ins> (read file content) – similar to type in CMD and cat in Linux. E.g. <ins>Get-Content -Path C:\Users</ins> displays contents of the C:\Users directory.
  
Launching PowerShell: Can be done via "Start" Menu, Run dialog (Win + R), or typing powershell in CMD.

---

## 🧩Piping, Filtering, and Sorting Data

Piping lets you connect commands so that one command's result goes straight into the next one — like a chain. You use the | symbol to do this. It works in both Windows and Linux command lines. In PowerShell, piping is even smarter because it passes full objects (not just plain text). These objects include extra details and actions, making it easier to work with data in powerful ways.

>E.g. <ins>get-childitem | sort-object length</ins> here <ins>Get-ChildItem</ins> lists all the files, and the | (pipe) sends those files to Sort-Object, which organizes them by their size.
- <ins>Sort-object</ins> sorts the files
- <ins>Where-Object</ins> filters the files by their Extension property (.txt). We can use <ins>comparision operators</ins> to define the extension property. Here are some commonly used comparision operators
  - -eq: "equal to"
  - -ne: "not equal"
  - -gt: "greater than"
  - -ge: "greater than or equal to"
  - -lt: "less than"
  - -le: "less than or equal to"
  - -like: selecting properties that match

> E.g. GetChildItem | Where -Object -Property "Name" -like "Ship*"
- <ins>Select-Object</ins> is used to select specific properties from objects or limit the number of objects returned.
- <ins>Select-String</ins> searches for text patterns within files, similar to grep in Unix-based systems or findstr in Windows Command Prompt.

> E.g. Get-ChildItem | Where-Object -Property Length -gt 100 to retrieve the items in the current directory with size greater than 100.

---

## 💻System and Network Information
- <ins>Get-ComputerInfo</ins> cmdlet retrieves comprehensive system information, including operating system information, hardware specifications, BIOS details, and more.
- <ins>Get-LocalUser</ins> lists all the local user accounts on the system.
- <ins>Get-NetIPConfiguration</ins> provides detailed information about the network interfaces on the system, including IP addresses, DNS servers, and gateway configurations.
- <ins>Get-NetIPAddress</ins> cmdlet will show details for all IP addresses configured on the system, including those that are not currently active.

---
## ⏰Real-Time System Analysis
- <ins>Get-Process</ins> shows all running programs on your system, including how much CPU and memory they’re using. It’s a handy tool for checking what’s going on and fixing issues.
- <ins>Get-Service</ins> shows which services on a computer are running, stopped, or paused. It’s useful for troubleshooting and for spotting anything unusual on the system.
- <ins>Get-NetTCPConnection</ins> shows all current TCP network connections. It's useful in incident response or malware checks to spot suspicious or hidden connections to attackers.
- <ins>Get-FileHash</ins> creates a unique code (hash) for a file. It's helpful in cybersecurity to check if a file has been changed or tampered with.
> E.g. Get-Service | Where-Object { $_.DisplayName -like "*$motto*" } | Select-Object Name, DisplayName

---
## 🎞Scripting
- <ins>Invoke-Command</ins> is essential for executing commands on remote systems.
  - To get more help use <ins>Get-Help Invoke-Command -examples</ins>
> E.g. <ins>Invoke-Command -ComputerName HoneyBadger -ScriptBlock { Get-Service }</ins> is the syntax to execute the command Get-Service on a remote computer named "HoneyBadger", when you do not have the credentials to login..
