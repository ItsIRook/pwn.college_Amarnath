# 🔹 Printing Variables

The flag for this challenge is stored in the shell variable `FLAG`. You can print its value by referencing the variable with a leading `$` and using `echo`.

### 🏴 Flag

`pwn.college{cJiuGdRgJL2RjbTsyWZOJgHXsh4.QX3UTN0wCO0gjNzEzW}`

### ⚡ How I Solved

* I used `echo $FLAG` to print the value of the `FLAG` environment variable from the shell.

```
echo $FLAG
# -> pwn.college{cJiuGdRgJL2RjbTsyWZOJgHXsh4.QX3UTN0wCO0gjNzEzW}
```

### 📚 What I Learned

* Prefix variable names with `$` to expand their value in the shell (e.g., `$PWD`, `$HOME`, `$FLAG`).
* `echo` prints its arguments to stdout — a quick way to inspect variable contents.

---
# 🔹 Setting Variables

You can assign values to shell variables using `=` with **no spaces** around it. To reference a variable later, prepend `$` to its name (e.g., `$PWN`). Variable names and values are case-sensitive.

In this challenge you must set the `PWN` variable to the value `COLLEGE`.

### 🏴 Flag

`pwn.college{wKKe5ef8_Ti-B6-mYcZFsGIeLg3.QX5UTN0wCO0gjNzEzW}`

### ⚡ How I Solved

* I assigned the value `COLLEGE` to the variable `PWN` using a direct assignment (no spaces around `=`):

```
PWN=COLLEGE
```

* The challenge verified the assignment and revealed the flag.

```
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wKKe5ef8_Ti-B6-mYcZFsGIeLg3.QX5UTN0wCO0gjNzEzW}
```

### 📚 What I Learned

* Use `NAME=value` (no spaces) to assign shell variables.
* Access values with `$NAME` (e.g., `echo $PWN`).
* Variable names and values are case-sensitive — `PWN` ≠ `pwn`, `COLLEGE` ≠ `College`.

---
# 🔹 Multi-word Variables

Spaces separate tokens in the shell. To assign a value that contains spaces to a variable, quote the value so the shell treats it as a single token.

For example, to set `VAR` to `1337 SAUCE` you must write:

```
VAR="1337 SAUCE"
```

In this challenge you must set the `PWN` variable to the two-word value `COLLEGE YEAH`.

### 🏴 Flag

`pwn.college{wTKWr5ejXEAjzXhYQwas-Wi-6k_.QXwYTN0wCO0gjNzEzW}`

### ⚡ How I Solved

* I assigned the multi-word value using double quotes (single quotes would also work):

```
PWN="COLLEGE YEAH"
```

* The challenge verified the assignment and printed the flag.

```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
# -> pwn.college{wTKWr5ejXEAjzXhYQwas-Wi-6k_.QXwYTN0wCO0gjNzEzW}
```

### 📚 What I Learned

* Quote values containing spaces: `VAR="two words"` or `VAR='two words'`.
* Quoting preserves spaces and prevents the shell from splitting the value into separate tokens.

---
# 🔹 Exporting variables

By default, variables you set in a shell are local to that shell. Use `export` to place a variable into the environment so child processes inherit it.

In this challenge you must ensure `/challenge/run` inherits `PWN=COLLEGE` (so `PWN` is exported) while `COLLEGE` is set to `PWN` but **not exported**.

### 🏴 Flag

`pwn.college{MpbCBKxRSXUi0oRyx0O4M1Sv7sF.QXyYTN0wCO0gjNzEzW}`

### ⚡ How I Solved

* Set and export `PWN` to `COLLEGE`.
* Set `COLLEGE` to `PWN` without exporting it.
* Run `/challenge/run`, which inspects the environment and validates the configuration.

```
PWN=COLLEGE
export PWN
COLLEGE=PWN
/challenge/run
# -> CORRECT! You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN.
# -> Here is your flag: pwn.college{MpbCBKxRSXUi0oRyx0O4M1Sv7sF.QXyYTN0wCO0gjNzEzW}
```

### 📚 What I Learned

* `export NAME` (or `export NAME=value`) puts a variable into the process environment so child processes inherit it.
* Variables assigned without `export` remain local to the current shell and are not visible to children.
* Use `export` intentionally to control what data child programs receive.

---
# 🔹 Print exported variables

`env` prints the environment variables that are exported into the current shell's environment. This is a quick way to inspect what child processes will inherit.

In this challenge the `FLAG` variable is exported; use `env` to find it.

### 🏴 Flag

`pwn.college{Ui1mhAGiMT2LiMadVf9jHc6808R.QX4UTN0wCO0gjNzEzW}`

### ⚡ How I Solved

* I ran `env` and scanned the output for the `FLAG` entry.

```
env
# -> ...
# -> SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=586754561715348536838e73ca7274d7bd04e5d16a6059bc3bc148a2a06fbb68
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{Ui1mhAGiMT2LiMadVf9jHc6808R.QX4UTN0wCO0gjNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env
```

### 📚 What I Learned

* `env` lists exported environment variables (those that child processes receive).
* Not all shell variables are shown—only exported ones.
* Use `export NAME=value` to make a variable appear in `env` for child processes.

---
# 🔹 Storing Command Output

This level teaches **command substitution**: capturing the output of a command into a shell variable using `$(...)` (preferred) or backticks `` `...` `` (older form).

### 🏴 Flag

`pwn.college{0Ju3cQKJdBcrs3nfPBZ9FdMxNvH.QX1cDN1wCO0gjNzEzW}`

### ⚡ How I Solved

* I ran the `run` program and captured its output into a variable named `PWN` using command substitution.
* Then I echoed the variable to display the flag.

```
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo "$PWN"
pwn.college{0Ju3cQKJdBcrs3nfPBZ9FdMxNvH.QX1cDN1wCO0gjNzEzW}
```

### 📚 What I Learned

* `$(command)` runs `command` and substitutes its standard output where the construct appears; you can assign that to a variable: `VAR=$(cmd)`.
* Backticks (`` `...` ``) also perform command substitution but are harder to nest; prefer `$(...)`.
* Quoting the variable when printing (`echo "$PWN"`) preserves whitespace and avoids word-splitting.

---
# 🔹 Reading input

This level teaches using the `read` builtin to capture user input into a shell variable.

### 🏴 Flag

`pwn.college{AcLSDpksDSo_EgUDf3GVSZ00sJU.QX4cTN0wCO0gjNzEzW}`

### ⚡ How I Solved

* I invoked `read` to accept input from the user and stored the provided value into the `PWN` variable.
* After entering `COLLEGE` as the input, the challenge accepted it and printed the flag.

```
hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{AcLSDpksDSo_EgUDf3GVSZ00sJU.QX4cTN0wCO0gjNzEzW}
hacker@variables~reading-input:~$
```

### 📚 What I Learned

* `read VAR` reads a single line from standard input and assigns it to `VAR`.
* Use `read -p "PROMPT" VAR` to display a prompt before reading input.
* `read` is a builtin and avoids spawning an external process.

---

# 🔹 Reading files

This level teaches how to avoid the "Useless Use of `cat`" by using shell input redirection with `read` to load a file directly into a variable.

### 🏴 Flag

`pwn.college{kiI8O7F3N7qnjU_sIGGyj2vIcHK.QXwIDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I used the shell built-in `read` and redirected `/challenge/read_me` into its standard input.
* The file's first line was read into the `PWN` variable, which I then echoed.

```bash
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{kiI8O7F3N7qnjU_sIGGyj2vIcHK.QXwIDO0wCO0gjNzEzW}
hacker@variables~reading-files:~$
```

### 📚 What I Learned

* Avoid spawning `cat` when unnecessary — you can read files directly into variables: `read VAR < file`.
* `read` reads from standard input; `< filename` redirects the file into it.
* Quote variables when printing (`echo "$PWN"`) to preserve whitespace and prevent word-splitting.

---
