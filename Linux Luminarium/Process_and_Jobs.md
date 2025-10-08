# 🔹 Listing Processes
In this level the `/challenge/run` binary was renamed and the `/challenge` directory was made unreadable. The running program still appears in the process list, so you must use `ps` to discover its filename and then execute it directly to get the flag.

### 🏴 Flag

`pwn.college{Mf1VA3-rKXR58qR9f6xP3D1f9tj.QX4MDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I listed processes with `ps aux` to find the running program under `/challenge`.
* From the process list I read the full path: `/challenge/14989-run-3987`.
* I executed it directly to reveal the flag.

```
hacker@processes~listing-processes:~$ ps aux
... (truncated) ...
root         132  0.0  0.0   4132  2560 ?        S    05:50   0:00 /challenge/14989-run-3987
...

hacker@processes~listing-processes:~$ /challenge/14989-run-3987
Yahaha, you found me! Here is your flag:
pwn.college{Mf1VA3-rKXR58qR9f6xP3D1f9tj.QX4MDO0wCO0gjNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').
```

### 📚 What I Learned

* `ps aux` (or `ps -ef`) shows processes for all users; `ps auxww` prevents truncation of long command lines.
* Even if a directory is unreadable, executables running from it still appear in the process list.
* You can execute a discovered program by its full path to get its output.

---
# 🔹 Killing Processes

This level requires terminating a running process so that `/challenge/run` can execute. Use `ps` to find the interfering process and `kill` with its PID to terminate it.

### 🏴 Flag

`pwn.college{YjvJh-El9MaqwXhD-237seDMLOb.QXyQDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I listed processes with `ps aux` and located the interfering process (the challenge showed `/challenge/dont_run`).
* I terminated the interfering process by calling `kill <PID>` (in the session shown, `kill 137`).
* I then ran `/challenge/run` and it printed the flag.

```
hacker@processes~killing-processes:~$ ps aux
... (truncated) ...
hacker       136  0.0  0.0 231576  3520 ?        Ss   05:56   0:00 /challenge/dont_run
...

hacker@processes~killing-processes:~$ kill 137
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{YjvJh-El9MaqwXhD-237seDMLOb.QXyQDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* Use `ps aux` (or `ps -ef`) to find running processes and their PIDs.
* `kill <PID>` sends a termination signal allowing the process to exit cleanly.
* Sometimes the interfering process is obvious from its command column (e.g., `/challenge/dont_run`).

---
# 🔹 Interrupting Processes

Some programs wait for input or otherwise hang in your terminal. Ctrl-C sends an interrupt (SIGINT) to the foreground process, usually causing it to exit cleanly.

### 🏴 Flag

`pwn.college{sX8un_udo2NWT810wx9hZK6zI8V.QXzQDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I ran the blocking program: `/challenge/run`.
* When it refused to give the flag, I pressed **Ctrl-C** to interrupt the process.
* The program exited and printed the flag.

```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{sX8un_udo2NWT810wx9hZK6zI8V.QXzQDO0wCO0gjNzEzW}
hacker@processes~interrupting-processes:~$
```

### 📚 What I Learned

* Ctrl-C sends SIGINT to the foreground process, which typically causes it to terminate.
* Interrupting is useful when a program is waiting for input or is otherwise unresponsive.
* Some programs may ignore or handle SIGINT specially; in those cases other signals or methods may be required.

---
# 🔹 Killing Misbehaving Processes

This level requires identifying and terminating a misbehaving process that is writing decoy flags into a named pipe at `/tmp/flag_fifo`. After killing the decoy, run `/challenge/run`, then read the FIFO to receive the true flag.

### 🏴 Flag

`pwn.college{88P2egWEm26Rc0FSEHBAjOBTuSg.0FNzMDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* I listed processes to find the decoy and the Python helper writing into the FIFO.
* Killing the root-owned launcher failed (`kill 139` returned "Operation not permitted"). I terminated the user-space decoy process instead (`kill 142`).
* I ran the challenge and then read the FIFO to obtain the flag.

```bash
hacker@processes~killing-misbehaving-processes:~$ ps aux
...
root         139  0.0  0.0   5204  3520 ?        S    06:06   0:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
hacker       142  0.1  0.0  13516  9280 ?        Ss   06:06   0:00 /usr/bin/python /challenge/decoy
...

hacker@processes~killing-misbehaving-processes:~$ kill 139
bash: kill: (139) - Operation not permitted
hacker@processes~killing-misbehaving-processes:~$ kill 142
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
^C
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{88P2egWEm26Rc0FSEHBAjOBTuSg.0FNzMDOxwCO0gjNzEzW}
```

### 📚 What I Learned

* Some processes may be root-owned launchers that you cannot kill; look for user-space worker processes that you can terminate.
* Named pipes (FIFOs) are buffered; data already written may still appear after killing the writer.
* Workflow: `ps aux` → identify offending PID → `kill <PID>` → run producer → read FIFO (`cat /tmp/flag_fifo`).

---
# 🔹 Suspending Processes

This level requires running a program, suspending it with **Ctrl-Z**, and then launching a second copy of the same program in the same terminal so the challenge detects two instances and rewards you with the flag.

### 🏴 Flag

`pwn.college{wPKM15c1RNB-_7VrXmedwXHycOk.QX1QDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I launched `/challenge/run` in the terminal.
* I pressed **Ctrl-Z** to suspend the first copy (it moved to the background in a stopped state).
* While the first copy remained suspended, I launched a second `/challenge/run` in the same terminal; the challenge detected two copies and printed the flag.

```bash
hacker@processes~suspending-processes:~$ /challenge/run
... (program asks for another copy) ...
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
Yay, I found another version of me! Here is the flag:
pwn.college{wPKM15c1RNB-_7VrXmedwXHycOk.QX1QDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* **Ctrl-Z** sends SIGTSTP, suspending the foreground job and returning control to the shell.
* Suspended jobs remain in memory and can coexist with newly launched processes in the same terminal.
* Use `jobs`, `fg`, and `bg` to manage suspended/background jobs when needed.

---
# 🔹 Resuming Processes

This level practices resuming a suspended job using the shell builtin `fg`.

### 🏴 Flag

`pwn.college{0ROxyQDo0ZpENeZ6mrH1wL156QG.QX2QDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I launched `/challenge/run` in the terminal.
* I suspended it with **Ctrl-Z** to send it to the background in a stopped state.
* I resumed it with the `fg` command, which brought it back to the foreground and allowed it to print the flag.

```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{0ROxyQDo0ZpENeZ6mrH1wL156QG.QX2QDO0wCO0gjNzEzW}
Don't forget to press Enter to quit me!
```

### 📚 What I Learned

* **Ctrl-Z** suspends the foreground job (SIGTSTP), keeping it in memory but stopped.
* `fg` resumes a suspended job and places it in the foreground.
* Use `jobs` to list suspended/background jobs when managing multiple jobs.

---
# 🔹 Backgrounding Processes

This level requires you to suspend a foreground job with **Ctrl-Z**, then resume it in the background with the `bg` builtin, and finally launch a second copy so the challenge detects a running instance and a backgrounded instance in the same terminal.

### 🏴 Flag

`pwn.college{EOa-aiwQqWBd9zsrgZIuGyUUjmX.QX3QDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I launched `/challenge/run` in the terminal.
* I suspended it with **Ctrl-Z**, which stopped the job but left it in memory.
* I resumed the stopped job in the background with `bg`, so it continued running but returned control to the shell.
* While the first copy was running in the background, I launched a second `/challenge/run` in the foreground — the challenge detected both and printed the flag.

```
hacker@processes~backgrounding-processes:~$ /challenge/run
... (program asks for another copy running and not suspended) ...
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &

hacker@processes~backgrounding-processes:~$ /challenge/run
Yay, I found another version of me running in the background! Here is the flag:
pwn.college{EOa-aiwQqWBd9zsrgZIuGyUUjmX.QX3QDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* **Ctrl-Z** sends SIGTSTP and suspends the foreground job (STAT shows `T`).
* `bg` resumes the suspended job but keeps it in the background (STAT becomes `S` for sleeping or similar, and it loses the `+` foreground marker).
* Backgrounded jobs run while you regain a shell prompt to start other commands.
* Use `jobs`, `fg`, and `bg` to manage suspended and backgrounded tasks.

---
# 🔹 Foregrounding processes

This level requires you to suspend a running program, resume it in the background with `bg`, then bring it back to the foreground with `fg` (without re-suspending it).

### 🏴 Flag

`pwn.college{0EF-kBd5PijzZzyM9bffVLU81Fm.QX4QDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* Launched `/challenge/run` in the terminal.
* Pressed **Ctrl-Z** to suspend it (job becomes `Stopped`).
* Ran `bg` to resume it in the background (job runs, shell prompt returns).
* Used `fg` to bring the backgrounded job back into the foreground; the program printed the flag.

```
hacker@processes~foregrounding-processes:~$ /challenge/run
... (program asks to suspend and background it) ...
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{0EF-kBd5PijzZzyM9bffVLU81Fm.QX4QDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* **Ctrl-Z** suspends a foreground job (STAT `T`).
* `bg` resumes a suspended job in the background (STAT becomes `S`).
* `fg` brings a backgrounded job back to the foreground so you can interact with it.

---
# 🔹 Starting Backgrounded Processes

You can start a command in the background immediately by appending `&` to it. This lets the process run while you keep using the shell.

### 🏴 Flag

`pwn.college{YleygvgFLbJlaWtDcKPCmw9kW1c.QX5QDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I launched the challenge program in the background by appending `&` to the command.
* The shell returned a job id and PID; the program printed the flag while running in the background.

```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 162
hacker@processes~starting-backgrounded-processes:~$

Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{YleygvgFLbJlaWtDcKPCmw9kW1c.QX5QDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* Appending `&` runs a command in the background immediately (no Ctrl-Z needed).
* The shell prints a job number and PID when you background a job.
* Background processes run while you retain the shell prompt to continue work.

---
# 🔹 Process Exit Codes

Every command exits with a numeric code indicating success (usually `0`) or failure (non-zero). The shell stores the last command's exit code in the special variable `$?`.

### 🏴 Flag

`pwn.college{gcFHfVgWha5Rs9DWU_8bIxRU6Os.QX5YDO1wCO0gjNzEzW}`

### ⚡ How I Solved

* I ran `/challenge/get-code`, which exited with a non-zero code.
* I echoed `$?` to see the exit code (which was `188`).
* I passed that code to `/challenge/submit-code` as an argument to receive the flag.

```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!

hacker@processes~process-exit-codes:~$ echo $?
188

hacker@processes~process-exit-codes:~$ /challenge/submit-code 188
CORRECT! Here is your flag:
pwn.college{gcFHfVgWha5Rs9DWU_8bIxRU6Os.QX5YDO1wCO0gjNzEzW}
```

### 📚 What I Learned

* `$?` contains the exit code of the most recently terminated command.
* Successful commands typically return `0`; failures return non-zero values.

---
