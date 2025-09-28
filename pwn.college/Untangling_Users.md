# 1. Becoming Root with Su
Using the su command to gain root privileges

## My solve
**Flag:** `pwn.college{YkKDofwuL-g_Ue8_xAPLi5wEa-y.QX1UDN1wiMxkjNzEzW}`

Used su to become root by providing the given password, then accessed the flag as the root user.

```
hacker@users~becoming-root-with-su:~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# cd /
root@users~becoming-root-with-su:/# ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
root@users~becoming-root-with-su:/# cat flag 
pwn.college{YkKDofwuL-g_Ue8_xAPLi5wEa-y.QX1UDN1wiMxkjNzEzW}
```

## What I learned
How to use the su command to elevate privileges to root by providing the root password.

## References 
pwn college description

# 2. Other Users with Su
Using su to switch between different user accounts

## My solve
**Flag:** `pwn.college{ENzDsqgQRAO-vjVtPYanyArkGCp.QX2UDN1wiMxkjNzEzW}`

Used su to switch to the zardus user with the provided password, then ran /challenge/run to get the flag.

```
hacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{ENzDsqgQRAO-vjVtPYanyArkGCp.QX2UDN1wiMxkjNzEzW}
```

## What I learned
How to use su with a username argument to switch to a specific user account.

## References 
pwn college description

# 3. Cracking Passwords
Using John the Ripper to crack a leaked shadow file password

## My solve
**Flag:** `pwn.college{wvw0JJxBtUIAHDQutHLvAQz2ecz.QX3UDN1wiMxkjNzEzW}`

I found a leaked shadow file at `/challenge/shadow-leak`. Using John the Ripper, I cracked the password hash for user zardus. After obtaining the password, I used su to switch to the zardus user and ran the challenge program to get the flag.

```bash
hacker@users~cracking-passwords:~$ john /challenge/
.catflag        DESCRIPTION.md  bin/            run             shadow-leak     
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak 
Created directory: /home/hacker/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:09 93% 1/3 0g/s 283.5p/s 283.5c/s 283.5C/s zardus999992002..zardus1963
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04930g/s 287.1p/s 287.1c/s 287.1C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ john --show
Password files required, but none specified
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak --show
hacker:NO PASSWORD:20357:0:99999:7:::
zardus:aardvark:20359:0:99999:7:::

2 password hashes cracked, 0 left
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run 
Congratulations, you have become Zardus! Here is your flag:
pwn.college{wvw0JJxBtUIAHDQutHLvAQz2ecz.QX3UDN1wiMxkjNzEzW}
```

## What I learned
How to use John the Ripper to crack password hashes from leaked shadow files and gain unauthorized access to user accounts.

## References
pwn college description

# 4. Using sudo
Using sudo to execute commands as the root user
## My solve
**Flag:** `pwn.college{oPHYwvMOi58X5sQfupovE6Wipxl.QX4UDN1wiMxkjNzEzW}`

I used sudo to run commands with root privileges, which allowed me to access files that are normally restricted. By using sudo to read the protected flag file, I was able to complete the challenge.

```bash
hacker@users~using-sudo:~$ sudo cat /flag 
pwn.college{oPHYwvMOi58X5sQfupovE6Wipxl.QX4UDN1wiMxkjNzEzW}
```

## What I learned
How to use sudo to execute commands with elevated privileges without needing to know the root password.

## References
pwn college description
