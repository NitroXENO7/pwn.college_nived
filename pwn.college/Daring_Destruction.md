# 1. The Fork Bomb
Creating a fork bomb to deplete system resources  
## My solve  
**Flag:** `pwn.college{sYh1MZpPunSC2ICuxKihYcKWCMV.0VMyEzNxwiMxkjNzEzW}`  
In this challenge, I wrote a shell script that continuously forked new processes to create a fork bomb, causing the system to become unresponsive to new processes. I ran the `/challenge/check` command to confirm that the flag was successfully obtained before the system became unusable.  

```bash
hacker@destruction~the-fork-bomb:~$ ./forkbomb.sh 
hacker@destruction~the-fork-bomb:~$ /challenge/check 
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
It looks like the system can still spawn processes. We'll check again in 5 seconds...
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
/home/hacker/forkbomb.sh: fork: retry: Resource temporarily unavailable
You successfully saturated the process table.  Here is your hard-earned flag:
pwn.college{sYh1MZpPunSC2ICuxKihYcKWCMV.0VMyEzNxwiMxkjNzEzW}
```

## What I learned  
How to create a fork bomb by recursively launching processes to overwhelm system resources.  

## References  
pwn college description  

---

# 2. Disk Space Doomsday
Filling up disk space with excess data  
## My solve  
**Flag:** `pwn.college{cuKmZkbWcrpQpvYNxOGWTF0CQcb.0lMyEzNxwiMxkjNzEzW}`  
I used the `yes` command to generate a massive amount of data, redirecting the output to a file in my home directory. I then ran `/challenge/check`, which attempted to create a 1 MB temporary file to verify that the disk was full. I deleted the file after the check to clean up space.  

```bash
hacker@destruction~disk-space-doomsday:~$ yes > yes.txt
yes: standard output: Disk quota exceeded
hacker@destruction~disk-space-doomsday:~$ /challenge/check 
Well done, you clogged the disk. Now free that space (remove the file you created) and run /challenge/check again to prove you cleaned up!
hacker@destruction~disk-space-doomsday:~$ rm yes.txt 
hacker@destruction~disk-space-doomsday:~$ /challenge/check 
Disk space restored. Here is your flag:
pwn.college{cuKmZkbWcrpQpvYNxOGWTF0CQcb.0lMyEzNxwiMxkjNzEzW}
```

## What I learned  
How to fill disk space using the `yes` command and manage files to pass checks.  

## References  
pwn college description  

---

# 3. Hijacking Commands
Wiping the system with a destructive command  
## My solve  
**Flag:** `pwn.college{sRJYgx3QPXaYW2O18ApmSwLDoWW.0lMzEzNxwiMxkjNzEzW}`  
I executed `rm -rf /` to delete everything on the filesystem, rendering the system unusable, but I started `/challenge/check` beforehand to retrieve the flag.  

```bash
acker@destruction~rm-rf-:~$ rm -rf /
/bin/rm: it is dangerous to operate recursively on '/'
/bin/rm: use --no-preserve-root to override this failsafe
hacker@destruction~rm-rf-:~$ rm -rf / --no-preserver-root
/bin/rm: unrecognized option '--no-preserver-root'
Try '/bin/rm --help' for more information.
hacker@destruction~rm-rf-:~$ rm -rf / --no-preserve-root
/bin/rm: skipping '/home/hacker', since it's on a different device
/bin/rm: cannot remove '/etc/resolv.conf': Device or resource busy
/bin/rm: cannot remove '/etc/hostname': Device or resource busy
/bin/rm: cannot remove '/etc/hosts': Device or resource busy
/bin/rm: skipping '/dev', since it's on a different device
/bin/rm: cannot remove '/usr/sbin/docker-init': Device or resource busy
/bin/rm: skipping '/run/dojo/sys', since it's on a different device
/bin/rm: skipping '/sys', since it's on a different device
/bin/rm: skipping '/proc', since it's on a different device
/bin/rm: skipping '/nix', since it's on a different device

hacker@destruction~rm-rf-:~$ /challenge/check 
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
YES! You wiped it, you wild hacker! The flag is yours:
pwn.college{sRJYgx3QPXaYW2O18ApmSwLDoWW.0lMzEzNxwiMxkjNzEzW}

```

## What I learned  
How to use the `rm` command to recursively and forcefully delete all files in a directory.  

## References  
pwn college description  

---

# 4. Life After rm -rf /
Reading files using built-in commands  
## My solve  
**Flag:** `pwn.college{ga2WyxqaMnFetRLJWr6H0K-PjG3.01MzEzNxwiMxkjNzEzW}`  
After executing `rm -rf /`, I utilized the `read` command to retrieve the flag from `/flag`, which had been restored by the challenge script.  

```bash
hacker@destruction~life-after-rm-rf-:~$ rm -rf / --no-preserve-root
/bin/rm: skipping '/home/hacker', since it's on a different device
/bin/rm: cannot remove '/etc/resolv.conf': Device or resource busy
/bin/rm: cannot remove '/etc/hostname': Device or resource busy
/bin/rm: cannot remove '/etc/hosts': Device or resource busy
/bin/rm: skipping '/dev', since it's on a different device
/bin/rm: cannot remove '/usr/sbin/docker-init': Device or resource busy
/bin/rm: skipping '/run/dojo/sys', since it's on a different device
/bin/rm: skipping '/sys', since it's on a different device
/bin/rm: skipping '/proc', since it's on a different device
/bin/rm: skipping '/nix', since it's on a different device


hacker@destruction~life-after-rm-rf-:~$ /challenge/check 
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
YES! You did it again! Go read the flag!
hacker@destruction~life-after-rm-rf-:~$ read FLAG < /flag
hacker@destruction~life-after-rm-rf-:~$ echo $FLAG
pwn.college{ga2WyxqaMnFetRLJWr6H0K-PjG3.01MzEzNxwiMxkjNzEzW}
```

## What I learned  
How to read files using built-in shell commands even after deleting most of the system's files.  

## References  
pwn college description  

---

# 5. Find Meaning After rm -rf /
Locating files without using ls  
## My solve  
**Flag:** `pwn.college{w9KJ-T9HeQs2y6Ih0v_ERlWyNQ2.0FNzEzNxwiMxkjNzEzW}`  
After the `rm -rf /` command, I needed to find the randomly-named flag file that was created. I used `echo *` to list the files without the `ls` command and discovered the flag file.  

```bash

hacker@destruction~finding-meaning-after-rm-rf-:~$ rm -rf / --no-preserve-root
/bin/rm: skipping '/home/hacker', since it's on a different device
/bin/rm: cannot remove '/etc/resolv.conf': Device or resource busy
/bin/rm: cannot remove '/etc/hostname': Device or resource busy
/bin/rm: cannot remove '/etc/hosts': Device or resource busy
/bin/rm: skipping '/dev', since it's on a different device
/bin/rm: cannot remove '/usr/sbin/docker-init': Device or resource busy
/bin/rm: skipping '/run/dojo/sys', since it's on a different device
/bin/rm: skipping '/sys', since it's on a different device
/bin/rm: skipping '/proc', since it's on a different device
/bin/rm: skipping '/nix', since it's on a different device

hacker@destruction~finding-meaning-after-rm-rf-:~$ /challenge/check 
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
Looks like you haven't wiped the system! We'll check again in 5 seconds...
YES! You did it again! Go read the flag!
hacker@destruction~finding-meaning-after-rm-rf-:~$ cd /
hacker@destruction~finding-meaning-after-rm-rf-:/$ echo *
ca8542a0 dev etc home nix proc run sys usr
hacker@destruction~finding-meaning-after-rm-rf-:/$ read FLAG < /ca8542a0 
hacker@destruction~finding-meaning-after-rm-rf-:/$ echo $FLAG
pwn.college{w9KJ-T9HeQs2y6Ih0v_ERlWyNQ2.0FNzEzNxwiMxkjNzEzW}
```

## What I learned  
How to use command line expansion and built-in commands to find files in a directory when typical commands like `ls` are unavailable.  

## References  
pwn college description
