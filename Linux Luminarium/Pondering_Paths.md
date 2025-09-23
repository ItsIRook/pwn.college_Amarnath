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
- which lead me to the `include`, from there I invoked `/challenge/run`.
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
- I learned the usage of `cd` command and in this scenerio I used the command to change directory from root to `/usr/include` which contained many programs which enabled me to use the `run` program from the absolute path `/challenge/run`.

---
# 🔹 Position thy self
In this challenege, the user uses cd command to get into `/usr/include` to run the command `run` from `/challenge/run`.

### 🏴 Flag
`pwn.college{0CuNWD3lzRhiOHu-SW52AVG0NXA.QX2QTN0wCO0gjNzEzW}`

### ⚡ How I Solved
- I executed `/challenge/run` which displayed that I should be in `/usr/include` directory to use the command.
- I simply typed `cd /usr/include` in the terminal.
- which lead me to the `include`, from there I invoked `/challenge/run`.
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
- I learned the usage of `cd` command and in this scenerio I used the command to change directory from root to `/usr/include` which contained many programs which enabled me to use the `run` program from the absolute path `/challenge/run`.

---
