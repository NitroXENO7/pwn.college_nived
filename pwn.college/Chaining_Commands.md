# 1. Chaining with Semicolons
Chaining commands using the semicolon operator  
## My solve  
**Flag:** `pwn.college{UB7UAIf8ir6EempOO8zfVzPrNw3.QX1UDO0wiMxkjNzEzW}`  
In this challenge, I needed to run the programs `/challenge/pwn` and `/challenge/college`, chaining them with a semicolon. This allowed both commands to execute in succession.

```bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college 
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{UB7UAIf8ir6EempOO8zfVzPrNw3.QX1UDO0wiMxkjNzEzW}
```

## What I learned  
How to use the semicolon operator to chain multiple commands in the shell.

## References  
pwn college description  

---

# 2. Building on Success
Using the `&&` operator to chain commands based on success  
## My solve  
**Flag:** `pwn.college{Q3M49XSN1oIxDH8en9lOV2JdvhV.0lM0MDOxwiMxkjNzEzW}`  
In this challenge, I was required to chain the programs `/challenge/first-success` and `/challenge/second` using the `&&` operator. This ensured that the second command only ran if the first command succeeded.

```bash
hacker@chaining~building-on-success:~$ /challenge/first-success 
hacker@chaining~building-on-success:~$ /challenge/second 
Error: /challenge/first-success must be successfully chained with 
/challenge/second using &&
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second 
Nice chaining! Flag: pwn.college{Q3M49XSN1oIxDH8en9lOV2JdvhV.0lM0MDOxwiMxkjNzEzW}
```

## What I learned  
How to use the `&&` operator to conditionally execute a command based on the success of the previous command.  

## References  
pwn college description  

---

# 3. Handling Failure
Using the `||` operator to chain commands based on failure  
## My solve  
**Flag:** `pwn.college{EFD3pVzxSpLUPDUNS4AmzejNBFd.01M0MDOxwiMxkjNzEzW}`  
In this challenge, I needed to chain the commands `/challenge/first-failure` and `/challenge/second` using the `||` operator. This allowed the second command to run only if the first command failed.

```bash
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second 
Nice chaining! Flag: pwn.college{EFD3pVzxSpLUPDUNS4AmzejNBFd.01M0MDOxwiMxkjNzEzW}
```

## What I learned  
How to use the `||` operator to conditionally execute a command based on the failure of the previous command.

## References  
pwn college description  

---

# 4. Your First Shell Script
Creating a shell script to execute multiple commands  
## My solve  
**Flag:** `pwn.college{MtiR4yYRVxqMMu4rArPDURm-JF2.QXxcDO0wiMxkjNzEzW}`  
In this challenge, I created a shell script called `x.sh` containing the commands to run `/challenge/pwn` and `/challenge/college`. I then executed the script using `bash`.  

```bash
hacker@chaining~your-first-shell-script:~$ nano x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{MtiR4yYRVxqMMu4rArPDURm-JF2.QXxcDO0wiMxkjNzEzW}
```

## What I learned  
How to create and run a shell script to execute multiple commands sequentially.  

## References  
pwn college description  

---

# 5. Redirecting Script Output
Piping output from a shell script to another program  
## My solve  
**Flag:** `pwn.college{AwLC358qYUr2wRILf2mGvktkb4O.QX4ETO0wiMxkjNzEzW}`  
I created a shell script that called the `/challenge/pwn` command followed by the `/challenge/college` command, and piped the output into the `/challenge/solve` command.  

```bash
hacker@chaining~redirecting-script-output:~$ nano x.sh
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve 
Correct! Here is your flag:
pwn.college{AwLC358qYUr2wRILf2mGvktkb4O.QX4ETO0wiMxkjNzEzW}
```

## What I learned  
How to redirect output from a script to another program using pipes.  

## References  
pwn college description  

---

# 6. Executable Shell Scripts
Making a shell script executable and running it directly  
## My solve  
**Flag:** `pwn.college{kdCDXpCgDFViNx5LFe299Fb7p21.QX0cjM1wiMxkjNzEzW}`  
I created a shell script named `x.sh` with a proper shebang. After making it executable, I ran it directly without invoking `bash`.  

```bash
hacker@chaining~executable-shell-scripts:~$ nano x.sh
hacker@chaining~executable-shell-scripts:~$ chmod +x x.sh
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{kdCDXpCgDFViNx5LFe299Fb7p21.QX0cjM1wiMxkjNzEzW}
```

## What I learned  
How to create an executable shell script that can be run directly from the terminal.  

## References  
pwn college description  

---

# 7. Understanding Shebangs
Using shebangs to specify script interpreters  
## My solve  
**Flag:** `pwn.college{4GoG9_i8Km6PS1UvCXG0IKjdHxU.0VOzMDOxwiMxkjNzEzW}`  
I created a shell script at `/home/hacker/solve.sh` that includes a shebang (`#!/bin/bash`) and outputs "hack the planet". I made it executable and verified it worked correctly.  

```bash
hacker@chaining~understanding-shebangs:~$ nano solve.sh
hacker@chaining~understanding-shebangs:~$ chmod +x solve.sh 
hacker@chaining~understanding-shebangs:~$ ./solve.sh 
hack the planet
hacker@chaining~understanding-shebangs:~$ /challenge/run 
Testing your script...
Perfect! Your flag:
Flag: pwn.college{4GoG9_i8Km6PS1UvCXG0IKjdHxU.0VOzMDOxwiMxkjNzEzW}
```

## What I learned  
The purpose of the shebang (`#!`) in a script and how it specifies which interpreter to use.  

## References  
pwn college description  

---

# 8. Scripting with Arguments
Passing arguments to a shell script  
## My solve  
**Flag:** `pwn.college{sKXO1L-S4Wyi8KUnZMqCNdVMYYh.0VNzMDOxwiMxkjNzEzW}`  
I wrote a script at `/home/hacker/solve.sh` that takes two arguments and outputs them in reverse order. After testing it, I confirmed it provided the correct outputs.  

```bash
hacker@chaining~scripting-with-arguments:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ ./solve.sh world hello
hello world
hacker@chaining~scripting-with-arguments:~$ /challenge/run 
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{sKXO1L-S4Wyi8KUnZMqCNdVMYYh.0VNzMDOxwiMxkjNzEzW}
```

## What I learned  
How to access and use command-line arguments within a shell script.  

## References  
pwn college description  

---

# 9. Scripting with Conditionals
Using `if` statements in shell scripts  
## My solve  
**Flag:** `pwn.college{smU9bZhEiiWYz-sR7lwKc8hw0o5.0lNzMDOxwiMxkjNzEzW}`  
I created a script at `/home/hacker/solve.sh` that takes one argument and outputs "college" if the argument is "pwn". It outputs nothing for any other input.  

```bash
hacker@chaining~scripting-with-conditionals:~$ nano solve.sh 
hacker@chaining~scripting-with-conditionals:~$ ./solve.sh pwn
college
hacker@chaining~scripting-with-conditionals:~$ /challenge/run 
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{smU9bZhEiiWYz-sR7lwKc8hw0o5.0lNzMDOxwiMxkjNzEzW}
```

## What I learned  
How to implement conditional logic using `if` statements in shell scripts.  

## References  
pwn college description  

---

# 10. Scripting with Default Cases
Implementing `else` in shell scripts  
## My solve  
**Flag:** `pwn.college{Uw3_3oGmk7iHcXSoAbU1vsibCMn.01NzMDOxwiMxkjNzEzW}`  
I wrote a script at `/home/hacker/solve.sh` that checks for the argument "pwn" and outputs "college"; otherwise, it outputs "nope".  

```bash
hacker@chaining~scripting-with-default-cases:~$ nano solve.sh 
hacker@chaining~scripting-with-default-cases:~$ ./solve.sh pwn
college
hacker@chaining~scripting-with-default-cases:~$ ./solve.sh else
nope
hacker@chaining~scripting-with-default-cases:~$ /challenge/run 
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{Uw3_3oGmk7iHcXSoAbU1vsibCMn.01NzMDOxwiMxkjNzEzW}
```

## What I learned  
How to use `else` to provide default actions in conditional statements.  

## References  
pwn college description  

---

# 11. Scripting with Multiple Conditions
Using `elif` for multiple conditions  
## My solve  
**Flag:** `pwn.college{wvJIMmv1Q3i-hurOAzSX8_jHAt9.0FOzMDOxwiMxkjNzEzW}`  
I created a script at `/home/hacker/solve.sh` that checks multiple arguments and outputs relevant responses for each known input while falling back to "unknown" for anything else.  

```bash
hacker@chaining~scripting-with-multiple-conditions:~$ nano solve.sh 
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run 
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{wvJIMmv1Q3i-hurOAzSX8_jHAt9.0FOzMDOxwiMxkjNzEzW}
```

## What I learned  
How to chain multiple conditional checks using `if`, `elif`, and `else`.  

## References  
pwn college description  

---

# 12. Reading Shell Scripts
Reading and understanding a shell script's contents  
## My solve  
**Flag:** `pwn.college{0PCBUoRWsldU77Slm_yIimJMCfO.0lMwgDOxwiMxkjNzEzW}`  
I read the contents of the `/challenge/run` shell script to find the hardcoded password necessary to obtain the flag.  

```bash
hacker@chaining~reading-shell-scripts:~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /challenge/run 
hack the PLANET
CORRECT! Your flag:
pwn.college{0PCBUoRWsldU77Slm_yIimJMCfO.0lMwgDOxwiMxkjNzEzW}
```

## What I learned  
How to read and understand shell scripts to extract information directly from them.  

## References  
pwn college description
