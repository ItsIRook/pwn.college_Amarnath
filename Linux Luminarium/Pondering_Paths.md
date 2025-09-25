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

  - If my cwd is `/`, then a relative path to the file is `tmp/a/b/my_file`.
  - If my cwd is `/tmp`, then a relative path to the file is `a/b/my_file`.
  - If my cwd is `/tmp/a/b/c`, then a relative path to the file is `../my_file`. The .. refers to the parent directory.

---
# 🔹 Explicit Relative Paths, From /
In this challenege, the user uses cd command to get into `/` to run the command `run` from `./challenge/run`(the idea is to use `.`.

### 🏴 Flag
`pwn.college{sZtVJ2yDVy4Hx5imCCNCcWoR1eQ.QXwUTN0wCO0gjNzEzW}`

### ⚡ How I Solved
- I simply typed `cd /` in the terminal.
- I invoked `./challenge/run`.
- The command was executed and the flag was displayed

```
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{sZtVJ2yDVy4Hx5imCCNCcWoR1eQ.QXwUTN0wCO0gjNzEzW}
hacker@paths~explicit-relative-paths-from-:/$
```

### 📚 What I Learned
- I learned that in most operating system, every directory has implicit entries that you can reference in paths: `.` and `..`. The first, `.`, refers right to the same directory, so the following absolute paths are identical to each other: 
  - `/challenge`
  - `/challenge/.`
  - `/challenge/./././././././././`
  - `/./././challenge/././`
- The following relative paths are also all identical to each other:
  - `challenge`
  - `./challenge`
  - `./././challenge`
  - `challenge/.`

---
# 🔹 Implicit Relative Paths

In this challenge, you must run run from the /challenge directory. Linux does not search the current directory for programs when you type a naked command name (like run) — that would be unsafe. To explicitly execute a program in the current directory you must use . in the path (for example ./run).

### 🏴 Flag

`pwn.college{E-Q08MPtzdkfJ6TDecp7Dk5CyxY.QXxUTN0wCO0gjNzEzW}`

### ⚡ How I Solved

- I changed into the `/challenge` directory with cd /challenge. 
- I invoked the program with an explicit relative path: `./run`.
- The program ran and printed the flag.

```
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{E-Q08MPtzdkfJ6TDecp7Dk5CyxY.QXxUTN0wCO0gjNzEzW}
hacker@paths~implicit-relative-path:/challenge$
```

### 📚 What I Learned

- Linux avoids implicitly searching the current directory for commands when you give a naked path (e.g. run) as a safety measure.

- To explicitly execute something in the current directory you must prefix it with `./` (dot-slash).

- `.` refers to the current directory; `..` refers to the parent directory. Using `./program` removes ambiguity and tells the shell you mean the program in the current directory.

---
# 🔹 Home Sweet Home

In this challenge you must provide an argument (three characters or less before expansion) that expands to an absolute path inside your home directory. Bash expands a leading `~` to your home directory (`/home/hacker`), so `~/a` becomes `/home/hacker/a` and satisfies the constraints.

### 🏴 Flag
`pwn.college{UerExeWBXmW8YUOK3GcA_dgs_lY.QXzMDO0wCO0gjNzEzW}`

### ⚡ How I Solved
- I ran the program with an argument that uses ~ as shorthand and is three characters before expansion: `/`challenge/run `~/a`.
- /challenge/run wrote the flag to `/home/hacker/a` and printed the flag.

```
hacker@paths~home-sweet-home:~$ /challenge/run ~/a
Writing the file to /home/hacker/a!
... and reading it back to you:
pwn.college{UerExeWBXmW8YUOK3GcA_dgs_lY.QXzMDO0wCO0gjNzEzW}
hacker@paths~home-sweet-home:~$
```

### 📚 What I Learned
- `~` expands to the user’s home directory (/home/hacker) only when it appears at the start of a path.
- `~` expansion happens before the program sees the argument, so passing `~/a` satisfies an "absolute path" requirement after expansion.
- cd with no arguments returns you to your home directory; `~` is a convenient shorthand for home.

---
# 🔹 removing files

Files can pile up; `rm` removes them. Be careful—`rm` permanently deletes (no recycle bin). Basic usage:

```
rm filename
```

In this challenge, a file named `delete_me` is created in your home directory. Remove it, then run `/challenge/check` to verify and receive the flag.

### 🏴 Flag

`pwn.college{QqAmkIOoJsIN9MfN5alnv0cdgmm.QX2kDM1wCO0gjNzEzW}`

### ⚡ How I Solved

* I removed the file using `rm delete_me`.
* I ran `/challenge/check`, which confirmed the removal and printed the flag.

```
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{QqAmkIOoJsIN9MfN5alnv0cdgmm.QX2kDM1wCO0gjNzEzW}
hacker@commands~removing-files:~$
```

### 📚 What I Learned

* `rm <file>` deletes a file—there is no undo in the shell.
* Use caution with `rm`, especially with wildcards or `-r` for recursive deletion.
* After removing a required file, challenge checkers can verify and reward you.

---
# 🔹 moving files

`mv` renames or moves files. Usage:

```bash
mv source target
```

This challenge asks you to move `/flag` into `/tmp/hack-the-planet`, then run `/challenge/check` to verify and reveal the reward.

### 🏴 Flag

`pwn.college{YGyLeMkC2F8e9KQPUS2vi7pgm9T.0VOxEzNxwCO0gjNzEzW}`

### ⚡ How I Solved

* I moved the flag with `mv /flag /tmp/hack-the-planet`.
* I ran `/challenge/check`, which confirmed the move and printed the flag.

```
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{YGyLeMkC2F8e9KQPUS2vi7pgm9T.0VOxEzNxwCO0gjNzEzW}
```

### 📚 What I Learned

* `mv <src> <dst>` moves or renames files and directories.
* Ensure the target path exists or that you specify the desired filename.
* Moving system files may require appropriate permissions.

---
# 🔹 hidden files

Files beginning with a `.` are hidden from `ls` by default. Use `ls -a` to show all entries, including `.` and `..` and dotfiles.

In this challenge the flag is hidden as a dot-prefixed file in the filesystem root. List `/` with `ls -a`, locate the dotfile, and `cat` it to read the flag.

### 🏴 Flag

`pwn.college{cF6Gm-oHxYwzC02eGkB1QSw_yit.QXwUDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I listed the root directory including hidden files with `ls -a /`.
* I found the dot-prefixed file (`.flag-179121076127016`) and used `cat` to read it.

```
hacker@commands~hidden-files:~$ ls -a /
.   .dockerenv             bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-179121076127016  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:~$ cat /.flag-179121076127016
pwn.college{cF6Gm-oHxYwzC02eGkB1QSw_yit.QXwUDO0wCO0gjNzEzW}
hacker@commands~hidden-files:~$
```

### 📚 What I Learned

* `ls -a` shows hidden files (dotfiles) and the `.` and `..` entries.
* Hidden files are simply filenames that start with `.`; they are not magically protected.
* Use `ls -a` when you suspect a file might be hidden.

---
# 🔹 An Epic Filesystem Quest

This challenge is a puzzle hunt using `ls`, `cd`, and `cat`. Start at `/`, find a file named `LEAD` (or similar), `cat` it to get a clue that points to the next location, and repeat until you reach the flag.

Each clue may have special requirements:

* **Trapped** clues must be read without `cd`-ing into their directory (use absolute paths).
* **Hidden** clues are dotfiles and require `ls -a` to see them.
* **Delayed** clues become readable only after you `cd` into their directory.

### 🏴 Flag

`pwn.college{kEDX9gVxXUjn2qN5alysNYNEwPB.QX5IDO0wCO0gjNzEzW}`

### ⚡ How I Solved

1. Read the first clue in `/`:

   ```
   cat /LEAD
   # -> Lucky listing!
   # -> The next clue is in: /usr/share/locale/kl/LC_MESSAGES
   ```
2. Read the trapped clue without `cd`:

   ```
   cat /usr/share/locale/kl/LC_MESSAGES/SPOILER-TRAPPED
   # -> Tubular find!
   # -> Next: /usr/lib/x86_64-linux-gnu/perl/5.30.0/Devel (hidden file)
   ```
3. List hidden files and read the dotfile:

   ```
   ls -a /usr/lib/x86_64-linux-gnu/perl/5.30.0/Devel
   # -> .HINT present
   cat /usr/lib/x86_64-linux-gnu/perl/5.30.0/Devel/.HINT
   # -> Lucky listing! Next: /usr/share/icons/hicolor/72x72/stock/image
   ```
4. Continue following clues and obeying hints (use `ls`, `ls -a`, `cat`, and `cd` when instructed):

   * `cat /usr/share/icons/hicolor/72x72/stock/image/NUGGET` → next: `/var/cache/man/hr` (hidden file `.REVELATION`)
   * `cat /var/cache/man/hr/.REVELATION` → next: `/opt/pwndbg/.venv/lib/python3.8/site-packages/cryptography/hazmat/bindings/__pycache__` (delayed)
   * `cd` into that directory and `cat CUE` → next: `/opt/linux/linux-5.4/arch/mips/fw/lib` (trapped)
   * `cat /opt/linux/linux-5.4/arch/mips/fw/lib/README-TRAPPED` → next: `/usr/share/doc/bash/examples`
   * `cat /usr/share/doc/bash/examples/TIP` → next: `/usr/lib/R/library/base/help` (trapped)
   * `cat /usr/lib/R/library/base/help/TEASER-TRAPPED` → reveals the flag.


```
hacker@commands~an-epic-filesystem-quest:~$ cat /LEAD
Lucky listing!
The next clue is in: /usr/share/locale/kl/LC_MESSAGES

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:~$ ls /usr/share/locale/kl/LC_MESSAGES
SPOILER-TRAPPED  iso_3166-1.mo  iso_3166.mo
hacker@commands~an-epic-filesystem-quest:~$ ls /usr/share/locale/kl/LC_MESSAGES
SPOILER-TRAPPED  iso_3166-1.mo  iso_3166.mo
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/locale/kl/LC_MESSAGES/SPOILER-TRAPPED
Tubular find!
The next clue is in: /usr/lib/x86_64-linux-gnu/perl/5.30.0/Devel

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:~$ ls -a /usr/lib/x86_64-linux-gnu/perl/5.30.0/Devel
.  ..  .HINT  PPPort.pm  Peek.pm
hacker@commands~an-epic-filesystem-quest:~$ cat //usr/lib/x86_64-linux-gnu/perl/5.30.0/Devel/.HINT
Lucky listing!
The next clue is in: /usr/share/icons/hicolor/72x72/stock/image
hacker@commands~an-epic-filesystem-quest:~$ ls -a /usr/share/icons/hicolor/72x72/stock/image
.  ..  NUGGET
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/icons/hicolor/72x72/stock/image/NUGGET
Congratulations, you found the clue!
The next clue is in: /var/cache/man/hr

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:~$ ls -a /var/cache/man/hr
.  ..  .REVELATION  CACHEDIR.TAG  cat1  index.db
hacker@commands~an-epic-filesystem-quest:~$ cat /var/cache/man/hr/.REVELATION
Tubular find!
The next clue is in: /opt/pwndbg/.venv/lib/python3.8/site-packages/cryptography/hazmat/bindings/__pycache__

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:~$ cd /opt/pwndbg/.venv/lib/python3.8/site-packages/cryptography/hazmat/bindings/__pycache__
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/cryptography/hazmat/bindings/__pycache__$ ls
CUE  __init__.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/cryptography/hazmat/bindings/__pycache__$ cat CUE
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/arch/mips/fw/lib

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/cryptography/hazmat/bindings/__pycache__$ ls /opt/linux/linux-5.4/arch/mips/fw/lib
Makefile  README-TRAPPED  call_o32.S  cmdline.c
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/cryptography/hazmat/bindings/__pycache__$ cat /opt/linux/linux-5.4/arch/mips/fw/lib/README-TRAPPED
Great sleuthing!
The next clue is in: /usr/share/doc/bash/examples
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/cryptography/hazmat/bindings/__pycache__$ ls /usr/share/doc/bash/examples
TIP  loadables
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/cryptography/hazmat/bindings/__pycache__$ cat /usr/share/doc/bash/examples/TIP
Great sleuthing!
The next clue is in: /usr/lib/R/library/base/help

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/cryptography/hazmat/bindings/__pycache__$ ls /usr/lib/R/library/base/help
AnIndex  TEASER-TRAPPED  aliases.rds  base.rdb  base.rdx  paths.rds
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/cryptography/hazmat/bindings/__pycache__$ cat /usr/lib/R/library/base/help/TEASER-TRAPPED
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{kEDX9gVxXUjn2qN5alysNYNEwPB.QX5IDO0wCO0gjNzEzW}
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/cryptography/hazmat/bindings/__pycache__$
```

### 📚 What I Learned

* Use `ls` to inspect directories and `ls -a` to reveal dotfiles.
* Use `cat /path/to/file` to read files without changing directories.
* Follow instructions in clues carefully — some require `cd`, some forbid it, and some are hidden.
* Combining these commands lets you traverse and inspect the filesystem reliably to find hidden content.

---
# 🔹 finding files

`find` walks directory trees and lists files that match criteria. By default it searches `.` (the current directory) and prints every file it finds. You can provide a location and a test, for example:

```bash
find / -name flag
find my_directory -name my_subfile
```

The filesystem is large and some directories will print "Permission denied" — ignore those; the flag won't be hidden in places you can't access.

### 🏴 Flag

`pwn.college{Mabe3DUBmp4Bd-VQ3quKbQPclpb.QXyMDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I ran `find / -name flag` to search the whole filesystem for files named `flag`.
* The command printed many candidate paths and some permission errors (expected).
* I inspected the readable candidates with `cat` until one returned the real flag.

Example interaction:

```find: ‘/tmp/tmp.TpSOPGOVKK’: Permission denied
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
/opt/linux/linux-5.4/include/linux/mfd/pcf50633/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/nix/store/7ns27apnvn4qj4q5c82x0z1lzixrz47p-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/5z3sjp9r463i3siif58hq5wj5jmy5m98-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/5n5lp1m8gilgrsriv1f2z0jdjk50ypcn-rizin-0.7.3/share/rizin/flag
/nix/store/h88mxp2mbgyj06vypwmqpy05idhwimnp-python3.13-pwntools-4.14.1/lib/python3.13/site-packages/pwnlib/flag
/nix/store/s8b49lb0pqwvw0c6kgjbxdwxcv2bp0x4-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/bnlabj2vsbljhp597ir29l51nrqhm89w-rizin-0.7.4/share/rizin/flag
/nix/store/1hyxipvwpdpcxw90l5pq1nvd6s6jdi5m-python3.12-pwntools-4.14.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/5qz6hgb1qzpvjrsw20wyiylx5zw8b9bk-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag /opt/linux/linux-5.4/include/linux/mfd/pcf50633/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/nix/store/7ns27apnvn4qj4q5c82x0z1lzixrz47p-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/5z3sjp9r463i3siif58hq5wj5jmy5m98-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/5n5lp1m8gilgrsriv1f2z0jdjk50ypcn-rizin-0.7.3/share/rizin/flag
/nix/store/h88mxp2mbgyj06vypwmqpy05idhwimnp-python3.13-pwntools-4.14.1/lib/python3.13/site-packages/pwnlib/flag
/nix/store/s8b49lb0pqwvw0c6kgjbxdwxcv2bp0x4-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/bnlabj2vsbljhp597ir29l51nrqhm89w-rizin-0.7.4/share/rizin/flag
/nix/store/1hyxipvwpdpcxw90l5pq1nvd6s6jdi5m-python3.12-pwntools-4.14.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/5qz6hgb1qzpvjrsw20wyiylx5zw8b9bk-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
pwn.college{Mabe3DUBmp4Bd-VQ3quKbQPclpb.QXyMDO0wCO0gjNzEzW}bash: /opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag: Is a directory
bash: /nix/store/7ns27apnvn4qj4q5c82x0z1lzixrz47p-radare2-5.9.8/share/radare2/5.9.8/flag: Is a directory
bash: /nix/store/5z3sjp9r463i3siif58hq5wj5jmy5m98-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag: Is a directory
bash: /nix/store/5n5lp1m8gilgrsriv1f2z0jdjk50ypcn-rizin-0.7.3/share/rizin/flag: Is a directory
bash: /nix/store/h88mxp2mbgyj06vypwmqpy05idhwimnp-python3.13-pwntools-4.14.1/lib/python3.13/site-packages/pwnlib/flag: Is a directory
bash: /nix/store/s8b49lb0pqwvw0c6kgjbxdwxcv2bp0x4-radare2-5.9.8/share/radare2/5.9.8/flag: Is a directory
bash: /nix/store/bnlabj2vsbljhp597ir29l51nrqhm89w-rizin-0.7.4/share/rizin/flag: Is a directory
bash: /nix/store/1hyxipvwpdpcxw90l5pq1nvd6s6jdi5m-python3.12-pwntools-4.14.1/lib/python3.12/site-packages/pwnlib/flag: Is a directory
bash: /nix/store/5qz6hgb1qzpvjrsw20wyiylx5zw8b9bk-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$
```

Notes:

* Some `flag` paths were directories — `cat` on those fails with "Is a directory".
* Ignore permission denied errors; they are expected when scanning system directories.

### 📚 What I Learned

* `find` is powerful for locating files by name, type, timestamp, size, and many more criteria.
* When searching the whole filesystem, expect and ignore permission-denied messages.
* Once you get candidate paths, use `cat` (or `ls -l`) to inspect which ones actually contain the flag.

---
