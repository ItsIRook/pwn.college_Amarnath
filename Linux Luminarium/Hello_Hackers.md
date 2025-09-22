# 🔹 Intro to Commands
In this challenge, the user invokes their very first command: `hello`.

### 🏴 Flag
`pwn.college{Ieswv42nQuGHzh3QQicda3luFuf.QX3YjM1wCO0gjNzEzW}`

### ⚡ How I Solved
I simply typed `hello` in the terminal.  
The command was executed and the flag was displayed.

<pre> ```bashhacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{Ieswv42nQuGHzh3QQicda3luFuf.QX3YjM1wCO0gjNzEzW}
hacker@hello~intro-to-commands:~$``` </pre>

### 📚 What I Learned
- How to invoke a command in Linux.  
- The terminal is **case-sensitive**: `hello` works, but `HELLO` does not.

---

# 🔹 Intro to Arguments
This challenge required running the `hello` command with one argument: `hackers`.

### 🏴 Flag
`pwn.college{4D7bUAVIqmq2a-ggw-edzo8to7x.QX4YjM1wCO0gjNzEzW}`

### ⚡ How I Solved
I entered: `hello hackers`
and obtained the flag.

![Intro to Arguments](argument.png)

### 📚 What I Learned
- How to use **arguments** with commands.  
- Arguments are also **case-sensitive**.

---

# 🔹 Command History
In this challenge, the user explores the command history using the arrow keys.

### 🏴 Flag
`pwn.college{AeQtBPsIeq1cro1tL5SeTfXrPKv.0lNzEzNxwCO0gjNzEzW}`

### ⚡ How I Solved
I pressed the **Up Arrow** key to cycle through previous commands.  
One of the recalled commands revealed the flag.

![Command History](history.png)

### 📚 What I Learned
- The **Up/Down arrows** allow quick access to previously executed commands.  
- Useful for avoiding retyping long or repetitive commands.

---
