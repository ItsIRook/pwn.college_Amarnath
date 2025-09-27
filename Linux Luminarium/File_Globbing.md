# 🔹 Matching wiht *

The shell expands `*` as a wildcard that matches zero or more characters (except `/` and a leading `.`). Use it to shorten typing or match patterns. In this challenge you must `cd` into `/challenge` from your home directory while keeping the argument to `cd` at most four characters long by using a glob.

### 🏴 Flag

`pwn.college{QCk5P6YpOLw6PVfmKHJZew2Wma-.QXxIDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* From my home directory I used a glob that matched `/challenge` but was no longer than four characters: `cd /ch*`.
* The shell expanded `/ch*` to `/challenge`, changing the working directory.
* I ran `/challenge/run`, which detected the working directory and printed the flag.

```
# from home directory
cd /ch*
# shell expands /ch* -> /challenge
/challenge/run
# -> You ran me with the working directory of /challenge! Here is your flag:
# -> pwn.college{QCk5P6YpOLw6PVfmKHJZew2Wma-.QXxIDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* `*` matches any string of characters (except `/` and a leading `.`).
* Globbing happens **before** the command runs: the shell expands the pattern into matching filenames/paths.
* Use globs to write shorter, flexible commands when filenames share common prefixes.

---
# 🔹 Matching with ?

The `?` wildcard matches exactly one character in a filename or path. It's like `*`, but limited to a single character per `?`.

In this challenge you must `cd` into `/challenge` from your home directory using `?` wildcards instead of the letters `c` and `l` in the path, then run `/challenge/run` for the flag.

### 🏴 Flag

`pwn.college{ch_F-VKWpdn8V-XgLBA1YALVJgT.QXyIDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I used a pattern where each `?` stands for a single character in the path component:

```bash
cd /?ha??enge
# shell expands /?ha??enge -> /challenge
/challenge/run
# -> You ran me with the working directory of /challenge! Here is your flag:
# -> pwn.college{ch_F-VKWpdn8V-XgLBA1YALVJgT.QXyIDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* `?` matches exactly one character (not `/` and not a leading `.`).
* Multiple `?` characters sequence to match multiple single characters.
* Globbing is performed by the shell **before** the command runs, expanding patterns into matching filenames or paths.

---
# 🔹 Matching with []

Square-bracket globs match exactly one character from a specified set. For example, `file_[ab]` matches `file_a` or `file_b` but not `file_c`.

In this challenge there are files in `/challenge/files`. Change into that directory and run `/challenge/run` with a single bracket-glob argument that matches `file_b`, `file_a`, `file_s`, and `file_h`.

### 🏴 Flag

`pwn.college{wQ1zas82ArgnJ6ZF4ORA1BpA0d8.QXzIDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I changed into the target directory:

```
cd /challenge/files
```

* I invoked the challenge with a bracket glob that matches the required files (`b`, `a`, `s`, `h`):

```
/challenge/run file_[bash]
# -> You got it! Here is your flag:
# -> pwn.college{wQ1zas82ArgnJ6ZF4ORA1BpA0d8.QXzIDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* `[]` matches exactly one character from the set inside the brackets (e.g., `[abc]` matches `a`, `b`, or `c`).
* Use bracket globs when you want to match a small list of possible characters at a particular position.
* Globbing is expanded by the shell before the command runs, so `/challenge/run file_[bash]` expands to multiple arguments (one per matched filename).

---
# 🔹 Matching paths with []

Globs operate per-path-component, so you can use them in absolute paths as well as relative paths. The pattern `/challenge/files/file_[bash]` expands to the matching filenames with full paths.

In this challenge, run `/challenge/run` from your home directory and pass a single argument that bracket-globs into the absolute paths for `file_b`, `file_a`, `file_s`, and `file_h` located under `/challenge/files`.

### 🏴 Flag

`pwn.college{EpQhavqfNM_0RLj_jbhZaee_nlB.QX0IDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* From my home directory I invoked the challenge with a single bracket-glob argument that expands to the absolute paths of the required files:

```
/challenge/run /challenge/files/file_[bash]
# -> You got it! Here is your flag:
# -> pwn.college{EpQhavqfNM_0RLj_jbhZaee_nlB.QX0IDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* Globbing is applied to each path component, so `/path/prefix*` expands to absolute paths when used that way.
* Bracket globs (`[abc]`) match exactly one character from the set and can be used in absolute paths just like relative ones.
* The shell expands globs before executing the command, so the program receives the expanded absolute paths as arguments.

---
# 🔹 Multiple globs

Bash expands `*` as a wildcard that matches any sequence of characters (except `/` and a leading `.`). You can use multiple `*` glob tokens in a single word; the shell will expand the pattern to any filenames that fit.

In this challenge you must `cd` to `/challenge/files` and run `/challenge/run` with a single short (≤3 characters) globbed word containing two `*` tokens that matches every filename that contains the letter `p`.

### 🏴 Flag

`pwn.college{0jIj3lbxPSUNLQ-Rm1Ye_dytEWf.0lM3kjNxwCO0gjNzEzW}`

### ⚡ How I Solved

* I changed into the target directory:

```
cd /challenge/files
```

* I ran `/challenge/run` with a short glob containing two `*` tokens that matches any filename containing `p`:

```
/challenge/run *p*
# -> You got it! Here is your flag:
# -> pwn.college{0jIj3lbxPSUNLQ-Rm1Ye_dytEWf.0lM3kjNxwCO0gjNzEzW}
```

### 📚 What I Learned

* Multiple `*` tokens in one word are allowed and together match any string that satisfies the combined pattern.
* A pattern like `*p*` matches every filename that contains `p` anywhere in its name.
* Globbing expansion happens before the command runs, so `/challenge/run *p*` receives the expanded list of matching filenames as a single or multiple arguments depending on matches.

---

# 🔹 Mixing globs

Use the globbing patterns you've learned (`[]`, `*`, `?`) to construct a single short pattern that matches several different filenames. In this challenge you must match the files `challenging`, `educational`, and `pwning` with one glob of **6 characters or less**, then pass it as an argument to `/challenge/run` from `/challenge/files`.

### 🏴 Flag

`pwn.college{YIx3I2oQQg14WdvV4bqxKfEvkrw.QX1IDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I changed into the target directory:

```
cd /challenge/files
```

* I invoked the challenge with a single short glob that matches all three target filenames. The pattern uses a character-class to match the initial letter of each word followed by `*` to match the rest:

```
/challenge/run [cep]*
# -> You got it! Here is your flag:
# -> pwn.college{YIx3I2oQQg14WdvV4bqxKfEvkrw.QX1IDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* A bracket glob like `[cep]` matches exactly one character from the set `c`, `e`, or `p`.
* Appending `*` allows the rest of the filename to be arbitrary, so `[cep]*` matches `challenging`, `educational`, and `pwning`.
* Keep globs short and deliberate to meet constraints while still matching required targets.

---# 🔹 Exclusionary Globbing with

Bracket globs can be inverted by placing `!` (or `^` in some shells) as the first character inside the brackets. This matches any single character *not* in the set. Use this to exclude certain leading characters from matches.

In this challenge you must `cd` into `/challenge/files` and run `/challenge/run` with a single glob argument that matches **all files that do not start with `p`, `w`, or `n`**.

### 🏴 Flag

`pwn.college{0mMhkD7grGcyImZnNRWhwzNs4bt.QX2IDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I changed to the target directory:

```
cd /challenge/files
```

* I used an inverted bracket glob that excludes the characters `p`, `w`, and `n`, then allowed the rest of the filename with `*`:

```
/challenge/run [!pwn]*
# -> You got it! Here is your flag:
# -> pwn.college{0mMhkD7grGcyImZnNRWhwzNs4bt.QX2IDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* `[!abc]` matches any single character except `a`, `b`, or `c` (similarly, `[^abc]` if supported).
* Place `!` (or `^`) as the first character inside `[]` to invert the character class.
* Be careful: `!` has other shell meanings outside `[]`, so invert only inside the bracket and as the first character.

---
# 🔹 Tab completion

Globs are powerful but sometimes dangerous. Tab completion is a safer way to let the shell expand a partial word for you. Hitting `Tab` completes filenames (or shows options) so you don't accidentally type the wrong thing.

In this challenge the file visible under `ls /challenge` is named `pwncollege`, but the real file you must read is only accessible by using tab completion after typing the prefix.

### 🏴 Flag

`pwn.college{gaItXoWAsp_Re_YB2ik2NbXhTas.0FN0EzNxwCO0gjNzEzW}`

### ⚡ How I Solved

* I listed `/challenge` to confirm the visible entry:

```bash
ls /challenge
# -> DESCRIPTION.md  pwncollege
```

* Typing the partial path and hitting Tab completed the hidden/obscured filename and allowed me to cat the file:

```bash
cat /challenge/pwn<TAB>
# -> pwn.college{gaItXoWAsp_Re_YB2ik2NbXhTas.0FN0EzNxwCO0gjNzEzW}
```

> Note: `<TAB>` denotes pressing the Tab key; the shell performs the completion for you.

### 📚 What I Learned

* Pressing `Tab` asks the shell to complete the current word using filesystem entries (or command names).
* Tab-completion reduces typing and prevents accidental glob expansions that might target unintended files.
* When a filename is hard to type or contains hidden characters, Tab is the reliable way to enter it correctly.

---
# 🔹 Multiple options for tab completion

When you press Tab and multiple filesystem entries match the current prefix, shells behave differently:

* **bash (default)**: completes up to the longest common prefix (e.g., `fl`) and on a second Tab lists all possibilities.
* **some shells** (or configured bash): cycle through matches each Tab press.

This challenge places many files that begin with `pwncollege` under `/challenge/files`. Use tab-completion (or a shell that cycles completions, like fish) starting from `/challenge/files/p` (or similar) to reach the full filename for the flag.

### 🏴 Flag

`pwn.college{A8yzO4G-6UosVqHuBmBCeG1CGZa.0lN0EzNxwCO0gjNzEzW}`

### ⚡ How I Solved

* I started tab-completion (in fish cause bash doesn't cycle throught files) from the given prefix until the shell completed the desired filename (or switched to a shell that cycles matches).
* I then `cat`-ed the completed path to read the flag.

Example interaction (using fish to cycle completions):

```
fish
# -> Welcome to fish, the friendly interactive shell
# -> Type `help` for instructions on how to use fish
cat /challenge/files/pwncollege-flag
# -> pwn.college{A8yzO4G-6UosVqHuBmBCeG1CGZa.0lN0EzNxwCO0gjNzEzW}
```

### 📚 What I Learned

* Tab completion behavior depends on shell and configuration.
* If first Tab shows a common prefix, press Tab again to list options in bash.
* Some shells cycle completions which can be more convenient for picking a single file interactively.

---
# 🔹 Tab completion on commands

Tab completion can complete command names as well as filenames. The shell will attempt to expand the word you're typing into a known executable or function when you press the Tab key. This is handy for long command names or when you don't quite remember the exact suffix.

In this level a command whose name starts with `pwncollege` exists. Type the prefix and press Tab to complete it, then run it to get the flag.

### 🏴 Flag

`pwn.college{0nqYgx2bm0HUfhfK6413KnDo2TM.0VN0EzNxwCO0gjNzEzW}`

### ⚡ How I Solved

* I entered a shell with friendly tab-completion behavior (fish was used here for convenience).
* I typed the `pwncollege` prefix and pressed Tab to complete the command name.
* I executed the completed command which printed the flag.

```
fish
# -> Welcome to fish, the friendly interactive shell
# -> Type `help` for instructions on how to use fish
pwncollege-25001
# -> Correct! Here is your flag:
# -> pwn.college{0nqYgx2bm0HUfhfK6413KnDo
```

