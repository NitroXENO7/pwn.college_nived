# 1. Printing Variables
Displaying environment variables in the shell

## My solve
**Flag:** `pwn.college{sjLymJcwuXF32LIswJ39uhVx5Gg.QX3UTN0wiMxkjNzEzW}`

Used echo with the $ syntax to print the value of the FLAG environment variable.

```
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{sjLymJcwuXF32LIswJ39uhVx5Gg.QX3UTN0wiMxkjNzEzW}
```

## What I learned
How to display the values of environment variables using the $ prefix with echo.

## References 
pwn college description

# 2. Setting Variables
Creating and assigning values to shell variables

## My solve
**Flag:** `pwn.college{oP6qHfBpsXUzbKy1iSnrOrG1B3B.QX5UTN0wiMxkjNzEzW}`

Set the PWN variable to COLLEGE using the proper variable assignment syntax.

```
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{oP6qHfBpsXUzbKy1iSnrOrG1B3B.QX5UTN0wiMxkjNzEzW}
```

## What I learned
How to create and set shell variables using the assignment operator without spaces.

## References 
pwn college description

# 3. Multi-word Variables
Setting variables with values containing spaces

## My solve
**Flag:** `pwn.college{c_lhqgbuGLtug5070V52TEqim7o.QXwYTN0wiMxkjNzEzW}`

Set the PWN variable to "COLLEGE YEAH" using quotes to preserve the space in the value.

```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{c_lhqgbuGLtug5070V52TEqim7o.QXwYTN0wiMxkjNzEzW}
```

## What I learned
How to use quotes when assigning values with spaces to variables.

## References 
pwn college description

# 4. Exporting Variables
Making variables available to child processes

## My solve
**Flag:** `pwn.college{kZGFlQBDiRMfs0SYGI0G9MypE6l.QXyYTN0wiMxkjNzEzW}`

Set and exported PWN variable to COLLEGE, while setting COLLEGE variable to PWN without exporting it, then ran the challenge program.

```
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run 
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{kZGFlQBDiRMfs0SYGI0G9MypE6l.QXyYTN0wiMxkjNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```

## What I learned
How to use export to make variables available to child processes, and how variables remain local to the shell when not exported.

## References 
pwn college description

# 5. Printing Exported Variables
Using the env command to view environment variables

## My solve
**Flag:** `pwn.college{kMuU8_Sgh9VsZ-X9Z-Rbu5UTx7r.QX4UTN0wiMxkjNzEzW}`

Used the env command to display all exported environment variables, then located the FLAG variable in the output.

```
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=0ef381edb0e1eda53c69bb7939f242d66fd384a95b8abcb3542296640ea98b26
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{kMuU8_Sgh9VsZ-X9Z-Rbu5UTx7r.QX4UTN0wiMxkjNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env
```

## What I learned
How to use the env command to list all exported environment variables in the shell.

## References 
pwn college description

# 6. Storing Command Output
Using command substitution to capture command output in variables

## My solve
**Flag:** `pwn.college{02sp3EdKH6fy2GcrVTJg2O0PuZq.QX1cDN1wiMxkjNzEzW}`

Used command substitution to store the output of the challenge program in a variable, then displayed the variable.

```
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{02sp3EdKH6fy2GcrVTJg2O0PuZq.QX1cDN1wiMxkjNzEzW}
```

## What I learned
How to use command substitution with $() to capture command output into variables.

## References 
pwn college description

# 7. Reading Input
Using the read command to get user input into variables

## My solve
**Flag:** `pwn.college{kg7DUulFCMPeHlI3u7jt6UnSqaw.QX4cTN0wiMxkjNzEzW}`

Used the read command to set the PWN variable by typing COLLEGE when prompted.

```
hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{kg7DUulFCMPeHlI3u7jt6UnSqaw.QX4cTN0wiMxkjNzEzW}
```

## What I learned
How to use the read command to get user input and store it in shell variables.

## References 
pwn college description

# 8. Reading Files
Using read with redirection to get file content into variables

## My solve
**Flag:** `pwn.college{wyeqa_hZaAzjn0lkHXGHjcbESkI.QXwIDO0wiMxkjNzEzW}`

Used the read command with input redirection to read the content of the challenge file directly into a variable.

```
hacker@variables~reading-files:~$ read PWN < /challenge/read_me 
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wyeqa_hZaAzjn0lkHXGHjcbESkI.QXwIDO0wiMxkjNzEzW}
```

## What I learned
How to read file content directly into variables using read with input redirection, avoiding unnecessary use of cat.

## References 
pwn college description
