# 1. Learning from Documentation
Using command line arguments based on documentation

## My solve
**Flag:** `pwn.college{kw2fflg73z5SuEKTXyoRvZWo4kb.QX0ITO0wiMxkjNzEzW}`

Ran the program with the required --giveflag argument.

```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{kw2fflg73z5SuEKTXyoRvZWo4kb.QX0ITO0wiMxkjNzEzW}
```

## What I learned
How to use command line arguments specified in program documentation.

## References 
pwn college description

# 2. Learning Complex Usage
Using commands that take arguments to their arguments

## My solve
**Flag:** `pwn.college{gSsIhdhJuCVGkT_5AlhCHyQHgti.QX1ITO0wiMxkjNzEzW}`

Used the program with the --printfile argument, providing the flag file path as an argument to that argument.

```
hacker@man~learning-complex-usage:~$ cd /
hacker@man~learning-complex-usage:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@man~learning-complex-usage:/$ /challenge/challenge --printfile /flag 
Correct argument! Here is the /flag file:
pwn.college{gSsIhdhJuCVGkT_5AlhCHyQHgti.QX1ITO0wiMxkjNzEzW}
```

## What I learned
How to use commands with nested arguments where one argument requires its own parameter.

## References 
pwn college description

# 3. Reading Manuals
Using man pages to discover command options

## My solve
**Flag:** `pwn.college{MT5NIhH4UGCb3QHsOaUgpAmt_dm.QX0EDO0wiMxkjNzEzW}`

Used the man command to read the manual for the challenge program, discovered the secret option, and ran the program with that option.

```
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge --hbsagp 543
Correct usage! Your flag: pwn.college{MT5NIhH4UGCb3QHsOaUgpAmt_dm.QX0EDO0wiMxkjNzEzW}
```

## What I learned
How to use man pages to find command options and documentation.

## References 
pwn college description

# 4. Searching Manuals
Using search functionality within man pages

## My solve
**Flag:** `pwn.college{AJjeILtSObJG0fZkwfMIpg43BBs.QX1EDO0wiMxkjNzEzW}`

Used man to view the challenge documentation, then searched within the man page using / to find the flag-related option.

```
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --ghjtov
Initializing...
Correct usage! Your flag: pwn.college{AJjeILtSObJG0fZkwfMIpg43BBs.QX1EDO0wiMxkjNzEzW}
```

## What I learned
How to search within man pages using /, ?, n, and N to efficiently find information.

## References 
pwn college description

# 5. Searching for Manuals
Finding hidden man pages using the man page database

## My solve
**Flag:** `pwn.college{Yxa7yxmiAZ_sfvc37_wzIpJbocO.QX2EDO0wiMxkjNzEzW}`

Used `man man` to learn how to search the man page database, then used the appropriate search command to find the hidden challenge manual page. After reading the found manual, executed the challenge with the correct option.

```
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man -k flag
dpkg-buildflags (1)  - returns build flags to use during package build
Dpkg::BuildFlags (3perl) - query build flags
fegetexceptflag (3)  - floating-point rounding and exception handling
fesetexceptflag (3)  - floating-point rounding and exception handling
i386 (8)             - change reported architecture in new program environm...
ioctl_iflags (2)     - ioctl() operations for inode flags
linux32 (1)          - change reported architecture in new program environm...
linux64 (1)          - change reported architecture in new program environm...
pcap-config (1)      - write libpcap compiler and linker flags to standard ...
security_compute_av_flags (3) - query the SELinux policy database in the ke...
security_compute_av_flags_raw (3) - query the SELinux policy database in th...
set_matchpathcon_flags (3) - set flags controlling the operation of matchpa...
set_matchpathcon_invalidcon (3) - set flags controlling the operation of ma...
set_matchpathcon_printf (3) - set flags controlling the operation of matchp...
setarch (1)          - change reported architecture in new program environm...
setarch (8)          - change reported architecture in new program environm...
x86_64 (8)           - change reported architecture in new program environm...
xayxmisfvc (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man xayxmisfvc
hacker@man~searching-for-manuals:~$ /challenge/challenge --xayxmi 737
Correct usage! Your flag: pwn.college{Yxa7yxmiAZ_sfvc37_wzIpJbocO.QX2EDO0wiMxkjNzEzW}
```

## What I learned
How to search for man pages using commands like `man -k` or `apropos` when you don't know the exact man page name.

## References 
pwn college description

# 6. Helpful Programs
Using built-in help options for programs without man pages

## My solve
**Flag:** `pwn.college{8jkeFR8Dd3NKkTXFpURrHSKc71W.QX3IDO0wiMxkjNzEzW}`

Ran the challenge program with the --help flag to reveal its usage documentation, then used the appropriate option to get the flag.

```
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v]
                                            [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to
                        give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 883
hacker@man~helpful-programs:~$ /challenge/challenge -g 883
Correct usage! Your flag: pwn.college{8jkeFR8Dd3NKkTXFpURrHSKc71W.QX3IDO0wiMxkjNzEzW}
```

## What I learned
How to access built-in help documentation using --help, -h, or other similar flags when man pages aren't available.

## References 
pwn college description

# 7. Help for Builtins
Using help command to learn about shell built-in commands

## My solve
**Flag:** `pwn.college{Eo8tOoGzjZaa_K2k5UZa4ekR86W.QX0ETO0wiMxkjNzEzW}`

Used the help command to identify the challenge builtin, then ran help on that specific builtin to discover the correct option needed to obtain the flag.

```
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "Eo8tOoGz".
hacker@man~help-for-builtins:~$ challenge --secret Eo8tOoGz
Correct! Here is your flag!
pwn.college{Eo8tOoGzjZaa_K2k5UZa4ekR86W.QX0ETO0wiMxkjNzEzW}
```

## What I learned
How to use the help command to get documentation for shell builtins that don't have man pages.

## References 
pwn college description
