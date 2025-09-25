# 🔹 cat: not the pet, but the command

`cat` is one of the most fundamental Linux utilities. It prints file contents to standard output and can concatenate multiple files when passed more than one argument. When given no arguments, it reads from standard input.

In this challenge, the flag was copied to a file named `flag` in the home directory. The task: read that file with `cat`.

### 🏴 Flag

`pwn.college{MDdBa9tmJuiQTWvV1DiOpJV-gj6.QXxcTN0wCO0gjNzEzW}`

### ⚡ How I Solved

* I ensured I was in my home directory (the shell start location).
* I used `cat flag` to print the contents of the `flag` file.
* The command displayed the flag.

```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{MDdBa9tmJuiQTWvV1DiOpJV-gj6.QXxcTN0wCO0gjNzEzW}
hacker@commands~cat-not-the-pet-but-the-command:~$
```

### 📚 What I Learned

* `cat <filename>` prints the file's content to the terminal.
* `cat file1 file2` concatenates and prints both files in order.
* `cat` with no arguments reads from standard input until EOF, echoing what you type.
* `cat` is simple but powerful for quick file inspection and combining files.

---
# 🔹 catting absolute paths

In the previous level you used `cat flag` to read a file in your home directory. You can also provide absolute paths to `cat` so it reads files anywhere the current user has permission to read. In this challenge the flag is left readable at the absolute path `/flag`.

### 🏴 Flag

`pwn.college{EhIIavrq6dfGVTVhBHwNMINRmkg.QX5ETO0wCO0gjNzEzW}`

### ⚡ How I Solved

* From any directory, I ran `cat /flag` to print the file at its absolute path.
* The command displayed the flag.

```bash
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{EhIIavrq6dfGVTVhBHwNMINRmkg.QX5ETO0wCO0gjNzEzW}
hacker@commands~catting-absolute-paths:~$
```

### 📚 What I Learned

* `cat /path/to/file` reads the file at that absolute path.
* Absolute paths start with `/` and refer to the filesystem root.
* Whether you can read a file depends on permissions; `cat` will fail if you lack read access.

---
# 🔹 more catting practice

In this level you may *not* change directories with `cd`. The flag is placed in an unusual location and you must read it by providing its absolute path to `cat`.

### 🏴 Flag

`pwn.college{MsljiH5RiAahHr19mxa4Quw0dI_.QXwITO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I could not `cd` into the directory, so I used the absolute path of the flag file with `cat`.
* I ran `cat /usr/include/givaro/flag` and the flag was printed.

```
hacker@commands~more-catting-practice:~$ cat /usr/include/givaro/flag
pwn.college{MsljiH5RiAahHr19mxa4Quw0dI_.QXwITO0wCO0gjNzEzW}
hacker@commands~more-catting-practice:~$
```

### 📚 What I Learned

* If you cannot change directories, use an absolute path with `cat` to access files elsewhere.
* Absolute paths begin with `/` and specify the full location from the filesystem root.
* File readability depends on permissions; `cat` will fail if you lack read access.

---
# 🔹 grepping for a needle in a haystack

When files are huge, you don't want to `cat` the entire thing. `grep` searches files for matching lines and prints only those lines. The basic usage is:

```
grep SEARCH_STRING /path/to/file
```

In this challenge the file `/challenge/data.txt` contains 100,000 lines; the flag is hidden somewhere inside. The hint: flags start with `pwn.college`.

### 🏴 Flag

`pwn.college{8mac-__MdcOqhrDwe_B5O9ZzHpf.QX3EDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I used `grep pwn.college /challenge/data.txt` to search the file for the flag prefix.
* `grep` printed the matching line which contained the flag.

```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{8mac-__MdcOqhrDwe_B5O9ZzHpf.QX3EDO0wCO0gjNzEzW}
hacker@commands~grepping-for-a-needle-in-a-haystack:~$
```

### 📚 What I Learned

* `grep <pattern> <file>` finds and prints lines matching `<pattern>`.
* Use `grep` when you need to search large files without viewing them entirely.
* `grep` supports regexes and many options (case-insensitive, line numbers, whole-word matching) which are useful for advanced searches.

---
# 🔹 comparing files

`diff` compares two files line-by-line and shows the differences. It's perfect for spotting a single extra (or changed) line among many similar lines.

In this challenge there are two files in `/challenge`:

* `/challenge/decoys_only.txt` — contains 100 fake flags
* `/challenge/decoys_and_real.txt` — contains the same 100 fake flags **plus** the one real flag

Run `diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt` to see which line was added.

### 🏴 Flag

`pwn.college{wjMjs-XtS9pJ9WUeEptux1IMhxd.01MwMDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* I compared the two files with `diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt`.
* `diff` showed a single added line in the second file, which contained the real flag.

```
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
57a58
> pwn.college{wjMjs-XtS9pJ9WUeEptux1IMhxd.01MwMDOxwCO0gjNzEzW}
hacker@commands~comparing-files:~$
```

### 📚 What I Learned

* `diff fileA fileB` tells you which lines were added, removed, or changed between two files.
* An `a` (e.g., `57a58`) means lines were added to the second file after line 57 of the first file.
* Use `diff` when you need to find differences quickly without manually inspecting large files.

---
# 🔹 listing files

`ls` lists directory contents. If you don't know a filename, list the directory and inspect the results.

In this challenge, the `run` program was renamed and placed in `/challenge`. Use `ls /challenge` to find it, then execute it by absolute path.

### 🏴 Flag

`pwn.college{4trZmqFCgASGqK6x5eMG0gCCaA-.QX4IDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I listed the `/challenge` directory to find the renamed `run` file.
* I executed the found filename with its absolute path to reveal the flag.

```
hacker@commands~listing-files:~$ ls /challenge
12235-renamed-run-23669  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/12235-renamed-run-23669
Yahaha, you found me! Here is your flag:
pwn.college{4trZmqFCgASGqK6x5eMG0gCCaA-.QX4IDO0wCO0gjNzEzW}
hacker@commands~listing-files:~$
```

### 📚 What I Learned

* `ls` shows files and directories in the given path or the current directory if none is provided.
* When executables are renamed, listing the directory reveals their names so you can run them.
* Execute discovered binaries by their path (absolute or relative) to run them.

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
# 🔹 making directories

Create directories with `mkdir` and files with `touch`. Then place files inside and verify with `ls`.

This challenge asks you to create `/tmp/pwn` and a file `/tmp/pwn/college`, then run `/challenge/run` to confirm and receive the flag.

### 🏴 Flag

`pwn.college{QOkmggG6WPVaIHh38LWyGQF4YNJ.QXxMDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I created the directory `/tmp/pwn` with `mkdir /tmp/pwn`.
* I created the file `/tmp/pwn/college` with `touch /tmp/pwn/college`.
* I ran `/challenge/run`, which checked the presence of the directory and file and printed the flag.

```
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{QOkmggG6WPVaIHh38LWyGQF4YNJ.QXxMDO0wCO0gjNzEzW}
hacker@commands~making-directories:~$
```

### 📚 What I Learned

* `mkdir <directory>` creates a directory; use `-p` to create parent directories as needed.
* `touch <file>` creates an empty file (or updates its timestamp).
* Use `ls` to verify files and directories before running checks.

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


```
find / -name flag
find: ‘/tmp/tmp.TpSOPGOVKK’: Permission denied
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
# 🔹 linking files

A symbolic link points to another file by name. Use `ln -s <target> <link>` to create one. Accessing the symlink follows the path to the target and returns the target's contents.

In this challenge `/challenge/catflag` prints `/home/hacker/not-the-flag`. Create a symlink named `/home/hacker/not-the-flag` that points to `/flag` and `catflag` will print the real flag.

### 🏴 Flag

`pwn.college{IEMXzKe5hLOydFFY9NjSYpDbSIM.QX5ETN1wCO0gjNzEzW}`

### ⚡ How I Solved

* I created a symbolic link pointing `/home/hacker/not-the-flag` at `/flag`.
* I ran `/challenge/catflag`, which followed the symlink and printed the flag.

```
ln -s /flag /home/hacker/not-the-flag
/challenge/catflag
# -> About to read out the /home/hacker/not-the-flag file!
# -> pwn.college{IEMXzKe5hLOydFFY9NjSYpDbSIM.QX5ETN1wCO0gjNzEzW}
```

### 📚 What I Learned

* `ln -s <target> <link>` creates a symlink named `<link>` that points to `<target>`.
* Programs opening the symlink usually follow it transparently and access the target's contents.
* Use `file <name>` or `ls -l` to identify symlinks.

---
