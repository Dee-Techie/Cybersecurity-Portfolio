# 🐧 Linux Shells

## 🎏What is Linux?

"Linux" is a family of open-source systems built on UNIX. Because it's open-source, developers have created many different versions (called distributions), each tailored for specific needs. Popular distributions like Ubuntu and Debian are super flexible. For example, Ubuntu can be used as a full desktop OS or a server for hosting websites and applications.

👉 In this series, we’ll be using Ubuntu as our go-to Linux distro.

💡 Fun Fact: Ubuntu Server is lightweight — it can run with just 512MB of RAM!

---
## 💻 How to interact with Shell?

Most Linux distributions use Bash (Bourne Again Shell) as their default shell. However, the default shell displayed when you open the terminal depends on your Linux distribution. When interacting with a shell, you must be in the directory where you want to perform operations. By default, when you open a shell in most of the Linux distributions, you will be in your home directory. Here are some commands to help you maneuver through Linux :


| 📂 Command | 📖 Description |
|----------|-------------|
| echo |  Output any text that we provide  |
| whoami |  Find out what user we're currently logged in as!  |
| ls |  Listing (list the contents of a directory) |
| cd |  Change directory (for changing the directory/folder) |
| cat |  concatenate (outputting the Contents of a File) |
| pwd |  Print working directory (to find the full Path to our Current Working Directory) |
| find  |  to find files (e.g. find -name *.txt)  |
| grep |  search for any word or pattern inside a file ( search for specific entries/keyword in a huge file). E.g. grep Word Dictionary.txt  |
| --help | will list the possible options that the command accepts, provide a brief description and example of how to use it |
| man | manual pages. E.g. man ls |

---

### Linux Shell Operators
| 🧩 Symbol / Operator | 📒 Description |
|----------|-------------|
| & |  This operator allows us to execute commands in the background  |
| && |  This operator allows you to combine multiple commands together in one line of your terminal. E.g. command1 && command2. However, it's worth noting that command2 will only run if command1 was successful  |
| > |  This operator is a redirector - meaning that we can take the output from a command (such as using cat to output a file) and direct it elsewhere  |
| >> |  This operator does the same function of the > operator but appends the output rather than replacing (meaning nothing is overwritten)  |

---

## 🧠 Types of Linux Shells
Linux distributions come with several types of shells, each with its own unique set of features.
> - To see which shell you are using, type the following command: echo $SHELL
> - To list down the available shells in your Linux OS use : cat /etc/shells
![image](https://github.com/user-attachments/assets/4615546f-c668-4ee2-ab16-3eec565ee3eb)

> - To switch between the shells, just type the shell name
![image](https://github.com/user-attachments/assets/fdbd122e-7342-4bd0-8aea-51cdb085d691)
 
> - To permanently change the default Shell use : chsh -s /usr/bin/__ (replace __ with bash, zsh, tmux, etc.)

### ⚙️ BASH (Bourne Again Shell)
Bourne Again Shell (Bash) is the default shell for most Linux distributions.
- Least user friendly.
- it also supports scripting, making it a great tool for automating tasks; widely compatible scripting with extensive documentation available.
- Basic Tab completion - Start typing a command or filename, then hit Tab, and Bash will either auto-complete it or suggest possible options.
- Basic customization available.
- Bash also keeps track of everything you type in a history file. You can scroll through previous commands using the up/down arrow keys, or just type **<ins>history</ins>** to see your full command list. This makes it super easy to repeat or tweak past commands without retyping them.

### 🐠 FISH (Friendly Interactive Shell)
Not a default in most Linux distributions. However, its more user-friendly.
- It offers a very simple syntax, which is feasible for beginner users.
- It offers limited scripting features as compared to the other two shells.
- Advance tab completion
- Unlike bash, it has auto spell correction for the commands you write.
- You can customize the command prompt with some cool themes using fish.
- The syntax highlighting feature of fish colors different parts of a command based on their roles, which can improve the readability of commands. It also helps us to spot errors with their unique colors.
- Fish also provides scripting, tab completion, and command history functionality like the shells mentioned in this task.

### 🌀 Zsh (Z Shell)
Considered a modern shell. However, it is too not a default Shell for most of the Linux distributions.
- Very user friendly cause of the level of customization that is available.
- It offers an excellent level of scripting, combining the traditional capabilities of Bash shell with some extra features.
- Zsh provides advanced tab completion and is also capable of writing scripts, thanks to the plug-ins.
- Just like fish, it also provides auto spell correction for the commands.
- It offers extensive customization that may make it slower than other shells (through oh-my-zsh framework.).
- It also provides command history functionality, and several other features.

---

## ⚡ Shell Scripting and Components
Shell scripting allows users to automate repetitive tasks by combining several commands into a single executable file, which can be run at once.

To create a script we first need to create a file using any text editor for the script. The file must be named with an extension .sh, the default extension for bash scripts. 

> Every shell script should begin with a shebang — a special line that tells the system which interpreter to use to run the script. It starts with #!, followed by the path to the interpreter.
Since we're writing our script using Bash, we'll specify Bash as the interpreter in the shebang line. Here's how your first script <ins>(first_script.sh)</ins> should start: <ins>#!/bin/bash</ins>

Next, there are some fundamental building blocks of a script that together make an efficient script.




