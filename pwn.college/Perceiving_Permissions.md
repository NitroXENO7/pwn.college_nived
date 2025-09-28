# 1. Changing File Ownership
Using chown to change file ownership and access the flag
## My solve
**Flag:** `pwn.college{8m0Jq5c1_Pdyuh5lMPg-EIsbKTj.QXxEjN0wiMxkjNzEzW}`

I examined the permissions of the flag file and noticed it was owned by root with restrictive permissions. For this challenge, the hacker user was given the ability to use chown, which is normally restricted to root. I used chown to change the ownership of the flag file to my user, which allowed me to read it and obtain the flag.

```bash
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{8m0Jq5c1_Pdyuh5lMPg-EIsbKTj.QXxEjN0wiMxkjNzEzW}
```

## What I learned
How to use chown to change file ownership and gain access to otherwise restricted files.

## References
pwn college description

# 2. Groups and Files
Using chgrp to change file group ownership and access the flag
## My solve
**Flag:** `pwn.college{IwlTWxnzXOSNYJpRbGMblSmj4Fc.QXxcjM1wiMxkjNzEzW}`

I checked the permissions of the flag file and found it was owned by the root group with permissions allowing group members to read it. For this challenge, I could use chgrp despite not being root. I changed the group ownership of the flag file to the hacker group (which I was a member of), which gave me read access to obtain the flag.

```bash
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag 
pwn.college{IwlTWxnzXOSNYJpRbGMblSmj4Fc.QXxcjM1wiMxkjNzEzW}
```

## What I learned
How to use chgrp to change the group ownership of files to gain access to group-readable files.

## References
pwn college description

# 3. Fun with Group Names
Using id to identify your group and chgrp to access the flag
## My solve
**Flag:** `pwn.college{gq-vs2gv1OlIKe6uTH8E249LOhm.QXycjM1wiMxkjNzEzW}`

In this challenge, my user was a member of a randomly named group instead of the usual 'hacker' group. I used the id command to identify which group I belonged to, then used chgrp to change the flag file's group ownership to this group. Once the flag file was owned by my group, I could read it to obtain the flag.

```bash
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp20501) groups=1000(grp20501)
hacker@permissions~fun-with-groups-names:~$ chgrp grp20501 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{gq-vs2gv1OlIKe6uTH8E249LOhm.QXycjM1wiMxkjNzEzW}
```

## What I learned
How to use id to identify group memberships and apply that information when changing file group ownership.

## References
pwn college description

# 4. Changing Permissions
Using chmod to modify file permissions and access the flag
## My solve
**Flag:** `pwn.college{smkgS-z4DHNztlij94hvZDwFz5q.QXzcjM1wiMxkjNzEzW}`

In this challenge, I needed to change the permissions of the `/flag` file to allow read access. Using the `chmod` command, I modified the permissions to make the file readable by users other than the owner. This enabled me to read the flag, which was previously inaccessible due to strict permissions.

```bash
hacker@permissions~changing-permissions:~$ chmod a+rx /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{smkgS-z4DHNztlij94hvZDwFz5q.QXzcjM1wiMxkjNzEzW}
```

## What I learned
How to use `chmod` to change file permissions, allowing access to restricted files.

## References
pwn college description

# 5. Executable Files
Changing execute permissions to run a program and access the flag
## My solve
**Flag:** `pwn.college{UFrsERzVhZooSeHMzUPCVI8jEZR.QXyEjN0wiMxkjNzEzW}`

In this challenge, I needed to execute the `/challenge/run` program to obtain the flag, but it initially lacked the necessary execute permission for my user. I used `chmod` to add the execute permission for others, allowing me to run the program successfully.

```bash
hacker@permissions~executable-files:~$ chmod a+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{UFrsERzVhZooSeHMzUPCVI8jEZR.QXyEjN0wiMxkjNzEzW}
```

## What I learned
How to use `chmod` to modify execute permissions on a file, enabling programs to be run by users.

## References
pwn college description

# 6. Permission Tweaking Practice
Changing permissions on the `/challenge/pwn` file
## My solve
**Flag:** `pwn.college{YDSe-ue8qH02fUJk4jdGX-b8AA9.QXwEjN0wiMxkjNzEzW}`

In this challenge, I was tasked with changing the permissions of the `/challenge/pwn` file correctly multiple times in a row. I launched the challenge and followed the specified instructions to adjust the permissions accordingly. Successfully completing this task allowed me to eventually change the permissions of `/flag` to make it readable.

```bash
hacker@permissions~permission-tweaking-practice:~$ chmod go+wx /challenge/pwn
chmod u-r /challenge/pwn
chmod u+r /challenge/pwn
chmod go-x /challenge/pwn
chmod u-w /challenge/pwn
chmod g-r /challenge/pwn
chmod u+w /challenge/pwn
chmod g-w /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": rw-rwxrwx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -w-rwxrwx
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": -w-rwxrwx
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rw-rwxrwx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": rw-rwxrwx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rw-rw-rw-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": rw-rw-rw-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r--rw-rw-
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": r--rw-rw-
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r---w-rw-
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": r---w-rw-
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw--w-rw-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": rw--w-rw-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw----rw-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
                                                                    
hacker@permissions~permission-tweaking-practice:~$ chmod a+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{YDSe-ue8qH02fUJk4jdGX-b8AA9.QXwEjN0wiMxkjNzEzW}
```

## What I learned
How to accurately modify file permissions using `chmod` based on specific requirements.

## References
pwn college description

# 7. Permission Setting Practice
Setting file permissions using `chmod` with overriding and chaining
## My solve
**Flag:** `pwn.college{IRrxh7f-oZ3P-qQdZsPfJKdQjO9.QXzETO0wiMxkjNzEzW}`

In this challenge, I was required to change the permissions of the `/challenge/pwn` file using the `=` operator and command chaining to specify different permissions for the user and group. By correctly setting the permissions as instructed, I successfully completed the challenge.

```bash
hacker@permissions~permissions-setting-practice:~$ /challenge/run
Round 1 of 8!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": --xr-x--x
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rr--x,g=r-x,o=--x /challenge/pwn
NEEDED, BUT UNMET permissions of "/challenge/pwn": --xr-x--x
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

CURRENT, INCORRECT permissions of "/challenge/pwn": r--r-----
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

You set the permissions incorrectly! Restarting the game!
hacker@permissions~permissions-setting-practice:~$ chmod u=x,g=rx,o=x /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": --xr-x--x
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": --xr-x---
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod o=- /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": --xr-x---
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -wxr---wx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=wx,g=r,o=wx /challenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": -wxr---wx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -w-rw-r-x
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=wx,g=rw,o=rx /challenge/pwn
NEEDED, BUT UNMET permissions of "/challenge/pwn": -w-rw-r-x
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

CURRENT, INCORRECT permissions of "/challenge/pwn": -wxrw-r-x
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

You set the permissions incorrectly! Restarting the game!
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=rw,o=rx /challenge/pwn
NEEDED, BUT UNMET permissions of "/challenge/pwn": --xr-x--x
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

CURRENT, INCORRECT permissions of "/challenge/pwn": -w-rw-r-x
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

You set the permissions incorrectly! Restarting the game!
hacker@permissions~permissions-setting-practice:~$ chmod u=x,g=r-x,o=x /challenge/pwn
NEEDED, BUT UNMET permissions of "/challenge/pwn": --xr-x--x
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

CURRENT, INCORRECT permissions of "/challenge/pwn": --xr----x
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

You set the permissions incorrectly! Restarting the game!
hacker@permissions~permissions-setting-practice:~$ chmod u=x,g=rx,o=x /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": --xr-x--x
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": --xr-x---
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=x,g=rx,o=- /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": --xr-x---
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -wxr---wx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=wx,g=r,o=wx /challenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": -wxr---wx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -w-rw-r-x
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=rw,o=rx /challenge/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": -w-rw-r-x
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rw--w-r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rw,g=w,o=r /challenge/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": rw--w-r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-xrwxr--
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rx,g=rwx,o=r /challenge/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": r-xrwxr--
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -wx-wx-w-
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=wx,g=wx,o=w /challenge/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": -wx-wx-w-
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-rwx-w-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rw,g=rwx,o=w /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod a+r /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{IRrxh7f-oZ3P-qQdZsPfJKdQjO9.QXzETO0wiMxkjNzEzW}
```

## What I learned
How to use `chmod` with the `=` operator to overwrite file permissions and chain multiple changes for different user categories.

## References
pwn college description

# 8. The SUID Bit
Setting the SUID bit on an executable to gain elevated access
## My solve
**Flag:** `pwn.college{QqSmdZeqMD6gGrQ_bN1iTLEALlR.QXzEjN0wiMxkjNzEzW}`

In this challenge, I was instructed to add the SUID bit to the `/challenge/getroot` program. This bit allows the program to run with the permissions of the file's owner (in this case, `root`). After setting the SUID bit using `chmod`, I was able to execute the program and spawn a root shell, which let me read the flag.

```bash
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot                                                                    
hacker@permissions~the-suid-bit:~$ /challenge/getroot 
SUCCESS! You have set the suid bit on this program, and it is running as root! 
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag 
pwn.college{QqSmdZeqMD6gGrQ_bN1iTLEALlR.QXzEjN0wiMxkjNzEzW}
```

## What I learned
How to use `chmod` to set the SUID bit on an executable, allowing it to run with elevated permissions.

## References
pwn college description
