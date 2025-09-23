# Level 0
Connect to the game server using SSH

## My solve
Connected to the server using SSH with the provided credentials.

```
ssh -p 2220 bandit0@bandit.labs.overthewire.org
```

## What I learned
How to use SSH to connect to a remote server using a specific port.

## References 
- Secure Shell (SSH) on Wikipedia
- How to use SSH with a non-standard port on It's FOSS
- How to use SSH with ssh-keys on wikiHow

# Level 0 → Level 1
Find and read a file to get the password for the next level

## My solve
Connected to bandit0 via SSH, then used ls to list files in the home directory and found the readme file. Used cat to read the file contents, revealing the password for the next level.

```
bandit0@bandit:~$ cat readme
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

## What I learned
How to list files and read file contents in Linux using basic commands.

## References 
- ls (list directory contents)
- cat (concatenate and display file content)

# Level 1 → Level 2
Access a file with a dash as its name

## My solve
After connecting to bandit1, I found a file named "-" in the home directory. Since this is a special character in the shell, I needed a special approach to read it.

Used `cat ./-` to read the file, which specified the relative path to avoid treating the dash as standard input.

```
bandit1@bandit:~$ ls
-
bandit1@bandit:~$ cat ./-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

## What I learned
How to handle files with special characters like dash in their names, which normally have special meaning to the shell.

## References 
- Google Search for "dashed filename"
- Advanced Bash-scripting Guide - Chapter 3 - Special Characters

# Level 2 → Level 3
Access a file with spaces in its filename

## My solve
Connected to bandit2 and found a file with spaces in its name. Used quotes or backslashes to properly handle the spaces when accessing the file.

```
bandit2@bandit:~$ ls
--spaces in this filename--
bandit2@bandit:~$ cat ./--spaces\ in\ this\ filename-- 
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

## What I learned
How to handle filenames containing spaces, which require either quoting or escaping to prevent the shell from interpreting the spaces as argument separators.

## References 
- Google Search for "spaces in filename"

# Level 3 → Level 4
Find a hidden file in a directory

## My solve
Connected to bandit3, then navigated to the inhere directory with cd. Used ls -a to show hidden files (those starting with a dot), then read the hidden file to get the password.

```
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
bandit3@bandit:~/inhere$ cat ./..
../                 ...Hiding-From-You  
bandit3@bandit:~/inhere$ cat ./...Hiding-From-You 
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

## What I learned
How to list and access hidden files in Linux, which begin with a dot (.) and require the -a flag with ls to be displayed.

## References 
- ls command with -a flag to show all files including hidden ones

# Level 4 → Level 5
Find the only human-readable file in a directory

## My solve
After connecting to bandit4, I navigated to the inhere directory. The directory contained multiple files, but only one was human-readable. Used the file command to identify file types, then read the human-readable file to get the password.

```
bandit4@bandit:~$ cd inhere
bandit4@bandit:~/inhere$ ls
-file00  -file02  -file04  -file06  -file08
-file01  -file03  -file05  -file07  -file09
bandit4@bandit:~/inhere$ file ./-file00
./-file00: data
bandit4@bandit:~/inhere$ file ./-file01
./-file01: data
bandit4@bandit:~/inhere$ file ./-file02
./-file02: data
bandit4@bandit:~/inhere$ file ./-file03
./-file03: data
bandit4@bandit:~/inhere$ file ./-file04
./-file04: data
bandit4@bandit:~/inhere$ file ./-file05
./-file05: data
bandit4@bandit:~/inhere$ file ./-file06
./-file06: data
bandit4@bandit:~/inhere$ file ./-file07
./-file07: ASCII text
bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

## What I learned
How to use the file command to determine file types and identify human-readable (ASCII text) files among binary data files.

## References 
- file command to determine file types

# Level 5 → Level 6
Find a file with specific properties using find command

## My solve
Connected to bandit5 and navigated to the inhere directory. Used the find command with specific parameters to locate a file meeting all the required criteria: human-readable, 1033 bytes in size, and not executable.

```
bandit5@bandit:~/inhere$ find ./ -size 1033c
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

## What I learned
How to use the find command with multiple criteria to search for files with specific properties like size and permissions.

## References 
- find command with size, permission, and type options

# Level 6 → Level 7
Find a file on the server with specific ownership and size

## My solve
Connected to bandit6 and needed to find a file with specific criteria anywhere on the server. Used the find command with user, group, and size parameters to locate the file, then read it to get the password.

```
bandit6@bandit:/$ find ./ -size 33c -user bandit7
find: ‘./sys/kernel/tracing/osnoise’: Permission denied
find: ‘./sys/kernel/tracing/hwlat_detector’: Permission denied
find: ‘./sys/kernel/tracing/instances’: Permission denied
find: ‘./sys/kernel/tracing/trace_stat’: Permission denied
find: ‘./sys/kernel/tracing/per_cpu’: Permission denied
find: ‘./sys/kernel/tracing/options’: Permission denied
find: ‘./sys/kernel/tracing/rv’: Permission denied
find: ‘./sys/kernel/debug’: Permission denied
find: ‘./sys/fs/pstore’: Permission denied
find: ‘./sys/fs/bpf’: Permission denied
find: ‘./root’: Permission denied
find: ‘./boot/lost+found’: Permission denied
find: ‘./boot/efi’: Permission denied
find: ‘./run/udisks2’: Permission denied
find: ‘./run/chrony’: Permission denied
find: ‘./run/user/12001’: Permission denied
find: ‘./run/user/11011’: Permission denied
find: ‘./run/user/11010’: Permission denied
find: ‘./run/user/11003’: Permission denied
find: ‘./run/user/11007’: Permission denied
find: ‘./run/user/11009’: Permission denied
find: ‘./run/user/11001’: Permission denied
find: ‘./run/user/11021’: Permission denied
find: ‘./run/user/11015’: Permission denied
find: ‘./run/user/11006/systemd/inaccessible/dir’: Permission denied
find: ‘./run/user/11004’: Permission denied
find: ‘./run/user/11023’: Permission denied
find: ‘./run/user/11002’: Permission denied
find: ‘./run/user/11005’: Permission denied
find: ‘./run/user/8001’: Permission denied
find: ‘./run/user/11014’: Permission denied
find: ‘./run/user/11000’: Permission denied
find: ‘./run/user/12000’: Permission denied
find: ‘./run/user/11025’: Permission denied
find: ‘./run/user/11019’: Permission denied
find: ‘./run/user/11016’: Permission denied
find: ‘./run/user/11024’: Permission denied
find: ‘./run/user/11020’: Permission denied
find: ‘./run/user/11013’: Permission denied
find: ‘./run/user/11012’: Permission denied
find: ‘./run/user/11026’: Permission denied
find: ‘./run/user/11027’: Permission denied
find: ‘./run/sudo’: Permission denied
find: ‘./run/screen/S-bandit25’: Permission denied
find: ‘./run/screen/S-bandit22’: Permission denied
find: ‘./run/screen/S-bandit1’: Permission denied
find: ‘./run/screen/S-bandit0’: Permission denied
find: ‘./run/screen/S-utumno0’: Permission denied
find: ‘./run/screen/S-bandit20’: Permission denied
find: ‘./run/screen/S-bandit19’: Permission denied
find: ‘./run/multipath’: Permission denied
find: ‘./run/cryptsetup’: Permission denied
find: ‘./run/lvm’: Permission denied
find: ‘./run/systemd/propagate/fwupd.service’: Permission denied
find: ‘./run/systemd/propagate/ModemManager.service’: Permission denied
find: ‘./run/systemd/propagate/polkit.service’: Permission denied
find: ‘./run/systemd/propagate/chrony.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-logind.service’: Permission denied
find: ‘./run/systemd/propagate/irqbalance.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-networkd.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-resolved.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-udevd.service’: Permission denied
find: ‘./run/systemd/inaccessible/dir’: Permission denied
find: ‘./run/lock/lvm’: Permission denied
find: ‘./dev/mqueue’: Permission denied
find: ‘./dev/shm’: Permission denied
find: ‘./lost+found’: Permission denied
find: ‘./drifter/drifter14_src/axTLS’: Permission denied
find: ‘./manpage/manpage3-pw’: Permission denied
find: ‘./var/log’: Permission denied
find: ‘./var/lib/private’: Permission denied
find: ‘./var/lib/udisks2’: Permission denied
find: ‘./var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/update-notifier/package-data-downloads/partial’: Permission denied
find: ‘./var/lib/chrony’: Permission denied
find: ‘./var/lib/snapd/void’: Permission denied
find: ‘./var/lib/snapd/cookie’: Permission denied
find: ‘./var/lib/ubuntu-advantage/apt-esm/var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/amazon’: Permission denied
find: ‘./var/lib/polkit-1’: Permission denied
./var/lib/dpkg/info/bandit7.password
find: ‘./var/spool/bandit24’: Permission denied
find: ‘./var/spool/rsyslog’: Permission denied
find: ‘./var/spool/cron/crontabs’: Permission denied
find: ‘./var/cache/pollinate’: Permission denied
find: ‘./var/cache/private’: Permission denied
find: ‘./var/cache/apt/archives/partial’: Permission denied
find: ‘./var/cache/ldconfig’: Permission denied
find: ‘./var/cache/apparmor/0fb44ac6.0’: Permission denied
find: ‘./var/cache/apparmor/208b6430.0’: Permission denied
find: ‘./var/crash’: Permission denied
find: ‘./var/tmp’: Permission denied
find: ‘./proc/tty/driver’: Permission denied
find: ‘./proc/3849200/task/3849200/fd/6’: No such file or directory
find: ‘./proc/3849200/task/3849200/fdinfo/6’: No such file or directory
find: ‘./proc/3849200/fd/5’: No such file or directory
find: ‘./proc/3849200/fdinfo/5’: No such file or directory
find: ‘./snap’: Permission denied
find: ‘./tmp’: Permission denied
find: ‘./etc/credstore’: Permission denied
find: ‘./etc/credstore.encrypted’: Permission denied
find: ‘./etc/sudoers.d’: Permission denied
find: ‘./etc/ssl/private’: Permission denied
find: ‘./etc/xinetd.d’: Permission denied
find: ‘./etc/stunnel’: Permission denied
./etc/bandit_pass/bandit7
find: ‘./etc/polkit-1/rules.d’: Permission denied
find: ‘./etc/multipath’: Permission denied
find: ‘./home/bandit31-git’: Permission denied
find: ‘./home/bandit5/inhere’: Permission denied
find: ‘./home/leviathan4/.trash’: Permission denied
find: ‘./home/bandit30-git’: Permission denied
find: ‘./home/bandit27-git’: Permission denied
find: ‘./home/leviathan0/.backup’: Permission denied
find: ‘./home/drifter6/data’: Permission denied
find: ‘./home/ubuntu’: Permission denied
find: ‘./home/bandit28-git’: Permission denied
find: ‘./home/bandit29-git’: Permission denied
find: ‘./home/drifter8/chroot’: Permission denied
bandit6@bandit:/$ cat ./var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

## What I learned
How to search the entire filesystem for files with specific ownership and size properties, and how to redirect error messages to /dev/null to make output more readable.

## References 
- find command with user, group, and size options

# Level 7 → Level 8
Find a specific string in a text file

## My solve
Connected to bandit7 and found the data.txt file in the home directory. Used grep to search for the word "millionth" in the file, which revealed the line containing the password.

```
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ man grep
bandit7@bandit:~$ cat data.txt | grep millionth
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

## What I learned
How to use grep to search for specific patterns or strings within text files.

## References 
- grep command for pattern searching in files

# Level 8 → Level 9
Find the unique line in a text file

## My solve
Connected to bandit8 and examined data.txt. To find the only line that appears exactly once, I used a combination of sort and uniq commands. First sorted the file to group identical lines together, then used uniq with the -u flag to display only lines that appear exactly once.

```
bandit8@bandit:~$ sort data.txt | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

## What I learned
How to use sort and uniq together to find unique occurrences in text files, and how to use command pipelines to process data through multiple commands.

## References 
- sort command to organize text data
- uniq command with -u flag to show only unique lines
- Piping and Redirection

# Level 9 → Level 10
Find human-readable strings preceded by '=' characters

## My solve
Connected to bandit9 and found that data.txt was a binary file. Used the strings command to extract only the human-readable text, then piped that to grep to search for lines containing multiple '=' characters, which revealed the password.

```
bandit9@bandit:~$ strings data.txt | grep [=]*
q.9,
mY>m{
/<[;
fL{[
,)wp
fQ4U_
U [^
vy%-
,[(P
kxfl
zu`0|
tb^_5
========== the
[s}g'
aXJf`
5n%V
.Gl$
_}d@
^>!hM*aM
SvjdF
aX7/)
5Twx
"wl"4
tj(*
X-C'}
I\*A
$}>V6
F~81
}AA?
S=s*$u
cw{T
~`5!
N!Sb
'$|/
vN9LlQ4
5t6"
!Cc.
e%D1'`
b5M:
P!~LY
hXEjT
oOZ1
3 cK
MX.^
>9/^E
|S,t
i&y.
W@~,
,P2B
6$sf
[=u~]/
M]^/B
\b?[
hW\=
M1[I^
oedS
q/q;
p1*~
]FK}
f)Od
  5Fm0]?
Ab9I
[K;}
zvlB    {j
?X:TL
KBbd
l-Lo
Vvmf
O5gz
GYup
=}y2|
=RiaT
1j=\
j&B*
wv,Z
g`UZ
========== password
mgaw
 12w
*U[p<z
u[BMg
I"^!
]'kpM
!QeZ
5&~`Op5u{,
5DDB
D$JMl
iAHO
i`/`|9
P~{k
NMG1`
3P@X
&y{8L
k^5x+C
c^GH'{!D
f=+n
Q========== is%
ti1O
j,A/
|Yf_!i
H{y{K_
%@$3
V;yH
'qa)
T]FN
Q#C%#F
9hVt|
mvS^K
*?>v)
g0x|,
CAwN
9\"jM
.7"N
-5>CH8
hqMXlA!
}LGUB
l5i%h
Kh+>o
yYWE
imbx
JV,b
}`?ER
#:HV
  <|o
T\0;
;#Av
!IQL
A#c]
ZV;v
q4C]_
m[J#
^.@b
?N7P
"3;8
  jO+6
Sq$O
' gu3k&Z
k?.#v
~ieu3
ps6S
lbx{x{
@E5A
]){DJp
="K@
cMJR
uNI(
`A-o
L/1]
3ewB_
er/T
n7X=
D;2B8
LTCn
Er"l
om?}
JD19.s
F.s[
gd}]]
&@+F
HW      G7
;}[b
QcJC
IEyBXq
C87P
*,mN[
3+AM
|)C,
@{BJ
rMo;c{U
BJ?rGJ
Zw<@
]+AN
rrkj
|H&Fw
Ab@0
B0[T,
0s)o8
VtGl
bc&@P
@f;E
w \t
z'J|
i\t8
%DgU
IJ/cq
Y[m,<
Q),aC$;
`Z_i
R,oC
FB<<9
+il)
C#3MGk
f.H/
\sWEJ;#
fOM"
Za};+?
F<'=
j%OE
0Dc:
p2Ag
&&O0    %
J!gu
j6_+
0Sk\1
& MxY
]Ct-
kT+2
?L58!fb(ot
1&9H
5z7O
>/Meu
!=v5~6
7.p~
M J.)
S5vZ
eHY2*
>u`9J========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
F~aX`8
xcZK
4T9(
F,C] 
kd^l
[pp?RX9
{1]:
|WH
[~&N
rCtJ
t&Lb
I[rg8
c;Ep
BFb7
rL33
AeJgRi
*A      ;?M
8;I]
5J:)NV
DUjb
c>u}
vGu(q^
5pVLcj
Z]^Gn
zvUzy|
y|;KR"t^
tU.a
LZqw4h+
Lm.p
P yK
.Cye_
7x}FE
X$ns
 ]6r
0B\l
kFs+
8S|?
xZE 
R@3{
K"89
Fb=G
7h08
@udz
9V\N
F%?TI0oG
AUE:F
```

## What I learned
How to use the strings command to extract readable text from binary files, and how to combine it with grep to filter for specific patterns.

## References 
- strings command for extracting readable characters from binary files
- grep command with pattern matching

# Level 10 → Level 11
Decode base64 encoded data

## My solve
Connected to bandit10 and found the data.txt file containing base64 encoded data. Used the base64 command with the -d flag to decode the contents, revealing the password.

```
bandit10@bandit:~$ man base64
bandit10@bandit:~$ cat data.txt | base64 -d
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

## What I learned
How to recognize and decode base64 encoded data using the base64 command line tool.

## References 
- base64 command with -d flag for decoding
- Base64 on Wikipedia

# Level 11 → Level 12
Decode text that has been ROT13 encrypted

## My solve
Connected to bandit11 and found the data.txt file with ROT13 encoded content. Used the tr command to rotate all letters back 13 positions, revealing the password.

```
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

## What I learned
How to use the tr command to perform character substitution for simple ciphers like ROT13, where each letter is replaced with the letter 13 positions after it in the alphabet.

## References 
- tr command for character translation
- Rot13 on Wikipedia
