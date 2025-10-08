# 🔹 Becoming Root with `su`

This level demonstrates `su` (substitute user) and the SUID behavior that lets it run as root. On this challenge, a root password exists (`hack-the-planet`) — use it to become root and read the flag.

### 🏴 Flag

`pwn.college{872h9pYdsyOBVNUO6h8NY9ChdiF.QX1UDN1wCO0gjNzEzW}`

### ⚡ How I Solved

* I ran `su` and entered the root password `hack-the-planet` when prompted.
* After gaining a root shell, I listed the home directory and read the file containing the flag.

```
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# ls
COLLEGE  PWN  a  instructions  myflag  not-the-flag  pwn  the-flag
root@users~becoming-root-with-su:/home/hacker# cat not-the-flag
pwn.college{872h9pYdsyOBVNUO6h8NY9ChdiF.QX1UDN1wCO0gjNzEzW}
root@users~becoming-root-with-su:/home/hacker#
```

### 📚 What I Learned

* `su` is often SUID-root and can spawn a root shell if you supply the correct root password.
* Modern systems typically use `sudo` instead of `su` because root passwords are uncommon.
* Always be cautious when operating as root — you have full system control.

---
# 🔹 Other users wiht su

This level requires switching to the `zardus` user with `su`, authenticating with their password, and running `/challenge/run` to receive the flag.

### 🏴 Flag

`pwn.college{QrrRoH5KP8WwXG6SmIHL7-7ay6q.QX2UDN1wCO0gjNzEzW}`

### ⚡ How I Solved

* I ran `su zardus` and entered the password `dont-hack-me`.
* As `zardus`, I executed `/challenge/run` which printed the flag.

```
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{QrrRoH5KP8WwXG6SmIHL7-7ay6q.QX2UDN1wCO0gjNzEzW}
zardus@users~other-users-with-su:/home/hacker$
```

### 📚 What I Learned

* `su <username>` switches to that user after providing their password.
* Use `su` to access another user's environment and run commands as them.

---
# 🔹 Cracking Passwords

This level simulates a leaked `/etc/shadow` file. Use John the Ripper to crack the hashed password for the `zardus` account, `su` to that user, and run `/challenge/run` to reveal the flag.

### 🏴 Flag

`pwn.college{4cqrW7-vUDhMeDvaocckuzmvGkQ.QX3UDN1wCO0gjNzEzW}`

### ⚡ How I Solved

* I cracked the leaked shadow file using John the Ripper: `john /challenge/shadow-leak`.
* John discovered the plaintext password (`aardvark` in this session).
* I switched to `zardus` with `su zardus` and entered the cracked password.
* As `zardus`, I executed `/challenge/run` to obtain the flag.

```
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:03 37% 1/3 0g/s 265.8p/s 265.8c/s 265.8C/s Ozardus99999...zardus
aardvark         (zardus)
1g 0:00:00:21 100% 2/3 0.04576g/s 266.4p/s 266.4c/s 266.4C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed

hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{4cqrW7-vUDhMeDvaocckuzmvGkQ.QX3UDN1wCO0gjNzEzW}
```

### 📚 What I Learned

* Password hashes in `/etc/shadow` can be cracked offline using tools like John the Ripper if an attacker obtains the file.
* Cracked passwords let you `su` into other accounts and access files or run commands as that user.
* Protect `/etc/shadow` carefully and prefer stronger defenses (e.g., salted hashes, rate-limiting login attempts, and using `sudo` with strict policies).

---
# 🔹 Using `sudo`

This level demonstrates `sudo`, which runs commands as another user (root by default) according to policy. Use `sudo` to read a file you can't access as your normal user.

### 🏴 Flag

`pwn.college{cc7uKs1P3ByJHTISaRT7FM7Um91.QX4UDN1wCO0gjNzEzW}`

### ⚡ How I Solved

* I used `sudo` to run `cat` as root and read the file that was otherwise inaccessible.

```bash
hacker@users~using-sudo:~$ ls
COLLEGE  PWN  a  instructions  myflag  not-the-flag  pwn  the-flag
hacker@users~using-sudo:~$ sudo cat not-the-flag
pwn.college{cc7uKs1P3ByJHTISaRT7FM7Um91.QX4UDN1wCO0gjNzEzW}
```

### 📚 What I Learned

* `sudo <cmd>` runs `<cmd>` as root (or another user if configured).
* `sudo` uses policy (defined in `/etc/sudoers`) rather than the target user's password.
* Use `sudo` when you need to perform administrative tasks without logging in as root.

---
