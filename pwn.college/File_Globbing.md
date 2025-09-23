# 1. Matching with *
Using glob patterns with * to create short command arguments

## My solve
**Flag:** `pwn.college{gnFIaCpARPkeD9iPdJ_Q_NU-APx.QXxIDO0wiMxkjNzEzW}`

Used the * wildcard to create a short pattern (4 characters or less) that would match /challenge when changing directories, then ran the program.

```
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run 
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{gnFIaCpARPkeD9iPdJ_Q_NU-APx.QXxIDO0wiMxkjNzEzW}
```

## What I learned
How to use * glob patterns to match multiple filenames or paths with minimal typing.

## References 
pwn college description

# 2. Matching with ?
Using ? glob pattern to match single characters

## My solve
**Flag:** `pwn.college{EM1vHrdg7fJwcTYNi_LikqkCIaX.QXyIDO0wiMxkjNzEzW}`

Used the ? wildcard to replace specific characters in the path to /challenge directory, then ran the program.

```
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{EM1vHrdg7fJwcTYNi_LikqkCIaX.QXyIDO0wiMxkjNzEzW}
```

## What I learned
How to use ? glob patterns to match single characters in filenames or paths.

## References 
pwn college description

# 3. Matching with []
Using bracket globs to match specific characters

## My solve
**Flag:** `pwn.college{A-UboPTQEJP-ksdX1ZApf1bJlLi.QXzIDO0wiMxkjNzEzW}`

Changed to the /challenge/files directory and ran the challenge program with a bracket glob that matched only the specific files needed.

```
hacker@globbing~matching-with-:~$ cd /challenge/files/
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{A-UboPTQEJP-ksdX1ZApf1bJlLi.QXzIDO0wiMxkjNzEzW}
```

## What I learned
How to use bracket globs [] to match only specific characters in filenames.

## References 
pwn college description

# 4. Matching Paths with []
Using bracket globs with absolute paths

## My solve
**Flag:** `pwn.college{cYUiV-IRDDjvEbDu41iLznkMBoI.QX0IDO0wiMxkjNzEzW}`

From the home directory, ran the challenge program with a single argument containing a bracket glob that matched the absolute paths to the specified files.

```
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{cYUiV-IRDDjvEbDu41iLznkMBoI.QX0IDO0wiMxkjNzEzW}
```

## What I learned
How to use bracket globs with absolute paths to match specific files in other directories.

## References 
pwn college description

# 5. Multiple Globs
Using multiple glob patterns in a single argument

## My solve
**Flag:** `pwn.college{AK1qr29Sd0J60mFDm1PLpocx78v.0lM3kjNxwiMxkjNzEzW}`

Changed to the /challenge/files directory and ran the challenge program with a short argument containing two * globs that matched all files containing the letter p.

```
hacker@globbing~multiple-globs:~$ cd /challenge/files/
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{AK1qr29Sd0J60mFDm1PLpocx78v.0lM3kjNxwiMxkjNzEzW}
```

## What I learned
How to combine multiple glob patterns in a single argument to create complex matching patterns.

## References 
pwn college description

# 6. Mixing Globs
Combining different glob pattern techniques

## My solve
**Flag:** `pwn.college{UMrAnP6LmqpAr8NT0YZkgGhnUqv.QX1IDO0wiMxkjNzEzW}`

Changed to the /challenge/files directory and created a short glob pattern (6 characters or less) that matched only the three specified files.

```
hacker@globbing~mixing-globs:~$ cd /challenge/files/
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{UMrAnP6LmqpAr8NT0YZkgGhnUqv.QX1IDO0wiMxkjNzEzW}
```

## What I learned
How to combine different globbing techniques (* wildcards, ? single character wildcards, and [] character sets) to create precise matching patterns.

## References 
pwn college description

# 7. Exclusionary Globbing
Using inverted character classes in glob patterns

## My solve
**Flag:** `pwn.college{0iXke6kEnZBYEW_OFfpwRW3WCaJ.QX2IDO0wiMxkjNzEzW}`

Changed to the /challenge/files directory and ran the challenge program with an exclusionary glob pattern that matched all files not starting with p, w, or n.

```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files/
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{0iXke6kEnZBYEW_OFfpwRW3WCaJ.QX2IDO0wiMxkjNzEzW}
```

## What I learned
How to use inverted character classes with [!...] or [^...] to exclude specific characters from glob matches.

## References 
pwn college description

# 8. Tab Completion
Using tab completion to handle difficult filenames

## My solve
**Flag:** `pwn.college{IZxOgMKCOKnRKh3M_AQreH0AW0p.0FN0EzNxwiMxkjNzEzW}`

Used tab completion to correctly access a file with a tricky name that couldn't be typed directly.

```
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege 
pwn.college{IZxOgMKCOKnRKh3M_AQreH0AW0p.0FN0EzNxwiMxkjNzEzW}
```

## What I learned
How to use tab completion as a safer alternative to globbing when dealing with unusual filenames.

## References 
pwn college description

# 9. Multiple Options for Tab Completion
Using tab completion with multiple matching files

## My solve
**Flag:** `pwn.college{0TppJ-xUFWKQ6ynIHX9a9fXZrrq.0lN0EzNxwiMxkjNzEzW}`

Navigated to the /challenge/files directory and used tab completion starting with "p" to see the available files. Used multiple tab presses to view options and complete the path to the correct pwncollege file.

```
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag
pwn.college{0TppJ-xUFWKQ6ynIHX9a9fXZrrq.0lN0EzNxwiMxkjNzEzW}
```

## What I learned
How tab completion behaves with multiple matching files, showing common prefixes and listing all options on subsequent tab presses.

## References 
pwn college description

# 10. Tab Completion on Commands
Using tab completion to find and run commands

## My solve
**Flag:** `pwn.college{ot_gRLbtGzYgHkK0X9XiDFXYtvS.0VN0EzNxwiMxkjNzEzW}`

Typed "pwncollege" and used tab completion to discover and auto-complete the full command name, then executed it to get the flag.

```
hacker@globbing~tab-completion-on-commands:~$ pwncollege-25936 
Correct! Here is your flag:
pwn.college{ot_gRLbtGzYgHkK0X9XiDFXYtvS.0VN0EzNxwiMxkjNzEzW}
```

## What I learned
How to use tab completion for commands in addition to files, making it easier to discover and run available commands.

## References 
pwn college description
