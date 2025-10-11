# 🔹 Chaining Commands with Semicolons

This level demonstrates using `;` to run multiple commands sequentially on a single line. The semicolon separates commands just like pressing Enter between them.

### 🏴 Flag

`pwn.college{oNPCSO54GeCmruoQlBVQcz2Ggwm.QX1UDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I ran the two required programs separated by a semicolon so the shell executed them one after the other.

```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{oNPCSO54GeCmruoQlBVQcz2Ggwm.QX1UDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* `cmd1; cmd2` executes `cmd1` first, waits for it to finish, then executes `cmd2`.
* Semicolons are useful for simple sequential command chains when you don't need conditional behavior.

---
# 🔹 Building on success

Use `&&` to run a second command **only if** the first command succeeds (exit code 0). This is useful when later steps must depend on earlier steps completing successfully.

### 🏴 Flag

`pwn.college{QlJSkzHBonlVBjljV6Yx0HdvsIQ.0lM0MDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* I ran the two challenge programs with the `&&` operator so the second runs only if the first exits successfully.

```bash
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{QlJSkzHBonlVBjljV6Yx0HdvsIQ.0lM0MDOxwCO0gjNzEzW}
```

### 📚 What I Learned

* `cmd1 && cmd2` executes `cmd2` only when `cmd1` exits with code `0` (success).
* Use `&&` to create safe, dependent command chains.

---
# 🔹 Handling failures

Use `||` to run a fallback command only if the first command fails (non-zero exit code). This is useful for error handling or providing alternatives when a command doesn't succeed.

### 🏴 Flag

`pwn.college{gwufYbMFl6u81u4bq6Cvj3bdBg0.01M0MDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* I ran `/challenge/first-failure || /challenge/second` so that the second program runs only when the first fails.

```bash
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{gwufYbMFl6u81u4bq6Cvj3bdBg0.01M0MDOxwCO0gjNzEzW}
```

### 📚 What I Learned

* `cmd1 || cmd2` executes `cmd2` only if `cmd1` exits with a non-zero code (failure).
* Use `||` for fallbacks, error messages, or recovery commands.

---
# 🔹 Your First Shell Script

This level asks you to place the two commands `/challenge/pwn` and `/challenge/college` into a shell script `x.sh` and run it with `bash`.

### 🏴 Flag

`pwn.college{k4OIt8nAEck_nLG66CvZ4G87np7.QXxcDO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I created a one-line script that runs the two programs in sequence, then executed it with `bash`.

```bash
hacker@chaining~your-first-shell-script:~$ echo '/challenge/pwn && /challenge/college' > x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{k4OIt8nAEck_nLG66CvZ4G87np7.QXxcDO0wCO0gjNzEzW}
```

### 📚 What I Learned

* Put long or repetitive command chains into a file and run them with `bash script.sh` to simplify workflows.
* Scripts let you version, reuse, and share sequences of commands easily.

---
# 🔹 Redirecting Script Output 

This level practices redirecting the output of a shell script into another program via a pipe. Create a script that runs `/challenge/pwn` then `/challenge/college`, then pipe the script's output to `/challenge/solve`.

### 🏴 Flag

`pwn.college{QBd3iMqDr5HEF4Kh_6yQAttMu5G.QX4ETO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I created a one-line script that runs the two challenges in sequence and saved it as `x.sh`.
* I ran the script and piped its output into `/challenge/solve`.

```bash
hacker@chaining~redirecting-script-output:~$ echo '/challenge/pwn && /challenge/college' > x.sh
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{QBd3iMqDr5HEF4Kh_6yQAttMu5G.QX4ETO0wCO0gjNzEzW}
```

### 📚 What I Learned

* Scripts are commands and can have their stdout redirected or piped just like any other command.
* Use `bash script.sh | cmd` to send the script's combined output into another program.

---
# 🔹 Executable Shell Scripts 

Rather than invoking `bash script.sh`, make the script executable and run it directly (e.g., `./x.sh`). This level demonstrates that scripts are ordinary executable files once given the `x` bit.

### 🏴 Flag

`pwn.college{YFrkIv2WbbPsR4Sn62NzQTWjrE8.QX0cjM1wCO0gjNzEzW}`

### ⚡ How I Solved

* I wrote the command into a script file and made it executable.

```bash
hacker@chaining~executable-shell-scripts:~$ echo '/challenge/solve' > ~/x.sh
hacker@chaining~executable-shell-scripts:~$ chmod u+x x.sh
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{YFrkIv2WbbPsR4Sn62NzQTWjrE8.QX0cjM1wCO0gjNzEzW}
```

### 📚 What I Learned

* `chmod u+x script` makes the script executable so you can run it as `./script`.
* Adding a shebang (e.g., `#!/bin/bash`) at the top of the script specifies the interpreter but isn't strictly required if you invoke it with an explicit shell.

---
# 🔹 Understanding Shebangs 

This level teaches shebangs (`#!`) so the kernel knows which interpreter to use when executing a script. Create an executable script with a proper shebang that prints `hack the planet`, then run the challenge to verify it.

### 🏴 Flag

`pwn.college{EQI5Bx45axG2Dthl_Jz3ThxLGmE.0VOzMDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* I created `/home/hacker/solve.sh` with a bash shebang and the required output, made it executable, and ran the challenge to verify.

```bash
hacker@chaining~understanding-shebangs:~$ echo -e '#!/bin/bash\necho "hack the planet"' > ~/solve.sh
hacker@chaining~understanding-shebangs:~$ chmod a+x solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{EQI5Bx45axG2Dthl_Jz3ThxLGmE.0VOzMDOxwCO0gjNzEzW}
```

### 📚 What I Learned

* A shebang (`#!`) on the first line tells the kernel which interpreter to invoke (e.g., `/bin/bash`).
* Make scripts executable with `chmod a+x script` and ensure the shebang is the very first line.
* Shebangs allow scripts to be executed correctly no matter how they're invoked (from shell, Python, etc.).

---
# 🔹 Scripting with Arguments

Write a script that accepts two arguments and prints them in reverse order.

### 🏴 Flag

`pwn.college{Yd1IqGydaBbQjAwYEVPl5R5QmsR.0VNzMDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* Created `/home/hacker/solve.sh` containing a bash shebang and a single echo that prints `$2 $1`.
* Made it executable and ran the challenge to verify.

```bash
hacker@chaining~scripting-with-arguments:~$ echo -e '#!/bin/bash\necho "$2 $1"' > ~/solve.sh
hacker@chaining~scripting-with-arguments:~$ chmod a+x solve.sh
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{Yd1IqGydaBbQjAwYEVPl5R5QmsR.0VNzMDOxwCO0gjNzEzW}
```

### 📚 What I Learned

* `$1`, `$2`, ... access script arguments; use them to build flexible scripts.
* Make scripts executable with `chmod a+x` so they can be run directly.

---
# 🔹 Scripting with Conditionals

This level asks you to write a script that inspects its first argument and prints `college` only when that argument equals `pwn`.

### 🏴 Flag

`pwn.college{wew_PJ7OzKSY9e8q0O_qsK_xLHP.0lNzMDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* I edited `/home/hacker/solve.sh` to use a bash shebang and an `if` test on `$1`.
* If `$1` equals `pwn`, the script echoes `college`; otherwise it does nothing.
* I made the script executable and ran the challenge to verify it.

```
nvim ~/solve.sh
#!/bin/bash
if [ "$1" == "pwn" ]
then
    echo "college"
fi
chmod a+x ~/solve.sh
/challenge/run
# -> Correct! Your script properly handles all the conditions.
# -> Flag: pwn.college{wew_PJ7OzKSY9e8q0O_qsK_xLHP.0lNzMDOxwCO0gjNzEzW}
```

### 📚 What I Learned

* Bash `if` uses the `test` syntax: `if [ expression ] ; then ... fi` — spacing matters.
* Script arguments are accessed with `$1`, `$2`, etc.
* Use conditional logic to make scripts behave differently based on inputs.

---
# 🔹 Scripting with Defualt case

Write a script that prints `college` when given `pwn` as the first argument, and `nope` for anything else.

### 🏴 Flag

`pwn.college{Ys2r_2-mw5acBGYbomVEakbMCTv.01NzMDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* I edited `/home/hacker/solve.sh` with a bash shebang and an `if`/`else` that tests `$1`.
* Made the script executable and ran the challenge harness to verify.

```
nvim ~/solve.sh
#!/bin/bash
if [ "$1" == "pwn" ]
then
  echo "college"
else
  echo "nope"
fi

chmod a+x ~/solve.sh
/challenge/run
# -> Correct! Your script properly handles the if/else conditions.
# -> Flag: pwn.college{Ys2r_2-mw5acBGYbomVEakbMCTv.01NzMDOxwCO0gjNzEzW}
```

### 📚 What I Learned

* Use `if [ condition ]; then ... else ... fi` for branching logic in bash.
* `else` runs when the `if` condition is false; spacing in `[` `]` matters.
* Script arguments are accessed via `$1`, `$2`, etc., enabling flexible behavior.

---
# 🔹 Scripting with Multiple Conditions

Write a script that checks one argument against multiple possibilities using `if` / `elif` / `else` and prints the appropriate response.

### 🏴 Flag

`pwn.college{sZnmKWayNxh3u29iIp6w0FERIVx.0FOzMDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* I edited `/home/hacker/solve.sh` with a bash shebang and an `if` / `elif` / `else` chain that checks `$1`.
* The script prints:

  * "the planet" when `$1` is `hack`
  * "college" when `$1` is `pwn`
  * "linux" when `$1` is `learn`
  * "unknown" for anything else
* Made the script executable and ran the challenge to verify.

```bash
#!/bin/bash
if [ "$1" == "hack" ]
then
    echo "the planet"
elif [ "$1" == "pwn" ]
then
    echo "college"
elif [ "$1" == "learn" ]
then
    echo "linux"
else
    echo "unknown"
fi

chmod a+x ~/solve.sh
/challenge/run
# -> Correct! Your script properly handles all the conditions with elif.
# -> Flag: pwn.college{sZnmKWayNxh3u29iIp6w0FERIVx.0FOzMDOxwCO0gjNzEzW}
```

### 📚 What I Learned

* Use `elif` to check multiple conditions in order.
* Remember spacing around `[` and `]`: `if [ "$1" == "pwn" ]`.
* `else` handles any case not matched by previous checks.

---
# 🔹 Reading Shell Scripts

This level hides the correct password inside the shell script `/challenge/run`. Read the script to discover the password, then feed it to the program to get the flag.

### 🏴 Flag

`pwn.college{IL2X10mp_oH5Tujtw5bK-zgfPmA.0lMwgDOxwCO0gjNzEzW}`

### ⚡ How I Solved

* I read the challenge script with `cat /challenge/run` to inspect its logic.
* The script reads one line into `GUESS` and compares it to the hardcoded string `hack the PLANET`.
* I ran `/challenge/run`, entered the exact password `hack the PLANET`, and the script printed the flag.

```
hacker@chaining~reading-shell-scripts:~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
	echo "CORRECT! Your flag:"
	cat /flag
else
	echo "Read the /challenge/run file to figure out the correct password!"
fi

# Run and submit the password from the script:
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
CORRECT! Your flag:
pwn.college{IL2X10mp_oH5Tujtw5bK-zgfPmA.0lMwgDOxwCO0gjNzEzW}
```

### 📚 What I Learned

* Shell scripts are often human-readable; `cat` the file to inspect behavior and hidden values.
* Scripts may contain hardcoded secrets — reading source code can reveal them.
* Always be cautious with secrets in source code; they should be avoided in real systems.

---
