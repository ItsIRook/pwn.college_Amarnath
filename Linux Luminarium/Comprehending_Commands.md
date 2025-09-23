# 🔹 cat: not the pet, but the command

`cat` is one of the most fundamental Linux utilities. It prints file contents to standard output and can concatenate multiple files when passed more than one argument. When given no arguments, it reads from standard input.

In this challenge, the flag was copied to a file named `flag` in the home directory. The task: read that file with `cat`.

### 🏴 Flag

`pwn.college{MDdBa9tmJuiQTWvV1DiOpJV-gj6.QXxcTN0wCO0gjNzEzW}`

### ⚡ How I Solved

* I ensured I was in my home directory (the shell start location).
* I used `cat flag` to print the contents of the `flag` file.
* The command displayed the flag.

```bash
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
