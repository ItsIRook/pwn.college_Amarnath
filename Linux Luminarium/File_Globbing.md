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

---
