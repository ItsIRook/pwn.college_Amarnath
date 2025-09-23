# 🔹 Home Sweet Home, From ~

In this challenge you must provide an argument (three characters or less before expansion) that expands to an absolute path inside your home directory. Bash expands a leading `~` to your home directory (`/home/hacker`), so `~/a` becomes `/home/hacker/a` and satisfies the constraints.

### 🏴 Flag
`pwn.college{UerExeWBXmW8YUOK3GcA_dgs_lY.QXzMDO0wCO0gjNzEzW}`

### ⚡ How I Solved
- I ran the program with an argument that uses `~` as shorthand and is three characters before expansion: `/challenge/run ~/a`.
- `/challenge/run` wrote the flag to `/home/hacker/a` and printed the flag.

    hacker@paths~home-sweet-home:~$ /challenge/run ~/a
    Writing the file to /home/hacker/a!
    ... and reading it back to you:
    pwn.college{UerExeWBXmW8YUOK3GcA_dgs_lY.QXzMDO0wCO0gjNzEzW}
    hacker@paths~home-sweet-home:~$

### 📚 What I Learned
- `~` expands to the user’s home directory (`/home/hacker`) only when it appears at the start of a path.
- `~` expansion happens before the program sees the argument, so passing `~/a` satisfies an "absolute path" requirement after expansion.
- `cd` with no arguments returns you to your home directory; `~` is a convenient shorthand for home.

---

*Executed using a three-character pre-expansion argument (`~/a`) which expands to an absolute path inside the home directory.*
