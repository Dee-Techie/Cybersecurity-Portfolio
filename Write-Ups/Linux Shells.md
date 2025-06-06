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
> - To list down the available shells in your Linux OS use : **cat /etc/shells**
![image](https://github.com/user-attachments/assets/4615546f-c668-4ee2-ab16-3eec565ee3eb)

> - To switch between the shells, just type the shell name
![image](https://github.com/user-attachments/assets/fdbd122e-7342-4bd0-8aea-51cdb085d691)
 
> - To permanently change the default Shell use : **chsh -s /usr/bin/__ (replace __ with bash, zsh, tmux, etc.)**

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

To create a script we first need to create a file using any text editor for the script. The file must be named with an extension .sh, the default extension for bash scripts. E.g. first_script.sh 

> Every shell script should begin with a shebang — a special line that tells the system which interpreter to use to run the script. It starts with #!, followed by the path to the interpreter.
Since we're writing our script using Bash, we'll specify Bash as the interpreter in the shebang line. Here's how your first script <ins>(first_script.sh)</ins> should start: **<ins>#!/bin/bash</ins>**

- ✅ Step 1: Open Your Terminal
Launch the terminal in your Linux environment. We’ll be writing and executing commands here.

- 📁 Step 2: Create a New Script File
Use a text editor like nano to start writing directly: nano first_script.sh
This opens the nano text editor and creates a file called first_script.sh.

- 🧾 Step 3: Add a Shebang
At the very top of your file, add: <ins>#!/bin/bash</ins>
This tells Linux to use Bash to run your script.

- 🖊️ Step 4: Write Your Script
Add some simple commands below the shebang. For example: 
#!/bin/bash
   - echo "Hello, Cyber World!🌐 What is your name?"
   - read name
   - echo "Welcome, $name"
Press CTRL + O to save, then Enter, and CTRL + X to exit if you're using nano.

- 🔒 Step 5: Make the Script Executable
Give your script permission to run:
chmod +x first_script.sh

- 🚀 Step 6: Run the Script
Now execute your script by typing:
./first_script.sh

> We use ./ before the script to run rather than typing the script name directly because ./ tells the shell to execute the file that is present in the current directory. If you don't define ./ before the script name, the shell will search the script in the PATH environment variable (that contains all the directories except the current one), and it will not find the defined script in any of those directories and generate an error.

- ✅ You should see:
   - Hello, Cyber World!🌐 What is your name?
   - Reply > XYX
   - Welcome, XYZ

### Next, there are some fundamental building blocks of a script that together make an efficient script.

### <ins>Variables</ins>:
A variable stores a value inside it. Suppose you need to use some complex values, like a URL, a file path, etc., several times in your script. Instead of memorizing and writing them repeatedly, you can store them in a variable and use the variable name wherever you need it. In the example above <ins>"name" is a variable in which the input would be stored</ins>.

### <ins>Loop</ins> :
Loop, as the name suggests, is something that is repeating. let’s write a loop that will display all numbers starting from 1 to 10 on the screen. First, create a new file named loop_script.sh, then enter the code below. Save your file by pressing CRTL+X, then confirm with y and then ENTER.

![image](https://github.com/user-attachments/assets/12ba21f4-ec76-4416-9796-ec646b3e5389)

Here do indicates the start of the loop code, and done indicates the end.

The output will be

![image](https://github.com/user-attachments/assets/2cca9546-cd4d-4060-bfc0-86299ac23032)

### <ins>Conditional Statements</ins> :
Conditional statements are an essential part of scripting. They help you execute a specific code only when a condition is satisfied. For eg if we want to make a script that shows the user a secret. However, we want it to be shown to only some users (the high-authority user). We will create a conditional statement that will first ask the user their name, and if that name matches the high authority user’s name, it will display the secret. 

To do so, we first, create a new file named conditional_script.sh, then enter the code below. Save your file by pressing CRTL+X, then confirm with y and then ENTER.

![image](https://github.com/user-attachments/assets/338c300c-9a71-4f5b-91dc-ec6d8128e7ee)

The above script takes the user’s name as input and stores it into a variable. The conditional statement starts with if and compares the value of that variable with the string Stewart; if it’s a match, it will display the secret to the user, or else it will not. The fi is used to end the for loop.

Output to an authorized user

![image](https://github.com/user-attachments/assets/b4b24aae-d8df-4027-a44e-63174140151a)

Output to an un-authorized user

![image](https://github.com/user-attachments/assets/83711272-76ef-4117-a85c-d1e33c5620f8)

---

### 🚨  A good script always has some comments. 

Comments don’t affect the working of any script but make it easier to read.  A comment is a sentence that we write in our code just for the sake of our understanding. It is written with a # sign followed by a space and the sentence we need to write.

![image](https://github.com/user-attachments/assets/7f470824-309f-4ed5-a40b-c0fe66849b77)

---

## 🚠 Basic Authentication Script examples
![image](https://github.com/user-attachments/assets/1464d5fa-97f4-46a9-9cde-4cd3e8ada733)












