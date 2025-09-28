# 1. The PATH Variable
Disrupting the command execution by manipulating the PATH variable  
## My solve  
**Flag:** `pwn.college{Mx2V6qc4gEW_RMeihRxM46ivALX.QX2cDM1wiMxkjNzEzW}`  
In this challenge, I blanked out the `$PATH` variable to prevent the `/challenge/run` program from finding the `rm` command. This allowed me to stop the program from deleting the flag file.  

```bash
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run 
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{Mx2V6qc4gEW_RMeihRxM46ivALX.QX2cDM1wiMxkjNzEzW}
```

## What I learned  
How to use the `$PATH` variable to control where the shell looks for executables and disrupt their normal operation.  

## References  
pwn college description  

---

# 2. Setting PATH
Adding a new directory to the PATH variable  
## My solve  
**Flag:** `pwn.college{UhW9b3XJ05aBd6VDZGZU7YwN23q.QX1cjM1wiMxkjNzEzW}`  
I set the `$PATH` variable to include `/challenge/more_commands`, which allowed the `/challenge/run` to find the `win` command that I needed to execute to get the flag.  

```bash
hacker@path~setting-path:~$ PATH="/challenge/more_commands/"
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{UhW9b3XJ05aBd6VDZGZU7YwN23q.QX1cjM1wiMxkjNzEzW}
```

## What I learned  
How to modify the `$PATH` variable to include custom directories for command execution.  

## References  
pwn college description  

---

# 3. Finding Commands
Using the `which` command to locate executable files  
## My solve  
**Flag:** `[pwn.college{shegj89jawnwJoUdAgGGOMDTO-j.01NzEzNxwiMxkjNzEzW}`  
I used the `which` command to find the `win` command in the provided path, allowing me to confirm its location and then access the flag file.  

```bash
hacker@path~finding-commands:~$ which win
/challenge/paths/22202/win
hacker@path~finding-commands:~$ cat /challenge/paths/22202/flag
pwn.college{shegj89jawnwJoUdAgGGOMDTO-j.01NzEzNxwiMxkjNzEzW}
```

## What I learned  
How to use the `which` command to locate the actual file of a command based on the current `$PATH`.  

## References  
pwn college description  

---

# 4. Adding Commands
Creating a script to add custom commands to the PATH  
## My solve  
**Flag:** `pwn.college{E9oUi_1dOHPe_DS3tYbrp-8EXuk.QX2cjM1wiMxkjNzEzW}`  
I created a shell script called `win`, which was placed in the `/challenge/more_commands` directory. This allowed it to be executed by the `/challenge/run` script properly.  

```bash
hacker@path~adding-commands:~$ which cat
/run/dojo/bin/cat
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ chmod +x win
hacker@path~adding-commands:~$ PATH="~"
hacker@path~adding-commands:~$ /challenge/run 
Invoking 'win'....
pwn.college{E9oUi_1dOHPe_DS3tYbrp-8EXuk.QX2cjM1wiMxkjNzEzW}
```

## What I learned  
How to create a custom command in a shell script and ensure it can be executed from another command.  

## References  
pwn college description  

---

# 5. Hijacking Commands
Creating a command that prevents the flag from being deleted  
## My solve  
**Flag:** `pwn.college{Ya_vWjJLEiUHE3Fp3uboc3ZRn0Z.QX3cjM1wiMxkjNzEzW}`  
I created a command that would override the `rm` command, ensuring it would not remove the flag file when executed by `/challenge/run`.  

```bash
hacker@path~hijacking-commands:~$ nano rm
hacker@path~hijacking-commands:~$ chmod +x rm
hacker@path~hijacking-commands:~$ PATH="~"
hacker@path~hijacking-commands:~$ /challenge/run 
Trying to remove /flag...
pwn.college{Ya_vWjJLEiUHE3Fp3uboc3ZRn0Z.QX3cjM1wiMxkjNzEzW}
```

## What I learned  
How to effectively create scripts that can replace or control existing commands in the shell environment.  

## References  
pwn college description
