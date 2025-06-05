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

- <ins>Get-Content</ins> (read file content) – similar to type in CMD and cat in Linux.
- <ins>Set-Location</ins> (change directory) – similar to cd in CMD/Linux.
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
- <ins>Where-Object</ins> filters the files by their Extension property (.txt)
