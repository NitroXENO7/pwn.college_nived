# 1. Redirecting Output
Using redirection operators to save command output to files

## My solve
**Flag:** `pwn.college{YdNLZGZ0MAaGvFK9IrJ_aB-2YX-.QX0YTN0wiMxkjNzEzW}`

Used the output redirection operator to write "PWN" to a file named "COLLEGE".

```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{YdNLZGZ0MAaGvFK9IrJ_aB-2YX-.QX0YTN0wiMxkjNzEzW}
```

## What I learned
How to redirect command output to files using the > operator.

## References 
pwn college description

# 2. Redirecting More Output
Redirecting program output to a file while still seeing feedback

## My solve
**Flag:** `pwn.college{M4Wh7t391PHB1ygz3CCiryRHpHW.QX1YTN0wiMxkjNzEzW}`

Ran the challenge program while redirecting its output to the required file, allowing the program's status messages to still display on screen.

```
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{M4Wh7t391PHB1ygz3CCiryRHpHW.QX1YTN0wiMxkjNzEzW}
```

## What I learned
How to redirect command output to files while still seeing feedback messages that are sent to stderr.

## References 
pwn college description

# 3. Appending Output
Using append-mode redirection to collect complete output

## My solve
**Flag:** `pwn.college{kSYY6lzT_QXPxVKd-P0suesCieh.QX3ATO0wiMxkjNzEzW}`

Used the append-mode redirection operator to save the challenge program's output to the specified file without overwriting previous content.

```
hacker@piping~appending-output:~$ /challenge/run >> ~/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat ~/the-flag 
 | 
\|/ This is the first half:
 v 
pwn.college{kSYY6lzT_QXPxVKd-P0suesCieh.QX3ATO0wiMxkjNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
```

## What I learned
How to use the >> operator to append command output to files rather than overwriting them.

## References 
pwn college description

# 4. Redirecting Errors
Using file descriptor redirection to capture error output

## My solve
**Flag:** `pwn.college{4McZsUEZ1SKvlcMIZrYTnf9cJXn.QX3YTN0wiMxkjNzEzW}`

Ran the challenge program while redirecting both standard output to myflag and standard error to instructions files.

```
hacker@piping~redirecting-errors:~$ /challenge/run 1> myflag 2>instructions
hacker@piping~redirecting-errors:~$ cat instructions 
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[PASS] The file at the other end of my stderr looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-errors:~$ cat myflag 

[FLAG] Here is your flag:
[FLAG] pwn.college{4McZsUEZ1SKvlcMIZrYTnf9cJXn.QX3YTN0wiMxkjNzEzW}
```

## What I learned
How to use file descriptor numbers to redirect specific output streams (stdout and stderr) to different files.

## References 
pwn college description

# 5. Redirecting Input
Using input redirection to provide file content to programs

## My solve
**Flag:** `pwn.college{gsirGZ-Hkn8eDakfDSuLt23fgLk.QXwcTN0wiMxkjNzEzW}`

Created a file named PWN containing the text COLLEGE, then used input redirection to feed this file to the challenge program.

```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{gsirGZ-Hkn8eDakfDSuLt23fgLk.QXwcTN0wiMxkjNzEzW}
```

## What I learned
How to redirect file content as input to programs using the < operator.

## References 
pwn college description

# 6. Grepping Stored Results
Using redirection and grep to find information in large output

## My solve
**Flag:** `pwn.college{8nVwj5I9gWfC_mKN8m_IJXPTpKv.QX4EDO0wiMxkjNzEzW}`

Redirected the output of the challenge program to a temporary file, then used grep to search through the large file to locate the flag.

```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{8nVwj5I9gWfC_mKN8m_IJXPTpKv.QX4EDO0wiMxkjNzEzW}
```

## What I learned
How to combine output redirection with grep to efficiently search through large command outputs.

## References 
pwn college description

# 7. Grepping Live Output
Using pipes to directly search command output

## My solve
**Flag:** `pwn.college{8iUcYAUcY0pQrVPwUKoxQ4AWFlm.QX5EDO0wiMxkjNzEzW}`

Used a pipe to directly connect the output of the challenge program to grep, allowing for immediate filtering of the large output.

```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{8iUcYAUcY0pQrVPwUKoxQ4AWFlm.QX5EDO0wiMxkjNzEzW}
```

## What I learned
How to use the pipe operator (|) to connect commands, sending the output of one command directly to another without temporary files.

## References 
pwn college description

# 8. Grepping Errors
Using redirection to search through error output

## My solve
**Flag:** `pwn.college{oN2Fu0BhxeFFVQPptqmkm62KruO.QX1ATO0wiMxkjNzEzW}`

Used file descriptor redirection to redirect stderr to stdout, then piped the combined output to grep to find the flag.

```
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{oN2Fu0BhxeFFVQPptqmkm62KruO.QX1ATO0wiMxkjNzEzW}
```

## What I learned
How to use the 2>&1 redirection to combine stderr with stdout, allowing for piping error messages to other commands.

## References 
pwn college description

# 9. Filtering with grep -v
Using inverted pattern matching to exclude unwanted output

## My solve
**Flag:** `pwn.college{8tAU9ihcmTM4LShLu2dnsJCambJ.0FOxEzNxwiMxkjNzEzW}`

Used grep with the -v option to filter out all decoy flags from the challenge program's output, revealing only the real flag.

```
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v DECOY
pwn.college{8tAU9ihcmTM4LShLu2dnsJCambJ.0FOxEzNxwiMxkjNzEzW}
```

## What I learned
How to use grep -v to invert pattern matching, showing only lines that don't match a specific pattern.

## References 
pwn college description

# 10. Duplicate Piped Data with tee
Using tee to inspect data flowing through pipes

## My solve
**Flag:** `pwn.college{sgbRQ3w32udkXsyMXPY2p0OsEww.QXxITO0wiMxkjNzEzW}`

Used the tee command to inspect data being piped from /challenge/pwn to /challenge/college, allowing me to see the requirements needed to successfully complete the challenge.

```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee data | /challenge/college 
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat data
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "sgbRQ3w3"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret sgbRQ3w3 | /challenge/college 
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{sgbRQ3w32udkXsyMXPY2p0OsEww.QXxITO0wiMxkjNzEzW}
```

## What I learned
How to use tee to duplicate and inspect data flowing through pipes without interrupting the pipeline.

## References 
pwn college description

# 11. Process Substitution for Input
Using process substitution to compare command outputs

## My solve
**Flag:** `pwn.college{8Qw2G8YZb2_gYTv_0FA116Nvu3u.0lNwMDOxwiMxkjNzEzW}`

Used process substitution with diff to compare the outputs of two commands, revealing the flag that was only present in one of them.

```
hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
13a14
> pwn.college{8Qw2G8YZb2_gYTv_0FA116Nvu3u.0lNwMDOxwiMxkjNzEzW}
```

## What I learned
How to use process substitution (<(command)) to treat command output as a file for comparison with tools like diff.

## References 
pwn college description

# 12. Writing to Multiple Programs
Using process substitution for output to multiple commands

## My solve
**Flag:** `pwn.college{Yfhy3aCmZaoaFoPFKWHndILelxt.QXwgDN1wiMxkjNzEzW}`

Used tee with output process substitution to send the output of one command as input to multiple other commands simultaneously.

```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/planet)  >(/challenge/the)
This secret data must directly and simultaneously make it to /challenge/the and 
/challenge/planet. Don't try to copy-paste it; it changes too fast.
721128324226532992
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{Yfhy3aCmZaoaFoPFKWHndILelxt.QXwgDN1wiMxkjNzEzW}
```

## What I learned
How to use output process substitution (>(command)) with tee to send a command's output to multiple commands at once.

## References 
pwn college description

# 13. Split-Piping stderr and stdout
Redirecting stdout and stderr to different programs

## My solve
**Flag:** `pwn.college{MstGC0C5GnxbDTbG6Zaktqos3s6.QXxQDM2wiMxkjNzEzW}`

Used a combination of process substitution and redirection to send the challenge program's stdout and stderr to two different programs.

```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) | /challenge/planet
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{MstGC0C5GnxbDTbG6Zaktqos3s6.QXxQDM2wiMxkjNzEzW}
```

## What I learned
How to redirect stdout and stderr from one program to different destination programs using a combination of process substitution and redirection operators.

## References 
pwn college description

# 14. Named Pipes
Creating and using persistent named pipes (FIFOs)

## My solve
**Flag:** `pwn.college{Ui5_zlP-hRGhNMrq2U5lor2ysfp.01MzMDOxwiMxkjNzEzW}`

Created a named pipe using mkfifo, then redirected the challenge program's output to it. Used a second terminal to read from the pipe and retrieve the flag.

```
hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo 
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo! 
Bash will now try to open the FIFO for writing, to pass it as the stdout of 
/challenge/run. Recall that operations on FIFOs will *block* until both the 
read side and the write side is open, so /challenge/run will not actually be 
launched until you start reading from the FIFO!

hacker@piping~named-pipes:~$ cat /tmp/flag_fifo
You've correctly redirected /challenge/run's stdout to a FIFO at 
/tmp/flag_fifo! Here is your flag:
pwn.college{Ui5_zlP-hRGhNMrq2U5lor2ysfp.01MzMDOxwiMxkjNzEzW}
```

## What I learned
How to create and use named pipes (FIFOs) for inter-process communication without temporary files.

## References 
pwn college description
