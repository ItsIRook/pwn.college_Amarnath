# 🔹 Changing File Ownership

In this challenge you are allowed to change the owner of `/flag` (normally a root-only action). After changing ownership to the `hacker` user, you can read the flag.

### 🏴 Flag

`pwn.college{wBcBNV2EOX9sVq_2mMiLdQxc_ha.QXxEjN0wCO0gjNzEzW}`

### ⚡ How I Solved

* I changed the owner of `/flag` to `hacker`:

```
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
```

* Then I read the flag:

```
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{wBcBNV2EOX9sVq_2mMiLdQxc_ha.QXxEjN0wCO0gjNzEzW}
```

### 📚 What I Learned

* `chown user file` changes the ownership of a file; typically only root can do this.
* Ownership controls who can read or modify files; changing ownership can grant access to otherwise-restricted files.

---
# 🔹 Groups and Files

This level teaches how filesystem groups control access. The `/flag` file is readable by its owning group, which is currently `root`. You're allowed to change the group ownership as the `hacker` user with `chgrp`, so change the group to `hacker` and then read the flag.

### 🏴 Flag

`pwn.college{ogaMdcgXp60YS9CBQQQ2GRBvLsz.QXxcjM1wCO0gjNzEzW}`

### ⚡ How I Solved

* I changed the group owner of `/flag` to `hacker` with `chgrp hacker /flag`.
* Then I read the flag with `cat /flag`.

```
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{ogaMdcgXp60YS9CBQQQ2GRBvLsz.QXxcjM1wCO0gjNzEzW}
```

### 📚 What I Learned

* Files have both a user owner and a group owner; group membership can grant access.
* `chgrp group file` changes the file's group ownership (normally requires privileges).
* Making a file owned by a group you're in is a convenient privilege escalation when allowed.

---
# 🔹 Fun with Group Names

In this level the group name for your user is randomized (not `hacker`). Use `id` to discover your actual primary group name, then use `chgrp` to change `/flag`'s group to that name and read the flag.

### 🏴 Flag

`pwn.college{4bd_G5qcO6Ey75zcwIlXw0Tz0b3.QXycjM1wCO0gjNzEzW}`

### ⚡ How I Solved

* I checked my group name with `id` and learned it was `grp19767`.
* I changed the group of `/flag` to that group and then read the flag.

```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp19767) groups=1000(grp19767)

hacker@permissions~fun-with-groups-names:~$ chgrp grp19767 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{4bd_G5qcO6Ey75zcwIlXw0Tz0b3.QXycjM1wCO0gjNzEzW}
```

### 📚 What I Learned

* A user's primary group name may not match their username; use `id` to inspect it.
* `chgrp <group> <file>` updates a file's group ownership; when allowed, this can grant read access.

---
# 🔹 Changing Permissions

In this level you are granted the power to change file permissions even without owning or writing the file. Use `chmod` to make `/flag` readable and then read the flag.

### 🏴 Flag

`pwn.college{QHyNTk-Ol_tVcLSORgxbTuxI9YX.QXzcjM1wCO0gjNzEzW}`

### ⚡ How I Solved

* I changed the permissions of `/flag` to allow everyone to read (and for completeness, execute/write):

```bash
hacker@permissions~changing-permissions:~$ chmod a+rwx /flag
```

* Then I read the flag:

```bash
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{QHyNTk-Ol_tVcLSORgxbTuxI9YX.QXzcjM1wCO0gjNzEzW}
```

### 📚 What I Learned

* `chmod WHO±PERMS file` modifies permissions (e.g., `a+r` adds read for all).
* `chmod a+rwx file` makes a file readable, writable, and executable by everyone.
* Normally changing permissions requires appropriate privileges, but this level relaxes that restriction for practice.

---
# 🔹 Executable Files

Some files must have the execute bit set before the kernel will allow them to be run. Use `chmod` to add execute permission to `/challenge/run`, then execute it to receive the flag.

### 🏴 Flag

`pwn.college{ERcFNzxno6LIJAjKaZqFqvX61Ty.QXyEjN0wCO0gjNzEzW}`

### ⚡ How I Solved

* I added execute permission to `/challenge/run` for all users with `chmod a+x /challenge/run`.
* I executed the program and it printed the flag.

```
hacker@permissions~executable-files:~$ chmod a+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{ERcFNzxno6LIJAjKaZqFqvX61Ty.QXyEjN0wCO0gjNzEzW}
```

### 📚 What I Learned

* The execute permission (`x`) controls whether a file can be run as a program.
* `chmod a+x file` makes a file executable for user, group, and others.
* Even if you can read a program, you cannot run it unless the execute bit is set.

---
# 🔹 Permission Tweaking Practice

This level requires you to repeatedly set specific permission bits on `/challenge/pwn` eight times in a row. Succeeding eight rounds lets you change `/flag`'s permissions so you can read it.

### 🏴 Flag

`pwn.college{QqZ7e-wMGHtHoRB_aJGcQq3ZjYU.QXwEjN0wCO0gjNzEzW}`

### ⚡ How I Solved

* I launched the challenge with `/challenge/run` and followed the prompted rounds.
* For each round I used `chmod` with symbolic modes (e.g., `g+x`, `a+w`, `u-r`, etc.) to match the required permission bits.
* After completing eight correct rounds, the challenge allowed me to `chmod a+r /flag` and read the flag.

```
hacker@permissions~permission-tweaking-practice:~$ /challenge/run
# Rounds 1–8: apply the requested chmod changes; examples from the session:
hacker@permissions~permission-tweaking-practice:~$ chmod g+x,a+x,u-x /challenge/pwn   # round 1
hacker@permissions~permission-tweaking-practice:~$ chmod g+w,a+w /challenge/pwn       # round 2
hacker@permissions~permission-tweaking-practice:~$ chmod a-rx,g+rx,u+r /challenge/pwn # round 3
hacker@permissions~permission-tweaking-practice:~$ chmod a-w /challenge/pwn          # round 4
hacker@permissions~permission-tweaking-practice:~$ chmod g-x /challenge/pwn         # round 5
hacker@permissions~permission-tweaking-practice:~$ chmod u-r /challenge/pwn         # round 6
hacker@permissions~permission-tweaking-practice:~$ chmod g+w /challenge/pwn         # round 7
hacker@permissions~permission-tweaking-practice:~$ chmod g-r /challenge/pwn         # round 8

# After 8 rounds the challenge granted you permission to change /flag:
hacker@permissions~permission-tweaking-practice:~$ chmod a+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{QqZ7e-wMGHtHoRB_aJGcQq3ZjYU.QXwEjN0wCO0gjNzEzW}
```

### 📚 What I Learned

* `chmod` symbolic modes (WHO±PERMS) let you tweak specific permission bits without overwriting unrelated bits.
* Practice reading permission requirements carefully: `u`, `g`, `o`, and `a` target user/group/other/all; `r`, `w`, `x` specify read/write/execute.
* Small mistakes reset the challenge; take the extra second to verify the current permissions before applying changes.

---
# 🔹 Permissions Setting Practice

This level asks you to set exact permission masks using `chmod` with `=` and chained mode segments separated by commas. Succeed eight rounds to gain the ability to `chmod` `/flag` and read it.

### 🏴 Flag

`pwn.college{QYXxaFMPURCwfEhQ9VH5fmvg81o.QXzETO0wCO0gjNzEzW}`

### ⚡ How I Solved

* I launched the challenge with `/challenge/run` and followed the requested permission masks for each round.
* I used `chmod` with `=` and comma-separated segments where appropriate (for example `chmod a-rw,g+rw` or `chmod a+wx,g-x`).
* After completing eight correct rounds, the challenge allowed me to `chmod u+r /flag` and read the flag.

```
# Example commands from the session (one per round):
chmod a-rw,g+rw /challenge/pwn
chmod a+wx,g-x /challenge/pwn
chmod a-wx,a+r /challenge/pwn
chmod a+wx,g-rwx,u-rx /challenge/pwn
chmod u+r,u-w,g+rw /challenge/pwn
chmod a-rx,g+r,g-w /challenge/pwn
chmod u+rx,g+w /challenge/pwn
chmod u-x /challenge/pwn

# After 8 rounds:
chmod u+r /flag
cat /flag
# -> pwn.college{QYXxaFMPURCwfEhQ9VH5fmvg81o.QXzETO0wCO0gjNzEzW}
```

### 📚 What I Learned

* `chmod u=...,g=...,o=...` sets exact permission sets; use commas to chain multiple targets.
* `=` overwrites the targeted class's permissions entirely; `+` and `-` add/remove bits relative to current state.
* Careful read-back of current permissions before changing reduces mistakes in sequential challenges.

---
# 🔹 The SUID Bit

SUID (Set User ID) lets an executable run with the privileges of the file owner (often root). The `s` appears where the user's execute bit would be, for example: `-rwsr-xr-x`.

In this level you are allowed to set the SUID bit on `/challenge/getroot`. Once set, executing the program spawns a root shell which you can use to read `/flag`.

### 🏴 Flag

`pwn.college{400vmJus438GqUdND1kBzN-qfGX.QXzEjN0wCO0gjNzEzW}`

### ⚡ How I Solved

* I added the SUID bit to the program:

```
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
```

* I executed the program, which ran with root privileges and gave me a root shell:

```
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{400vmJus438GqUdND1kBzN-qfGX.QXzEjN0wCO0gjNzEzW}
```

### 📚 What I Learned

* `chmod u+s file` sets the SUID bit; an executable with SUID will run as the file owner (commonly root).
* SUID is powerful and dangerous: improperly set SUID on root-owned programs can create privilege escalation vectors.
* Only use SUID on trusted, well-audited programs.

---
