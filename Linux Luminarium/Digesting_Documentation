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

