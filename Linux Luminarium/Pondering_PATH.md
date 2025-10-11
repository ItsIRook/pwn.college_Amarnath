# 🔹 The PATH Variable

In this level, the challenge program tries to `rm /flag`. If the shell can't find `rm` because the `PATH` is empty, the removal fails and the challenge rewards you with the flag.

### 🏴 Flag

`pwn.college{EyODGUp4JJiq-4efeDk8rrCVXNs.QX2cDM1wCO0gjNzEzW}`

### ⚡ How I Solved

* I removed the directories from my shell's `PATH` so child processes couldn't locate `rm`.
* Then I executed the challenge program; its attempt to remove `/flag` failed because `rm` couldn't be found.
* The challenge noticed the failure and printed the flag.

```bash
# Clear PATH in the current shell so child processes inherit it
hacker@path~the-path-variable:~$ PATH=""
# Now the challenge can't find rm
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{EyODGUp4JJiq-4efeDk8rrCVXNs.QX2cDM1wCO0gjNzEzW}
```

### 📚 What I Learned

* The shell searches for commands using the `PATH` environment variable (a colon-separated list of directories).
* Child processes inherit the parent's environment, so clearing `PATH` in your shell prevents programs you launch from finding external commands like `rm`.
* Manipulating `PATH` can be a powerful tool — for defense (sandboxing) or exploitation — but be careful: blanking `PATH` breaks many useful commands.

---
# 🔹 Setting PATH

This level practices using the `PATH` environment variable to make programs callable by their bare names. The `win` command lives in `/challenge/more_commands/`, so placing that directory into `PATH` (or replacing `PATH` with it) lets you run `win` directly.

### 🏴 Flag

`pwn.college{I0JVrTzKTb52gm5d9FbL5YSBdFT.QX1cjM1wCO0gjNzEzW}`

### ⚡ How I Solved

* I set `PATH` so the shell would search `/challenge/more_commands/` for commands:

```bash
hacker@path~setting-path:~$ PATH=/challenge/more_commands/
```

* Then I ran the challenge; it invoked `win` by bare name and printed the flag:

```bash
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{I0JVrTzKTb52gm5d9FbL5YSBdFT.QX1cjM1wCO0gjNzEzW}
```

### 📚 What I Learned

* `PATH` is a colon-separated list of directories the shell searches for executables when you type a bare command name.
* Overwriting `PATH` with a directory that contains the desired program makes that program invokable without a full path.
* Be careful when changing `PATH`: replacing it entirely can make many standard commands unavailable; prefer prepending/appending when appropriate (e.g., `PATH=/my/bin:$PATH`).

---
# 🔹 Finding Commands

In this challenge you must locate a `win` program that was placed somewhere in your `$PATH`. The `which` command searches each directory in `$PATH` in order and prints the first matching executable it finds. Once you locate `win`, use its directory path to `cat` the adjacent flag file.

### 🏴 Flag

`pwn.college{I96x_IlsFoYRt072ychGVs2uDwD.01NzEzNxwCO0gjNzEzW}`

### ⚡ How I Solved

* I used `which win` to discover where `win` lives.
* I read the flag file in the same directory with `cat`.

```
hacker@path~finding-commands:~$ which win
/challenge/paths/26958/win
hacker@path~finding-commands:~$ cat /challenge/paths/26958/flag
pwn.college{I96x_IlsFoYRt072ychGVs2uDwD.01NzEzNxwCO0gjNzEzW}
hacker@path~finding-commands:~$
```

### 📚 What I Learned

* The shell executes the first matching executable it finds by scanning each directory listed in `$PATH` (unless the command is a shell builtin).
* Use `which <name>` to see precisely which file would run when you type a command name.
* Once you have the full path to an executable, you can inspect other files in the same directory (for example, a `flag` file) by using that path.

---
