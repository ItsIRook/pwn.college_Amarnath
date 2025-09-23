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
