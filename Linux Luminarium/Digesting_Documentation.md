# 🔹 Learn from Documentation

Programs often require specific command-line arguments. The challenge binary here documents that it accepts a `--giveflag` argument which causes it to print the flag.

### 🏴 Flag

`pwn.college{w0WY7XeRILK9xVFPEOcX9lHDPAD.QX0ITO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I read the provided documentation: the program expects the `--giveflag` argument.
* I invoked the program with that argument to make it print the flag.

```
/challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{w0WY7XeRILK9xVFPEOcX9lHDPAD.QX0ITO0wCO0gjNzEzW}
```

### 📚 What I Learned

* Read program documentation (or help text) to learn required arguments.
* Invoke programs with the correct flags (e.g., `--giveflag`) to trigger intended behavior.

---
# 🔹 Learning Complex Usage

Some commands accept arguments that themselves take arguments. Here, `/challenge/challenge` accepts a `--printfile` option whose *argument* is a path to the file you want printed. The documented example:

```
/challenge/challenge --printfile /challenge/DESCRIPTION.md
```

will print that file. Use the same pattern but point to `/flag` to retrieve the flag.

### 🏴 Flag

`pwn.college{EEIKtvCT1NvWRE6SZd8YNxqPub8.QX1ITO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I invoked the program with the `--printfile` option and passed `/flag` as its argument.
* The program printed the `/flag` file and revealed the flag.

```
/challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{EEIKtvCT1NvWRE6SZd8YNxqPub8.QX1ITO0wCO0gjNzEzW}
```

### 📚 What I Learned

* Some command-line options accept their own arguments; read documentation carefully to see which options do.
* The syntax `/program --option value` passes `value` as the argument to `--option`.
* This pattern appears across many Unix tools (e.g., `find -name pattern`, `tar -C dir -f archive`).

---
# 🔹 Reading Manuals

`man` displays the manual (manpage) for a command. Manpages document usage, options, and examples. To view a manpage, run:

```
man <command-name>
```

Don't pass the program's filesystem path—use its name (e.g., `man yes`). Read the SYNOPSIS and DESCRIPTION sections to discover available options.

In this challenge, `/challenge/challenge` has a secret command-line option described in its manpage that prints the flag.

### 🏴 Flag

`pwn.college{8HeiwBBC5ySkg0ehM6Jf8vNRVUh.QX0EDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I opened the manual for the program with `man /challenge/challenge` (or `man challenge` if installed in manpath).
* I read the manpage to find the secret option `--eiwykg` and its usage.
* I invoked the program with that option and the required argument to obtain the flag:

```
/challenge/challenge --eiwykg 850
# -> Correct usage! Your flag: pwn.college{8HeiwBBC5ySkg0ehM6Jf8vNRVUh.QX0EDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* Use `man <command>` to view detailed documentation and discover hidden or less-obvious options.
* The SYNOPSIS shows valid invocations; the DESCRIPTION explains option behavior.
* When a program behaves oddly, the manpage is often the fastest way to learn the intended usage.

---
# 🔹 Searching Manuals

You can search inside manpages with `/search_term` (forward) or `?search_term` (backward). After searching, press `n` to go to the next match and `N` for the previous match. Use this to quickly locate options or keywords in long manpages.

For this challenge, open the `challenge` manpage and search for the option that prints the flag.

### 🏴 Flag

`pwn.college{M64Q9Qe1Bkz6K-UG6KNXKrKFgDn.QX1EDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I opened the manual with `man challenge`.
* I searched within the manpage (for example `/flag` or part of an option) to find the secret option.
* I invoked the program with the discovered option:

```
man challenge
# (inside man) type: /<search-term>  then press Enter, use n/N to navigate
/challenge/challenge --xhbc
# -> Initializing...
# -> Correct usage! Your flag: pwn.college{M64Q9Qe1Bkz6K-UG6KNXKrKFgDn.QX1EDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* Use `/` or `?` inside `man` to search forward or backward respectively.
* `n` moves to the next search result and `N` moves to the previous one.
* Searching manpages is the fastest way to find obscure or hidden options without reading the entire document.

---
# 🔹 Searching Manuals

Some manpages are installed with randomized names. The `man` command's database can be searched with `man -k` (equivalent to `apropos`) to find entries by keyword. To learn how to search the man database, read `man man`.

In this challenge the manpage for the `challenge` program was installed under a random name. Use `man -k challenge` to locate the entry, then open that manpage and learn the secret option to run `/challenge/challenge`.

### 🏴 Flag

`pwn.college{Ip5PD8Jt4nNtJ_EG3w0BlXc9brK.QX2EDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I read the manpage for `man` to learn advanced usage (or recalled that `man -k` searches the man database).

  ```
  man man
  ```
* I searched the man database for the keyword `challenge`:

  ```
  man -k challenge
  # -> ptntwlcbrw (1) - print the flag!
  ```
* I opened the discovered manpage to learn its option (or confirm details):

  ```
  man ptntwlcbrw
  ```
* I then invoked the challenge program with the option discovered in that manpage:

  ```
  /challenge/challenge --ptntwl 584
  # -> Correct usage! Your flag: pwn.college{Ip5PD8Jt4nNtJ_EG3w0BlXc9brK.QX2EDO0wCO0gjNzEzW}
  ```

### 📚 What I Learned

* `man -k <keyword>` (or `apropos <keyword>`) searches the manpage database for entries related to a keyword.
* When manpages are installed with odd names, searching the database is the way to find them.
* After locating the manpage, use `man <entry>` to open it and learn how to invoke the associated program or option.

---
# 🔹 Helpful Programs

Many programs provide built-in usage help via `--help` (or `-h`). This prints the program's available options and how to use them. When a manpage is absent, `--help` is often the fastest way to learn required arguments.

In this challenge, `/challenge/challenge --help` reveals the options. Use `-p` (print the secret value) and then `-g` (give the flag) with that value to get the flag.

### 🏴 Flag

`pwn.college{89ZtnBLtbH5Upqb1pwqBso20CFj.QX3IDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I ran the program's help to learn its arguments:

```
/challenge/challenge --help
# shows: -p/--print-value and -g/--give-the-flag
```

* I asked the program to print the secret value:

```
/challenge/challenge -p
# -> The secret value is: 895
```

* I invoked the flag option with that value:

```
/challenge/challenge -g 895
# -> Correct usage! Your flag: pwn.college{89ZtnBLtbH5Upqb1pwqBso20CFj.QX3IDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* `--help` (or `-h`) often summarizes usage and available options.
* Use `--help` when manpages are missing or when you need a quick reminder of arguments.
* Some programs include convenience flags (like `-p`) to reveal the required input for secret options.

---
# 🔹 Help for Builtins

Some commands are **shell builtins** — the shell implements them directly instead of running external programs. Use the `help` builtin to read documentation for builtins:

```bash
help <builtin-name>
```

In this challenge, `challenge` is a shell builtin. The `help` output tells you the secret value to pass to `--secret` so the builtin will print the flag.

### 🏴 Flag

`pwn.college{sDAyFkTMfcgMHlReCMMxaGFvnJn.QX0ETO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I asked the shell for help on the `challenge` builtin:

```
help challenge
# -> shows: --secret VALUE (prints the flag if VALUE is correct)
# -> The help text reveals the secret value: "sDAyFkTM"
```

* I invoked the builtin with the revealed value:

```
challenge --secret sDAyFkTM
# -> Correct! Here is your flag!
# -> pwn.college{sDAyFkTMfcgMHlReCMMxaGFvnJn.QX0ETO0wCO0gjNzEzW}
```

### 📚 What I Learned

* `help <builtin>` displays usage for shell builtins (different from `man` and `--help`).
* Builtins are documented via `help` and can require specific arguments just like external programs.
* Always check `help` when a command seems to be implemented by the shell.

---

