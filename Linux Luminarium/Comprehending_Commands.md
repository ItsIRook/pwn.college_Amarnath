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
