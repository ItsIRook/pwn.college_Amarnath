# 🔹 Translating Characters

This level gives you a flag whose letter case has been swapped. Use `tr` to reverse the case and reveal the flag.

### 🏴 Flag

`pwn.college{IGYywyijQHvNGFCmcSI41XYFbXn.01MxEzNxwCO0gjNzEzW}`

### ⚡ How I Solved

* I piped the challenge output into `tr` and swapped upper and lower classes.

```
hacker@data~translating-characters:~$ /challenge/run | tr '[:upper:][:lower:]' '[:lower:][:upper:]'
yOUR CASE-SWAPPED FLAG:
pwn.college{IGYywyijQHvNGFCmcSI41XYFbXn.01MxEzNxwCO0gjNzEzW}
```

### 📚 What I Learned

* `tr` translates or deletes characters from standard input.
* Character classes like `[:upper:]` and `[:lower:]` let you operate on ranges (e.g., swap case) without listing each character.

---
# 🔹 Deleting Characters

This level adds decoy characters (`^` and `%`) into the flag. Use `tr -d` to delete those characters from the challenge output and reveal the flag.

### 🏴 Flag

`pwn.college{UZV39ePDvoeiiPuPLUG2vAM3jZy.0FNxEzNxwCO0gjNzEzW}`

### ⚡ How I Solved

* I piped the challenge output into `tr -d` and removed the `^` and `%` characters.

```
hacker@data~deleting-characters:~$ /challenge/run | tr -d ^%
Your character-stuffed flag:
pwn.college{UZV39ePDvoeiiPuPLUG2vAM3jZy.0FNxEzNxwCO0gjNzEzW}
```

### 📚 What I Learned

* `tr -d <chars>` deletes all occurrences of `<chars>` from standard input.
* Use `tr -d` to quickly strip unwanted characters from a stream.

---
# 🔹 Deleting Newlines

This level injects extra newline characters into the flag. Use `tr -d '\n'` to remove them and produce a single-line flag.

### 🏴 Flag

`pwn.college{sxKPnJIXoFEiE99bM7c3QuiKyp0.0VNxEzNxwCO0gjNzEzW}`

### ⚡ How I Solved

* I piped the challenge output into `tr -d '\n'` to delete all newline characters from the stream.
* The result printed the flag on a single line.

```
hacker@data~deleting-newlines:~$ /challenge/run | tr -d '\n'
Your line-split flag: pwn.college{sxKPnJIXoFEiE99bM7c3QuiKyp0.0VNxEzNxwCO0gjNzEzW}
```

### 📚 What I Learned

* `\n` represents a newline when passed as a quoted argument to `tr`.
* `tr -d '\n'` removes all newline characters from standard input, turning multiline streams into a single line.
* Escape sequences sometimes require quoting to prevent the shell from interpreting them before `tr` receives them.

---
# 🔹 Extracting First Lines with head

This challenge requires you to take the first 7 lines of a verbose program and pipe them into another program to get the flag.

### 🏴 Flag

`pwn.college{Q7wXU-hUVkf3qGv6yBhbkGIXNoC.0lNxEzNxwCO0gjNzEzW}`

### ⚡ How I Solved

* I ran `/challenge/pwn`, piped its output to `head -n 7` to capture the first seven lines, and then piped that into `/challenge/college`.

```
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{Q7wXU-hUVkf3qGv6yBhbkGIXNoC.0lNxEzNxwCO0gjNzEzW}
```

### 📚 What I Learned

* `head -n N` prints the first N lines of its input.
* Use multiple pipes to chain commands: `producer | filter | consumer`.

---
# 🔹 Extracting Specific Sections of text

This level provides lines where the flag characters are in a specific column. Use `cut` with an appropriate delimiter and field number to extract the flag characters, then remove newlines with `tr -d '\n'` to form the single-line flag.

### 🏴 Flag

`pwn.college{w9dnw2b7WljN49G3-BD-U2fd8AG.01NxEzNxwCO0gjNzEzW}`

### ⚡ How I Solved

* I piped the challenge output into `cut`, using a space (`" "`) as the delimiter and selecting field 2.
* I then piped that into `tr -d '\n'` to join the characters into one line.

```
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d '\n'
pwn.college{w9dnw2b7WljN49G3-BD-U2fd8AG.01NxEzNxwCO0gjNzEzW}
```

### 📚 What I Learned

* `cut -d "DELIM" -f N` extracts the Nth field using DELIM as the separator.
* Chain `cut` with `tr -d '\n'` to convert vertical column output into a single-line string.

---
# 🔹 Sorting Data

This level gives you `/challenge/flags.txt` containing 100 fake flags and the real flag mixed among them. When sorted alphabetically, the real flag was placed at the end—so sorting reveals it.

### 🏴 Flag

`pwn.college{4Y67pD9O_kuFDSvGQi_domH7nSu.0FM0MDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* I sorted the file in reverse alphabetical order so the true flag (placed at the end when sorted normally) appears first.

```bash
hacker@data~sorting-data:~$ sort /challenge/flags.txt -r
pwn.college{4Y67pD9O_kuFDSvGQi_domH7nSu.0FM0MDOxwCO0gjNzEzW}
... (other lines omitted) ...
```

### 📚 What I Learned

* `sort` orders lines alphabetically by default.
* `-r` reverses the order; `-n` for numeric sort; `-u` removes duplicates.
* When fake items are generated, a predictable sort key can hide the true item at a known position—sorting exposes it.

---
