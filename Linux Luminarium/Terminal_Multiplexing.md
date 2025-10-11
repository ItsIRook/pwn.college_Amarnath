# 🔹 Launching screen

This level introduces `screen`, a terminal multiplexer that creates virtual terminals inside your terminal. Starting `screen` opens a session you can interact with like a normal shell.

### 🏴 Flag

`pwn.college{QEC3vFB6adTcS4e4StB1LYeDANY.0VN4IDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* I launched `screen` by running the command `screen`.
* The challenge is configured to reveal the flag upon entering a `screen` session.

```bash
hacker@terminal-multiplexing~launching-screen:~$ screen
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{QEC3vFB6adTcS4e4StB1LYeDANY.0VN4IDOxwCO0gjNzEzW}
hacker@terminal-multiplexing~launching-screen:~$
```

### 📚 What I Learned

* `screen` creates a virtual terminal session; type `exit` or press `Ctrl-D` to leave it.
* Terminal multiplexers let you run multiple interactive sessions and detach/reattach to them later.

---
# 🔹 Detaching & Attaching

This level demonstrates `screen`'s ability to detach a running session and reattach later so long-running work continues even if you leave the terminal.

### 🏴 Flag

`pwn.college{oLswokRwfi6e4pSwVrrbmR-jfUd.0lN4IDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* I launched a `screen` session: `screen`.
* I detached from it with **Ctrl-A, d** (Screen showed `[detached from ...]`).
* Back in my original shell I ran `/challenge/run`, which secretly wrote the flag into the detached session.
* I reattached with `screen -r` and saw the flag in the resumed session.

```
screen

/challenge/run

screen -r

# Flag: pwn.college{oLswokRwfi6e4pSwVrrbmR-jfUd.0lN4IDOxwCO0gjNzEzW}
```

### 📚 What I Learned

* `Ctrl-A` then `d` detaches the current `screen` session without stopping processes inside it.
* `screen -r` reattaches to a detached session so you can resume interaction and view output produced while detached.
* Detaching is handy for long-running tasks and unstable connections.

---
# 🔹 Finding Windows

When you have multiple `screen` sessions, use `screen -ls` to list them and `screen -r <id|name>` to attach to the one you want. In this level, three sessions were created; only one contains the flag — inspect them until you find it, detaching (Ctrl-A d) before trying the next.

### 🏴 Flag

`pwn.college{4MX5cHaOK9q2HzTAO-W9PLIAKfe.01N4IDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* I listed running screen sessions with `screen -ls` to get their identifiers.
* I attached to each session using `screen -r <id>` and inspected the contents.
* If a session was a decoy, I detached with **Ctrl-A d** and tried the next session.
* When I attached to the session containing the flag, I saw the success message and the flag.

```bash
# list sessions
screen -ls

screen -r session_cb0872a1e33bbe04

screen -r session_21d4890cec978bab

echo pwn.college{4MX5cHaOK9q2HzTAO-W9PLIAKfe.01N4IDOxwCO0gjNzEzW}
```

### 📚 What I Learned

* `screen -ls` lists available sessions along with their PID.name identifiers.
* Use `screen -r <id|name>` to attach to a specific session; `screen -r` alone reattaches when only one session exists.
* Detach with **Ctrl-A d** to leave a session running while returning to your shell.
* Iteratively attaching/detaching is an effective way to hunt down the session containing your output or long-running job.

---
# 🔹 Switcing windows

This level teaches how to navigate multiple windows inside a single `screen` session.

### 🏴 Flag

`pwn.college{YWxB4A3KZ8OXl2kp98yBShYgZj8.0FO4IDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* I attached to the provided screen session with `screen -r`.
* Inside the session I switched to the other window (for example with **Ctrl-A n** or **Ctrl-A 1**).
* The second window contained the success message and the flag.

```
# attach to the session
screen -r

# -> pwn.college{YWxB4A3KZ8OXl2kp98yBShYgZj8.0FO4IDOxwCO0gjNzEzW}
```

### 📚 What I Learned

* `screen` supports multiple windows inside a single session; switch with `Ctrl-A c`, `Ctrl-A n`, `Ctrl-A p`, or `Ctrl-A <number>`.
* `Ctrl-A "` lists windows and lets you choose one interactively.
* Windows let you separate tasks while keeping everything within one session.

---
# 🔹 Detaching & Attaching (tmux)

This level demonstrates `tmux`'s detach/attach workflow using Ctrl-B as the prefix.

### 🏴 Flag

`pwn.college{AZOrAE6zbenUBvDthcRWmjh7FGF.0VO4IDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* Launched a tmux session with `tmux`.
* Detached from it with **Ctrl-B, d**.
* Ran `/challenge/run` in the original shell (it wrote the flag to the detached session).
* Reattached with `tmux attach` (or `tmux a`) and read the flag.

```
tmux

/challenge/run

tmux a

# Flag: pwn.college{AZOrAE6zbenUBvDthcRWmjh7FGF.0VO4IDOxwCO0gjNzEzW}
```

### 📚 What I Learned

* `Ctrl-B` then `d` detaches a tmux session; `tmux attach` rejoins it.
* `tmux` is a modern terminal multiplexer; keybindings differ from `screen` (Ctrl-B vs Ctrl-A).
* Detaching is useful for long-running tasks and unreliable network connections.

---
# 🔹 Switching Windows (tmux)

This level teaches how to navigate multiple windows inside a single `tmux` session using the `Ctrl-B` prefix.

### 🏴 Flag

`pwn.college{0JHJoGwqN1FcV09VzHwSERbFGRc.0FM5IDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* I attached to the tmux session with `tmux attach` (or `tmux a`).
* Inside tmux I switched to the window containing the flag (for example with **Ctrl-B 0** or **Ctrl-B n**).
* The window displayed the success message and the flag.

```
# attach to the tmux session
tmux attach
# Inside tmux: press Ctrl-B 0  (or Ctrl-B n) to switch windows
# Read the flag printed in the window
# -> pwn.college{0JHJoGwqN1FcV09VzHwSERbFGRc.0FM5IDOxwCO0gjNzEzW}
```

### 📚 What I Learned

* `tmux` windows can be switched with `Ctrl-B` followed by `c`, `n`, `p`, or a number to jump directly.
* `Ctrl-B w` brings up a window list for interactive selection.
* The status bar shows window indices and the currently active window (marked with `*`).

---
