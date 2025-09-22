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
