# 1. Launching Screen
Starting a screen session to obtain a flag  
## My solve  
**Flag:** `pwn.college{sULWYXSnPosBeVJ72CQZlwLBfTZ.0VN4IDOxwiMxkjNzEzW}`  
I launched a screen session by simply running the command `screen`, which automatically provided me with the flag upon starting.  

```bash
hacker@terminal-multiplexing~launching-screen:~$ screen
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{sULWYXSnPosBeVJ72CQZlwLBfTZ.0VN4IDOxwiMxkjNzEzW}
```

## What I learned  
How to start a `screen` session to create virtual terminals.  

## References  
pwn college description  

---

# 2. Detaching and Attaching
Using screen's detach and reattach features  
## My solve  
**Flag:** `pwn.college{koEq4YAdf1YSIrqOo_ZvWJuGdPV.0lN4IDOxwiMxkjNzEzW}`  
I launched the `screen` application, performed some work, and then detached from it using `Ctrl-A` followed by `d`. After running `/challenge/run`, I reattached to the session to receive the flag.

```bash
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen
hacker@terminal-multiplexing~detaching-and-attaching:~$
[detached from 155.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run 
Found detached screen session: 155.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{koEq4YAdf1YSIrqOo_ZvWJuGdPV.0lN4IDOxwiMxkjNzEzW}
Yes! Flag is: pwn.college{koEq4YAdf1YSIrqOo_ZvWJuGdPV.0lN4IDOxwiMxkjNzEzW}
```

## What I learned  
How to detach and reattach to `screen` sessions, preserving work in progress.  

## References  
pwn college description  

---

# 3. Finding Sessions
Listing and attaching to specific screen sessions  
## My solve  
**Flag:** `pwn.college{YdYQwLpdvnWJdJfu973f68wMYiG.01N4IDOxwiMxkjNzEzW}`  
I listed the active screen sessions using `screen -ls` and attached to the session containing the flag by using its session identifier.

```bash
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        144.session_da510786abbbd5e7    (Detached)
        147.session_df1bc18db506c4cf    (Detached)
        150.session_aef4af48d78f911b    (Detached)
3 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 144
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{YdYQwLpdvnWJdJfu973f68wMYiG.01N4IDOxwiMxkjNzEzW}
pwn.college{YdYQwLpdvnWJdJfu973f68wMYiG.01N4IDOxwiMxkjNzEzW}
```

## What I learned  
How to list and attach to specific screen sessions when multiple ones are running.  

## References  
pwn college description  

---

# 4. Switching Windows
Navigating between multiple windows in a screen session  
## My solve  
**Flag:** `pwn.college{0XKpgqo4UQhhM-P99FsXY1jD0Ln.0FO4IDOxwiMxkjNzEzW}`  
I attached to my existing screen session and used the appropriate keyboard shortcuts (`Ctrl-A n` and `Ctrl-A p`) to switch between windows, ultimately accessing the one containing the flag.

```bash
hacker@terminal-multiplexing~switching-windows:~$ screen -r

 cat <<MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Welcome to the window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-A 0 to switch to window 0!
> MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
hacker@terminal-multiplexing~switching-windows:~$

hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{0XKpgqo4UQhhM-P99FsXY1jD0Ln.0FO4IDOxwiMxkjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{0XKpgqo4UQhhM-P99FsXY1jD0Ln.0FO4IDOxwiMxkjNzEzW}
```

## What I learned  
How to manage multiple windows within a single screen session efficiently.  

## References  
pwn college description  

---

# 5. Detaching and Attaching (tmux)
Using tmux for terminal multiplexing  
## My solve  
**Flag:** `pwn.college{IvrAin8n64J7G4im6mktiagKhQv.0VO4IDOxwiMxkjNzEzW}`  
I launched a `tmux` session, detached from it with `Ctrl-B d`, and then ran `/challenge/run`. I reattached afterward to receive the flag.

```bash
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a

hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{IvrAin8n64J7G4im6mktiagKhQv.0VO4IDOxwiMxkjNzEzW}
Congratulations, here is your flag: pwn.college{IvrAin8n64J7G4im6mktiagKhQv.0VO4IDOxwiMxkjNzEzW}
```

## What I learned  
How to create and manage tmux sessions for persistent command line work.  

## References  
pwn college description  

---

# 6. Switching Windows (tmux)
Navigating different windows in a tmux session  
## My solve  
**Flag:** `pwn.college{k8ieynVtzRzlJ8x_GBFoZmv3IUt.0FM5IDOxwiMxkjNzEzW}`  
I created a new tmux window, navigated between the existing windows using `Ctrl-B n` and `Ctrl-B p`, and accessed the one with the flag.

```bash
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux a

 cat <<MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Welcome to the tmux window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-B 0 to switch to window 0!
> MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
hacker@terminal-multiplexing~switching-windows-tmux:~$

hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{k8ieynVtzRzlJ8x_GBFoZmv3IUt.0FM5IDOxwiMxkjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{k8ieynVtzRzlJ8x_GBFoZmv3IUt.0FM5IDOxwiMxkjNzEzW}
hacker@terminal-multiplexing~switching-windows-tmux:~$ 
```

## What I learned  
How to switch between multiple windows in a tmux session.  

## References  
pwn college description  

---
