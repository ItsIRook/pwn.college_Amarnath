# 🔹 Redirect output

Use the `>` operator to redirect a command's standard output into a file. If the file doesn't exist, it's created; if it does, it's overwritten.

Example:

```
echo hi > asdf
cat asdf
# -> hi
```

In this challenge the task was to write the exact text `PWN` (uppercase) into a file named `COLLEGE` (uppercase) using output redirection.

### 🏴 Flag

`pwn.college{ECB9NSTOMD0v8G3j73aEz0KI0Xc.QX0YTN0wCO0gjNzEzW}`

### ⚡ How I Solved

* I redirected the output of `echo` into the file `COLLEGE` using `>`:

```
echo PWN > COLLEGE
```

* The challenge checker verified the file contents and printed the flag.

```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{ECB9NSTOMD0v8G3j73aEz0KI0Xc.QX0YTN0wCO0gjNzEzW}
```

### 📚 What I Learned

* `>` redirects stdout to a file, creating or truncating the file.
* Use `>>` to append instead of overwrite.

---
# 🔹 Redirecting more output

Some programs print human-readable progress and diagnostics to **standard error** while sending their primary output to **standard output**. Redirecting only standard output with `>` lets you capture the program's real output while still seeing its diagnostics on your terminal.

In this level you must redirect the stdout of `/challenge/run` into a file named `myflag`. The program prints informational messages to stderr (which still appear on the terminal), and writes the flag to stdout — which will end up in the `myflag` file.

### 🏴 Flag

`pwn.college{QdHPDcZ0NgpVU3X_WNyeY_Cn-BZ.QX1YTN0wCO0gjNzEzW}`

### ⚡ How I Solved

* I redirected stdout to `myflag` when running the program:

```
/challenge/run > myflag
# program prints INFO and HYPE messages to stderr (they remain on the terminal)
```

* I then inspected the `myflag` file to read the flag:

```
cat myflag
# -> [FLAG] pwn.college{QdHPDcZ0NgpVU3X_WNyeY_Cn-BZ.QX1YTN0wCO0gjNzEzW}
```

### 📚 What I Learned

* `>` redirects **stdout** to a file; stderr still goes to the terminal by default.
* To redirect stderr as well, use `2> file` (or `&> file` to redirect both in some shells).
* Many programs separate human-facing diagnostics (stderr) from machine-readable output (stdout); capture the latter when you need it.

---
# 🔹 Appending output

Redirecting with `>` truncates (overwrites) the destination file. Use `>>` to append instead so multiple writes accumulate in the same file.

This challenge writes the flag in two parts: the program writes the first half directly to the file, then writes the second half to **stdout**. If stdout is redirected into the same file in **append** mode (`>>`), the second half is appended and you get the full flag. If you use truncation mode (`>`), the second write will overwrite the first and you'll only see the second half.

### 🏴 Flag

`pwn.college{05DTTUS2i0DiUVSNSAVlJLAPl27.QX3ATO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I redirected stdout of `/challenge/run` into `/home/hacker/the-flag` in append mode:

```bash
/challenge/run >> /home/hacker/the-flag
```

* The program performed its checks, wrote the first half directly to the file, and then wrote the second half to stdout which was appended to the file.
* I inspected the file to read the full flag:

```bash
cat /home/hacker/the-flag
# -> pwn.college{05DTTUS2i0DiUVSNSAVlJLAPl27.QX3ATO0wCO0gjNzEzW}
```

### 📚 What I Learned

* `>` truncates (overwrites) the destination file; `>>` appends.
* Some programs write to files and to stdout separately; when capturing stdout into a file, choose the correct redirection mode to avoid accidental overwrites.
* File descriptors and how a program opens/writes files can affect behavior — append when you need to preserve previous contents.

---
# 🔹 Redirecting errors

You can redirect by file descriptor number. `>` alone implies `1>` (stdout). Use `2>` to redirect stderr. Combine them to send stdout and stderr to different files.

This challenge requires sending stdout to `myflag` and stderr to `instructions` so nothing prints to the terminal.

### 🏴 Flag

`pwn.college{0ZEAB95IeChgLKT5Jr33sGe4dCc.QX3YTN0wCO0gjNzEzW}`

### ⚡ How I Solved

* I ran the program redirecting stdout to `myflag` and stderr to `instructions`:

```
/challenge/run > myflag 2> instructions
```

* I inspected the files to read the results:

```
cat instructions   # shows the program's INFO/HYPE/instructions written to stderr
cat myflag         # contains the flag written to stdout
```

### 📚 What I Learned

* FD `1` is stdout, FD `2` is stderr; redirect with `1>` and `2>` (or `>` and `2>` respectively).
* You can redirect multiple FDs in one command: `/cmd > out 2> err`.
* Programs often separate human-facing messages (stderr) from machine output (stdout); capture them separately when needed.

---
# 🔹 Redirecting input

Use `<` to redirect a file into a program's standard input (FD 0). This lets programs read from a file as if the contents were typed at the terminal.

In this level, you must write the string `COLLEGE` into a file named `PWN`, then run `/challenge/run` with that file redirected to its stdin.

### 🏴 Flag

`pwn.college{IFf_nW0jx00-i09Mf1Zw8Vmw_zy.QXwcTN0wCO0gjNzEzW}`

### ⚡ How I Solved

* I created the `PWN` file containing `COLLEGE` using output redirection.
* I ran `/challenge/run` with input redirected from `PWN` using `<`.

```
echo COLLEGE > PWN
/challenge/run < PWN
# -> Reading from standard input...
# -> Correct! You have redirected the PWN file into my standard input, and I read the value 'COLLEGE' out of it!
# -> Here is your flag:
# -> pwn.college{IFf_nW0jx00-i09Mf1Zw8Vmw_zy.QXwcTN0wCO0gjNzEzW}
```

### 📚 What I Learned

* `< filename` redirects the file into a program's stdin.
* Combine redirections: use `>` or `>>` to prepare files, and `<` to feed them into commands.

---
# 🔹 Grepping stored results

You can redirect a program's stdout into a file and then search that file with `grep`. This is useful when a program produces a lot of output and you want to search the results later.

In this challenge, `/challenge/run` writes 100,000 lines to stdout when redirected; one of those lines contains the flag. Save the output to `/tmp/data.txt`, then `grep` for the flag.

### 🏴 Flag

`pwn.college{8jY5qxQce_tSjX7zjKbkKMz74yx.QX4EDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I redirected the program's stdout into `/tmp/data.txt`:

```
/challenge/run > /tmp/data.txt
```

* Then I searched the resulting file for the flag prefix using `grep`:

```
grep pwn /tmp/data.txt
# -> pwn
# -> pwn.college{8jY5qxQce_tSjX7zjKbkKMz74yx.QX4EDO0wCO0gjNzEzW}
# -> pwns
# -> pwning
# -> pwned
```

The `grep` output included the flag line among other matching words.

### 📚 What I Learned

* Use `>` to capture program output into a file for later analysis.
* Use `grep <pattern> <file>` to find lines containing the pattern in a large file.
* Expect some noise (other matches); search for distinctive prefixes like `pwn.college` to pinpoint flags.

---
# 🔹 Grepping errors

The pipe `|` sends **stdout** of the left command into **stdin** of the right command. To search through **stderr**, first redirect stderr (FD 2) into stdout (FD 1) using `2>&1`, then pipe as usual.

Run the challenge with combined output piped into `grep` to find the flag.

### 🏴 Flag

`pwn.college{YNecvTkmBMczlejiTCAtSVeEEWP.QX1ATO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I redirected stderr into stdout and piped to `grep`:

```
/challenge/run 2>&1 | grep pwn
```

* The program checked that the process on the other end was `grep` (it inspects the receiving process) and then `grep` printed matching lines including the flag.

```
# sample output (truncated):
pwning
pwns
pwned
pwn
pwn.college{YNecvTkmBMczlejiTCAtSVeEEWP.QX1ATO0wCO0gjNzEzW}
```

### 📚 What I Learned

* `2>&1` makes stderr flow into stdout so a pipe can carry both streams.
* Order matters: `2>&1 | grep ...` redirects stderr to the same target as stdout (the pipe).
* Some programs may inspect the receiving process; piping to the expected executable (here `grep`) can be required.

---
