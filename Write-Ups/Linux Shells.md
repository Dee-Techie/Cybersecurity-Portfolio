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
> - To switch between the shells, just type the shell name
 <img width="262" alt="image" src="https://github.com/user-attachments/assets/9efa887c-6674-4bb1-9f65-e636f1d4dc07" />

