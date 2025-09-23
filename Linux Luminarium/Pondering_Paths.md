# 🔹 The Root
In this challenge, the user invokes a program `pwn` by giving the path to the program (here its in the root folder so `/pwn`).

### 🏴 Flag
`pwn.college{ws1orsx1ryEdUXt-3Tv1NNN43qd.QX4cTO0wCO0gjNzEzW}`

### ⚡ How I Solved
I simply typed `/pwn` in the terminal.  
The command was executed and the flag was displayed.

```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{ws1orsx1ryEdUXt-3Tv1NNN43qd.QX4cTO0wCO0gjNzEzW}
hacker@paths~the-root:~$
```

### 📚 What I Learned
- I learned that root folder can be accessed by `/`.  
- Programs can be directly invoked by giving the path to the program while executing.

---
# 🔹 Program and Absolute Paths
In this challenege, the user invokes a program `run` which has an absolute path of `/challenge/run`.

### 🏴 Flag
`pwn.college{IlyzhpSTAOvyZA13ZU-Bm59ddkR.QX1QTN0wCO0gjNzEzW}`

### ⚡ How I Solved
I simply typed `/challenge/run` in the terminal.
The command was executed and the flag was displayed.

```
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{IlyzhpSTAOvyZA13ZU-Bm59ddkR.QX1QTN0wCO0gjNzEzW}
hacker@paths~program-and-absolute-paths:~$
```

### 📚 What I Learned
- I learned that programs can be accessed by giving their absolute path while executing them in the terminal.

---
# 🔹 Position thy self
In this challenege, the user uses cd command to get into `/usr/include` to run the command `run` from `/challenge/run`.

### 🏴 Flag
`pwn.college{0CuNWD3lzRhiOHu-SW52AVG0NXA.QX2QTN0wCO0gjNzEzW}`

### ⚡ How I Solved
- I executed `/challenge/run` which displayed that I should be in `/usr/include` directory to use the command.
- I simply typed `cd /usr/include` in the terminal.
- which lead me to the `/include`, from there I invoked `/challenge/run`.
- The command was executed and the flag was displayed.

```
hacker@paths~position-thy-self:~$ cd /usr/include
hacker@paths~position-thy-self:/usr/include$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{0CuNWD3lzRhiOHu-SW52AVG0NXA.QX2QTN0wCO0gjNzEzW}
hacker@paths~position-thy-self:/usr/include$
```

### 📚 What I Learned
- I learned the usage of `cd` command and in this scenerio I used the command to change directory from root to `/usr/include` after which I ran the command with absolute path `/challenege/run` to obtain the flag.

---
# 🔹 Position Elsewhere
In this challenege, the user uses cd command to get into `/home` to run the command `run` from `/challenge/run`.

### 🏴 Flag
`pwn.college{YxSaG4yFJ-HbkUodE8cvk4uDIQ_.QX3QTN0wCO0gjNzEzW}`

### ⚡ How I Solved
- I executed `/challenge/run` which displayed that I should be in `/home` directory to use the command.
- I simply typed `cd /home` in the terminal.
- which lead me to the `/home`, from there I invoked `/challenge/run`.
- The command was executed and the flag was displayed.

```
hacker@paths~position-elsewhere:~$ cd /home
hacker@paths~position-elsewhere:/home$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{YxSaG4yFJ-HbkUodE8cvk4uDIQ_.QX3QTN0wCO0gjNzEzW}
hacker@paths~position-elsewhere:/home$
```

### 📚 What I Learned
- I learned the usage of `cd` command and in this scenerio I used the command to change directory from current working directory to `/home` which contained a folder `hacker`, then I was expected to type in the absolute path for the program `run` to execute it.
---
# 🔹 Position yet Elsewhere
In this challenege, the user uses cd command to get into `/home` to run the command `run` from `/challenge/run`.

### 🏴 Flag
`pwn.college{QcAx6VhJYgAusSTeQF6yqIbxq7B.QX4QTN0wCO0gjNzEzW}`

### ⚡ How I Solved
- I executed `/challenge/run` which displayed that I should be in `/sys/kernel` directory to use the command.
- I simply typed `cd /sys/kernal` in the terminal.
- which lead me to the `/sys/kernal`, from there I invoked `/challenge/run`.
- The command was executed and the flag was displayed.

```
hacker@paths~position-yet-elsewhere:~$ cd /sys/kernel
hacker@paths~position-yet-elsewhere:/sys/kernel$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{QcAx6VhJYgAusSTeQF6yqIbxq7B.QX4QTN0wCO0gjNzEzW}
hacker@paths~position-yet-elsewhere:/sys/kernel$
```

### 📚 What I Learned
- I learned the usage of `cd` command and in this scenerio I used the command to change directory from current working directory to `/sys/kernal` which contained many files, then I was expected to type in the absolute path for the program `run` to execute it.
---
# 🔹 Implicit Relative Paths, From /
In this challenege, the user uses cd command to get into `/home` to run the command `run` from `/challenge/run`.

### 🏴 Flag
`pwn.college{gB7PN_WzBxh2hhzJmx3MGa9iyHj.QX5QTN0wCO0gjNzEzW}`

### ⚡ How I Solved
- I simply typed `cd /` in the terminal.
- I invoked `/challenge/run`.
- The command was executed and the flag was displayed.

```
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{gB7PN_WzBxh2hhzJmx3MGa9iyHj.QX5QTN0wCO0gjNzEzW}
hacker@paths~implicit-relative-paths-from-:/$
```

### 📚 What I Learned
- I learned how to access a file in some location using relative path.
- Imagine we want to access some file located at /tmp/a/b/my_file.

  - If my cwd is /, then a relative path to the file is tmp/a/b/my_file.
  - If my cwd is /tmp, then a relative path to the file is a/b/my_file.
  - If my cwd is /tmp/a/b/c, then a relative path to the file is ../my_file. The .. refers to the parent directory.

---
# 🔹 Position Elsewhere
In this challenege, the user uses cd command to get into `/home` to run the command `run` from `/challenge/run`.

### 🏴 Flag
`pwn.college{QcAx6VhJYgAusSTeQF6yqIbxq7B.QX4QTN0wCO0gjNzEzW}`

### ⚡ How I Solved
- I executed `/challenge/run` which displayed that I should be in `/sys/kernel` directory to use the command.
- I simply typed `cd /sys/kernal` in the terminal.
- which lead me to the `/sys/kernal`, from there I invoked `/challenge/run`.
- The command was executed and the flag was displayed.

```
hacker@paths~position-yet-elsewhere:~$ cd /sys/kernel
hacker@paths~position-yet-elsewhere:/sys/kernel$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{QcAx6VhJYgAusSTeQF6yqIbxq7B.QX4QTN0wCO0gjNzEzW}
hacker@paths~position-yet-elsewhere:/sys/kernel$
```

### 📚 What I Learned
- I learned the usage of `cd` command and in this scenerio I used the command to change directory from current working directory to `/sys/kernal` which contained many files, then I was expected to type in the absolute path for the program `run` to execute it.
---
