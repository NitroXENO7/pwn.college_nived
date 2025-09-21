# The Root
invoke a program in root directory

## My solve
**Flag:** `pwn.college{M17_5Cdd3lJXhjC4cRKEm0yto8l.QX4cTO0wiMxkjNzEzW}`

Invoked the the program pwn by typing /pwn

```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{M17_5Cdd3lJXhjC4cRKEm0yto8l.QX4cTO0wiMxkjNzEzW}
```

## What I learned
Invoking programs with absolute path

## References 
pwn college description

# Programs and absolute paths
Invoke a program inside a folder called challenge

## My solve
**Flag:** `pwn.college{Q-u4PvQDo3KeGhKYVpHV0y8ML54.QX1QTN0wiMxkjNzEzW}`

invoked the program by typing in /challenge/run

```
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{Q-u4PvQDo3KeGhKYVpHV0y8ML54.QX1QTN0wiMxkjNzEzW}
```

## What I learned
How to invoke programs in folders using absolute paths

## References 
pwn college description

# Position thy self
cd into a specific folder and then run the program 'run'

## My solve
**Flag:** `pwn.college{A3m_7xpfki_UgxIdpX8w-EPdCqj.QX2QTN0wiMxkjNzEzW}`

I cd'd into the challenge folder and ran 'run' program which then asked me to cd into /etc/apt/sources.list.d folder and run it again, which i did and then i got the flag.

```
hacker@paths~position-thy-self:/$ cd challenge/
hacker@paths~position-thy-self:/challenge$ run
bash: run: command not found
hacker@paths~position-thy-self:/challenge$ ./run
Incorrect...
You are not currently in the /etc/apt/sources.list.d directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:/challenge$ cd /etc/ap
apache2/    apparmor.d/ apport/     apt/        
hacker@paths~position-thy-self:/challenge$ cd /etc/apt/sources.list.d
hacker@paths~position-thy-self:/etc/apt/sources.list.d$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{A3m_7xpfki_UgxIdpX8w-EPdCqj.QX2QTN0wiMxkjNzEzW}
```

## What I learned
how to cd into specific folders and run programs from other folders using absolute paths

## References 
pwn college description

# Position elsewhere
cd into a specific folder and then run the program 'run'

## My solve
**Flag:** `pwn.college{o_ts16RHk4EdaE9YnVLJIoZjL1U.QX3QTN0wiMxkjNzEzW}`


I cd'd into the challenge folder and ran 'run' program which then asked me to cd into /etc/apt/sources.list.d folder and run it again, which i did and then i got the flag.
```
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /etc/apt/sources.list.d directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /etc/apt/sources.list.d
hacker@paths~position-elsewhere:/etc/apt/sources.list.d$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{o_ts16RHk4EdaE9YnVLJIoZjL1U.QX3QTN0wiMxkjNzEzW}
```

## What I learned
how to cd into specific folders and run programs from other folders using absolute paths

## References 
pwn college description

# Position yet elsewhere
cd into a specific folder and then run the program 'run'

## My solve
**Flag:** `pwn.college{gkMns3IRIRsx4ucODvqeZEmL5w3.QX4QTN0wiMxkjNzEzW}`

I cd'd into the challenge folder and ran 'run' program which then asked me to cd into /usr/include folder and run it again, which i did and then i got the flag.

```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/include directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /usr/include/
hacker@paths~position-yet-elsewhere:/usr/include$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{gkMns3IRIRsx4ucODvqeZEmL5w3.QX4QTN0wiMxkjNzEzW}
```

## What I learned
how to cd into specific folders and run programs from other folders using absolute paths

## References 
pwn college description

# implicit relative paths, from /
use relative paths instead of absolute paths to run programs

## My solve
**Flag:** `pwn.college{0a8s-gdaCbUvQDdCkkAlZfXwEgm.QX5QTN0wiMxkjNzEzW}`

cd'd into root then ran challenge/run

```
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{0a8s-gdaCbUvQDdCkkAlZfXwEgm.QX5QTN0wiMxkjNzEzW}
```

## What I learned
run programs from specific directory with relative paths 

## References 
pwn college description

# explicit relative paths, from /
using . as a reference to current directory

## My solve
**Flag:** `pwn.college{QZuhlZVlLM8ADA2aX94I0w6QFpt.QXwUTN0wiMxkjNzEzW}`

cd'd into root then invoked ./challenge/run
```
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{QZuhlZVlLM8ADA2aX94I0w6QFpt.QXwUTN0wiMxkjNzEzW}
```

## What I learned
use . as the current directory

## References 
pwn college description

# implicit relative path
more in depth with relative paths

## My solve
**Flag:** `pwn.college{UkZmp2hKWas3yAg70x9K2D3Q8lz.QXxUTN0wiMxkjNzEzW}`

cd'd into /challenge then ran 'run' with ./run which is a relative path
```
hacker@paths~implicit-relative-path:~$ cd /challenge/
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{UkZmp2hKWas3yAg70x9K2D3Q8lz.QXxUTN0wiMxkjNzEzW}
```

## What I learned
running programs with relative paths

## References 
pwn college description

# home sweet home
run program with an argument of a relative path of a file , the argument should be less than 3 char long

## My solve
**Flag:** `pwn.college{kDcIAZp3QFeJVk6_lEvbtyD_QVx.QXzMDO0wiMxkjNzEzW}`

ran /challenge/run with an argument of '~/f' which specifies /home/hacker/f where 'f' is the name of the file
```
hacker@paths~home-sweet-home:~$ /challenge/run ~/f
Writing the file to /home/hacker/f!
... and reading it back to you:
pwn.college{kDcIAZp3QFeJVk6_lEvbtyD_QVx.QXzMDO0wiMxkjNzEzW}
```

## What I learned
using ~ as a shortened absolute path to home directory

## References 
pwn college description
