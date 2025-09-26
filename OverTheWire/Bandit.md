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

# Level 12 → Level 13
Deal with a hexdump of repeatedly compressed data

## My solve
Connected to bandit12 and found the data.txt hexdump file. Created a temporary directory using mktemp -d, copied the file there, and began the decompression process:

1. Used xxd -r to reverse the hexdump back to binary data
2. Used file command to identify the compression type
3. Renamed the file with appropriate extension and used the correct decompression tool
4. Repeated steps 2-3 multiple times through various compression formats (gzip, bzip2, tar)
5. Eventually found a text file containing the password

```
bandit12@bandit:~$ ls
data.txt
bandit12@bandit:~$ mktemp -d
/tmp/tmp.lE8XtLvS76
bandit12@bandit:~$ cp data.txt /tmp/tmp.lE8XtLvS76
bandit12@bandit:~$ cd /tmp/tmp.lE8XtLvS76
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ ls
data.txt
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ file data.txt 
data.txt: ASCII text
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ cat data.txt 
00000000: 1f8b 0808 0933 9f68 0203 6461 7461 322e  .....3.h..data2.
00000010: 6269 6e00 0148 02b7 fd42 5a68 3931 4159  bin..H...BZh91AY
00000020: 2653 59be 9d9d 9600 001f ffff fe7f fbcf  &SY.............
00000030: af7f 9eff f7ee ffdf bff7 fef7 ddbe 9db7  ................
00000040: bf9f 9f5f ca6f fffe d6fb feff b001 3ab3  ..._.o........:.
00000050: 0403 40d0 0000 00d0 01a0 03d4 0000 0346  ..@............F
00000060: 41a1 9000 0000 1900 0190 0686 8191 a326  A..............&
00000070: 1340 0c8c 4d0f 4d4c 4403 468d 0d1a 0001  .@..M.MLD.F.....
00000080: a686 8000 01a0 6462 6868 6800 0006 8f50  ......dbhhh....P
00000090: 00d0 1a06 9a0c d406 8c80 189a 6834 64d0  ............h4d.
000000a0: 064d 0000 3a68 1a34 d00d 0001 a1a1 91a0  .M..:h.4........
000000b0: 0000 0323 4d03 2341 9034 1a00 00c8 320d  ...#M.#A.4....2.
000000c0: 001a 1880 3401 8406 9a68 00d1 a34d 34d1  ....4....h...M4.
000000d0: 7808 0920 2027 a994 91db 6412 de13 8af2  x..  '....d.....
000000e0: 7f2a f82d c875 b4c2 6723 afc6 8b7c 62ad  .*.-.u..g#...|b.
000000f0: a375 3887 65c0 1718 5224 81c3 0b33 8e21  .u8.e...R$...3.!
00000100: c736 e901 b187 8c9f 5b3c a81e f09d ec5c  .6......[<.....\
00000110: 41c0 0b74 ca62 56e6 8452 ce37 8889 5ab7  A..t.bV..R.7..Z.
00000120: d5d8 9316 1d26 26e7 b18f e376 b6b9 02ec  .....&&....v....
00000130: 0880 aa07 3c2c fd25 03ba cc87 59fa 5436  ....<,.%....Y.T6
00000140: 4a67 b193 3aec d8a3 6813 92e6 67ce 5118  Jg..:...h...g.Q.
00000150: b22b d1b2 114c 9fb6 3033 d37a 86b2 62c5  .+...L..03.z..b.
00000160: 9fb1 09c3 afcb 76ab ab69 e168 cdb6 6d5e  ......v..i.h..m^
00000170: 3b86 91a9 7a45 0371 70de ca02 4ce5 1de9  ;...zE.qp...L...
00000180: f996 0ae0 2c33 a0ca ceeb 1d0a 02a7 3160  ....,3........1`
00000190: 9746 3cd6 c5c1 433b 991f 9989 5ab3 cbf2  .F<...C;....Z...
000001a0: 0759 072f 8b6f 08af f163 c149 8879 f738  .Y./.o...c.I.y.8
000001b0: 6241 3876 4edf 6038 0b60 277c d2ca 7908  bA8vN.`8.`'|..y.
000001c0: b1f3 a93c 23d0 277b 215c 7498 b2a1 01dd  ...<#.'{!\t.....
000001d0: 563b be47 3fdc a008 0f08 82c7 2044 c8da  V;.G?....... D..
000001e0: a241 c91c c3ee f1a1 9b98 25eb 5212 3fb1  .A........%.R.?.
000001f0: e545 2469 108f 7f01 e7c9 faed cd3e 9f08  .E$i.........>..
00000200: 97bc 1b04 a087 e826 0993 65d3 13b6 5365  .......&..e...Se
00000210: 3c6d 10e5 1d85 66ab 0497 6242 8799 8112  <m....f...bB....
00000220: 61a0 87dc fcfb 9274 774a c918 d5ce 3c0f  a......twJ....<.
00000230: d346 95c8 1e30 42a6 a3b7 a93b 67f3 186c  .F...0B....;g..l
00000240: 904c 842c 30c5 e1b2 b841 05e0 7144 2a60  .L.,0....A..qD*`
00000250: ca14 0a52 f589 fe2e e48a 70a1 217d 3b3b  ...R......p.!};;
00000260: 2c19 d8f7 0e48 0200 00                   ,....H...
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ xxd -r data.txt 
�       3�hdata2.binH��BZh91AY&SY��������ϯ�����߿���ݾ�����_�o�������:�@����FA�������&@
▒����dbhhh�P�▒�
▒▒�4��hѣM4�x2  �  '����d���*�-�u��g#�Ƌ|b��u8�e�▒R$��
                                                    3�!�6�����[<����\A�
                                                                       t�bV��R�7��Z��&&籏�v����<,�%�Y�T6Jg��:�أh��g�Q▒�+ѲL��03�z��bş� ï�v��i�hͶm^;���zEqp��L����
�,3����
�1`�F<���C;���Z���Y/���c�I�y�8bA8vN�`8
                                      `'|�����<#�'{!\t����V;�G�� D�ڢA���񡛘%�R?��E$i������>����&        �e��Se<m��f��bB���a������twJ�▒��<�F��0B����;g�▒l�L�,0�ᲸA�qD*`�
R���.��p�!};;,��Hbandit12@bandit:/tmp/tmp.lE8XtLvS76$ ls
data.txt
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ cat data.txt 
00000000: 1f8b 0808 0933 9f68 0203 6461 7461 322e  .....3.h..data2.
00000010: 6269 6e00 0148 02b7 fd42 5a68 3931 4159  bin..H...BZh91AY
00000020: 2653 59be 9d9d 9600 001f ffff fe7f fbcf  &SY.............
00000030: af7f 9eff f7ee ffdf bff7 fef7 ddbe 9db7  ................
00000040: bf9f 9f5f ca6f fffe d6fb feff b001 3ab3  ..._.o........:.
00000050: 0403 40d0 0000 00d0 01a0 03d4 0000 0346  ..@............F
00000060: 41a1 9000 0000 1900 0190 0686 8191 a326  A..............&
00000070: 1340 0c8c 4d0f 4d4c 4403 468d 0d1a 0001  .@..M.MLD.F.....
00000080: a686 8000 01a0 6462 6868 6800 0006 8f50  ......dbhhh....P
00000090: 00d0 1a06 9a0c d406 8c80 189a 6834 64d0  ............h4d.
000000a0: 064d 0000 3a68 1a34 d00d 0001 a1a1 91a0  .M..:h.4........
000000b0: 0000 0323 4d03 2341 9034 1a00 00c8 320d  ...#M.#A.4....2.
000000c0: 001a 1880 3401 8406 9a68 00d1 a34d 34d1  ....4....h...M4.
000000d0: 7808 0920 2027 a994 91db 6412 de13 8af2  x..  '....d.....
000000e0: 7f2a f82d c875 b4c2 6723 afc6 8b7c 62ad  .*.-.u..g#...|b.
000000f0: a375 3887 65c0 1718 5224 81c3 0b33 8e21  .u8.e...R$...3.!
00000100: c736 e901 b187 8c9f 5b3c a81e f09d ec5c  .6......[<.....\
00000110: 41c0 0b74 ca62 56e6 8452 ce37 8889 5ab7  A..t.bV..R.7..Z.
00000120: d5d8 9316 1d26 26e7 b18f e376 b6b9 02ec  .....&&....v....
00000130: 0880 aa07 3c2c fd25 03ba cc87 59fa 5436  ....<,.%....Y.T6
00000140: 4a67 b193 3aec d8a3 6813 92e6 67ce 5118  Jg..:...h...g.Q.
00000150: b22b d1b2 114c 9fb6 3033 d37a 86b2 62c5  .+...L..03.z..b.
00000160: 9fb1 09c3 afcb 76ab ab69 e168 cdb6 6d5e  ......v..i.h..m^
00000170: 3b86 91a9 7a45 0371 70de ca02 4ce5 1de9  ;...zE.qp...L...
00000180: f996 0ae0 2c33 a0ca ceeb 1d0a 02a7 3160  ....,3........1`
00000190: 9746 3cd6 c5c1 433b 991f 9989 5ab3 cbf2  .F<...C;....Z...
000001a0: 0759 072f 8b6f 08af f163 c149 8879 f738  .Y./.o...c.I.y.8
000001b0: 6241 3876 4edf 6038 0b60 277c d2ca 7908  bA8vN.`8.`'|..y.
000001c0: b1f3 a93c 23d0 277b 215c 7498 b2a1 01dd  ...<#.'{!\t.....
000001d0: 563b be47 3fdc a008 0f08 82c7 2044 c8da  V;.G?....... D..
000001e0: a241 c91c c3ee f1a1 9b98 25eb 5212 3fb1  .A........%.R.?.
000001f0: e545 2469 108f 7f01 e7c9 faed cd3e 9f08  .E$i.........>..
00000200: 97bc 1b04 a087 e826 0993 65d3 13b6 5365  .......&..e...Se
00000210: 3c6d 10e5 1d85 66ab 0497 6242 8799 8112  <m....f...bB....
00000220: 61a0 87dc fcfb 9274 774a c918 d5ce 3c0f  a......twJ....<.
00000230: d346 95c8 1e30 42a6 a3b7 a93b 67f3 186c  .F...0B....;g..l
00000240: 904c 842c 30c5 e1b2 b841 05e0 7144 2a60  .L.,0....A..qD*`
00000250: ca14 0a52 f589 fe2e e48a 70a1 217d 3b3b  ...R......p.!};;
00000260: 2c19 d8f7 0e48 0200 00                   ,....H...
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ xxd -r data.txt | tee data.bin
�       3�hdata2.binH��BZh91AY&SY��������ϯ�����߿���ݾ�����_�o�������:�@����FA�������&@
▒����dbhhh�P�▒�
▒▒�4��hѣM4�x2  �  '����d���*�-�u��g#�Ƌ|b��u8�e�▒R$��
                                                    3�!�6�����[<����\A�
                                                                       t�bV��R�7��Z��&&籏�v����<,�%�Y�T6Jg��:�أh��g�Q▒�+ѲL��03�z��bş� ï�v��i�hͶm^;���zEqp��L����
�,3����
�1`�F<���C;���Z���Y/���c�I�y�8bA8vN�`8
                                      `'|�����<#�'{!\t����V;�G�� D�ڢA���񡛘%�R?��E$i������>����&        �e��Se<m��f��bB���a������twJ�▒��<�F��0B����;g�▒l�L�,0�ᲸA�qD*`�
R���.��p�!};;,��Hbandit12@bandit:/tmp/tmp.lE8XtLvS76$ file data.bin
data.bin: gzip compressed data, was "data2.bin", last modified: Fri Aug 15 13:15:53 2025, max compression, from Unix, original size modulo 2^32 584
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ mv data.bin data.gz
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ gunzip data.gz 
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ ls
data  data.txt
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ file data
data: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ bzip2 -d data
bzip2: Can't guess original name for data -- using data.out
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ ls
data.out  data.txt
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ file data.out 
data.out: gzip compressed data, was "data4.bin", last modified: Fri Aug 15 13:15:53 2025, max compression, from Unix, original size modulo 2^32 20480
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ mv data.out data.gz
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ gunzip data.gz 
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ ls
data  data.txt
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ file data
data: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ tar -x -f data
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ ls
data  data5.bin  data.txt
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ file data5.bin 
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ tar -x -f data5.bin
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ ls
data  data5.bin  data6.bin  data.txt
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ bzip2 -d data6.bin
bzip2: Can't guess original name for data6.bin -- using data6.bin.out
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ ls
data  data5.bin  data6.bin.out  data.txt
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ file data6.bin.out 
data6.bin.out: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ tar -x -f data6.bin.out
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ ls
data  data5.bin  data6.bin.out  data8.bin  data.txt
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Fri Aug 15 13:15:53 2025, max compression, from Unix, original size modulo 2^32 49
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ mv data8.bin data8.gz
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ gunzip data8.gz
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ ls
data  data5.bin  data6.bin.out  data8  data.txt
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ file data8
data8: ASCII text
bandit12@bandit:/tmp/tmp.lE8XtLvS76$ cat data8
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```

## What I learned
How to handle hexdumps, identify file types, and work with multiple layers of compression using various tools like xxd, file, tar, gzip, and bzip2.

## References 
- xxd command for converting between binary and hexdump
- file command to identify file types
- Various decompression tools (gzip, bzip2, tar)
- Hex dump on Wikipedia

# Level 13 → Level 14
Use an SSH private key to access the next level

## My solve
Connected to bandit13 and found an SSH private key in the home directory. Used this key to log into bandit14 on localhost, then read the password file that was only accessible to the bandit14 user.

```
bandit13@bandit:~$ ls
sshkey.private
bandit13@bandit:~$ ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
The authenticity of host '[bandit.labs.overthewire.org]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit13/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit13/.ssh/known_hosts).
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

!!! You are trying to log into this SSH server with a password on port 2220 from localhost.
!!! Connecting from localhost is blocked to conserve resources.
!!! Please log out and log in again.

backend: gibson-1

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

bandit14@bandit:~$ cat  /etc/bandit_pass/bandit14
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```

## What I learned
How to use SSH with private key authentication instead of password authentication, and how to use a private key file with the ssh -i option.

## References 
- ssh command with -i flag for identity file (private key)
- SSH/OpenSSH/Keys documentation

# Level 14 → Level 15
Submit a password to a network service on a specific port

## My solve
Connected to bandit14, retrieved the current level's password from /etc/bandit_pass/bandit14, then used netcat (nc) to connect to localhost on port 30000 and submitted the password. The service responded with the password for the next level.

```
bandit14@bandit:~$ man nc
bandit14@bandit:~$ nc localhost 30000
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```

## What I learned
How to use netcat (nc) to connect to network services on specific ports and send data to them.

## References 
- nc (netcat) command for network connections
- Localhost and port concepts in networking

# Level 15 → Level 16
Connect to a service using SSL/TLS encryption

## My solve
Connected to bandit15, then used openssl s_client to establish an encrypted SSL/TLS connection to localhost on port 30001. Submitted the current level's password through this secure connection to receive the password for the next level.

```
bandit15@bandit:~$ man openssl
bandit15@bandit:~$ opensssl s_client localhost:30001
Command 'opensssl' not found, did you mean:
  command 'openssl' from deb openssl (3.0.13-0ubuntu3.5)
Try: apt install <deb name>
bandit15@bandit:~$ openssl s_client localhost:30001
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
---
Certificate chain
 0 s:CN = SnakeOil
   i:CN = SnakeOil
   a:PKEY: rsaEncryption, 4096 (bit); sigalg: RSA-SHA256
   v:NotBefore: Jun 10 03:59:50 2024 GMT; NotAfter: Jun  8 03:59:50 2034 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIFBzCCAu+gAwIBAgIUBLz7DBxA0IfojaL/WaJzE6Sbz7cwDQYJKoZIhvcNAQEL
BQAwEzERMA8GA1UEAwwIU25ha2VPaWwwHhcNMjQwNjEwMDM1OTUwWhcNMzQwNjA4
MDM1OTUwWjATMREwDwYDVQQDDAhTbmFrZU9pbDCCAiIwDQYJKoZIhvcNAQEBBQAD
ggIPADCCAgoCggIBANI+P5QXm9Bj21FIPsQqbqZRb5XmSZZJYaam7EIJ16Fxedf+
jXAv4d/FVqiEM4BuSNsNMeBMx2Gq0lAfN33h+RMTjRoMb8yBsZsC063MLfXCk4p+
09gtGP7BS6Iy5XdmfY/fPHvA3JDEScdlDDmd6Lsbdwhv93Q8M6POVO9sv4HuS4t/
jEjr+NhE+Bjr/wDbyg7GL71BP1WPZpQnRE4OzoSrt5+bZVLvODWUFwinB0fLaGRk
GmI0r5EUOUd7HpYyoIQbiNlePGfPpHRKnmdXTTEZEoxeWWAaM1VhPGqfrB/Pnca+
vAJX7iBOb3kHinmfVOScsG/YAUR94wSELeY+UlEWJaELVUntrJ5HeRDiTChiVQ++
wnnjNbepaW6shopybUF3XXfhIb4NvwLWpvoKFXVtcVjlOujF0snVvpE+MRT0wacy
tHtjZs7Ao7GYxDz6H8AdBLKJW67uQon37a4MI260ADFMS+2vEAbNSFP+f6ii5mrB
18cY64ZaF6oU8bjGK7BArDx56bRc3WFyuBIGWAFHEuB948BcshXY7baf5jjzPmgz
mq1zdRthQB31MOM2ii6vuTkheAvKfFf+llH4M9SnES4NSF2hj9NnHga9V08wfhYc
x0W6qu+S8HUdVF+V23yTvUNgz4Q+UoGs4sHSDEsIBFqNvInnpUmtNgcR2L5PAgMB
AAGjUzBRMB0GA1UdDgQWBBTPo8kfze4P9EgxNuyk7+xDGFtAYzAfBgNVHSMEGDAW
gBTPo8kfze4P9EgxNuyk7+xDGFtAYzAPBgNVHRMBAf8EBTADAQH/MA0GCSqGSIb3
DQEBCwUAA4ICAQAKHomtmcGqyiLnhziLe97Mq2+Sul5QgYVwfx/KYOXxv2T8ZmcR
Ae9XFhZT4jsAOUDK1OXx9aZgDGJHJLNEVTe9zWv1ONFfNxEBxQgP7hhmDBWdtj6d
taqEW/Jp06X+08BtnYK9NZsvDg2YRcvOHConeMjwvEL7tQK0m+GVyQfLYg6jnrhx
egH+abucTKxabFcWSE+Vk0uJYMqcbXvB4WNKz9vj4V5Hn7/DN4xIjFko+nREw6Oa
/AUFjNnO/FPjap+d68H1LdzMH3PSs+yjGid+6Zx9FCnt9qZydW13Miqg3nDnODXw
+Z682mQFjVlGPCA5ZOQbyMKY4tNazG2n8qy2famQT3+jF8Lb6a4NGbnpeWnLMkIu
jWLWIkA9MlbdNXuajiPNVyYIK9gdoBzbfaKwoOfSsLxEqlf8rio1GGcEV5Hlz5S2
txwI0xdW9MWeGWoiLbZSbRJH4TIBFFtoBG0LoEJi0C+UPwS8CDngJB4TyrZqEld3
rH87W+Et1t/Nepoc/Eoaux9PFp5VPXP+qwQGmhir/hv7OsgBhrkYuhkjxZ8+1uk7
tUWC/XM0mpLoxsq6vVl3AJaJe1ivdA9xLytsuG4iv02Juc593HXYR8yOpow0Eq2T
U5EyeuFg5RXYwAPi7ykw1PW7zAPL4MlonEVz+QXOSx6eyhimp1VZC11SCg==
-----END CERTIFICATE-----
subject=CN = SnakeOil
issuer=CN = SnakeOil
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 2103 bytes and written 373 bytes
Verification error: self-signed certificate
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 4096 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 18 (self-signed certificate)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: D86E7E0D6D04D33AF1530448D45CB163783D39455BD65523F9D2D5F7061FC259
    Session-ID-ctx: 
    Resumption PSK: F6F1A0886BDE1C1C6B3357BAD8ECCE0635FDF2A0D334F4107F51E9ED112C7FC5ABF289DE7911D23FA0F74E2E6AD1617A
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - b3 e0 25 4d 51 8b 9b bc-6d 7b 2e b9 70 74 42 b6   ..%MQ...m{..ptB.
    0010 - 17 6c 45 21 66 55 c5 38-1f fa 33 54 7b 6c 53 d0   .lE!fU.8..3T{lS.
    0020 - f7 49 dd c6 01 0c dc 68-79 fa a5 39 ce 4e 92 96   .I.....hy..9.N..
    0030 - b1 14 ee bc 0c 6b 4e 15-8e 54 f4 fc 60 f4 12 0d   .....kN..T..`...
    0040 - c1 45 d0 83 38 26 d8 2b-e4 8e b8 29 0c b9 32 ba   .E..8&.+...)..2.
    0050 - 90 3c 6c 0e 50 12 03 08-43 46 6b 67 6e da 01 ff   .<l.P...CFkgn...
    0060 - c7 3d 20 15 80 1d 68 ae-5d 09 f4 d4 e7 57 ae 0a   .= ...h.]....W..
    0070 - dd 6f 3a d9 e5 40 df 92-50 20 96 6f f6 3f cf fc   .o:..@..P .o.?..
    0080 - 52 0f f5 f8 7d 59 c0 f2-ac d2 1d b6 ce 26 30 a0   R...}Y.......&0.
    0090 - 32 f6 e3 8a 07 a3 b2 13-f5 83 bb ea 32 b5 16 44   2...........2..D
    00a0 - 4b 23 cc 6f 97 ad e4 a7-cf 55 f2 81 c8 ab 49 75   K#.o.....U....Iu
    00b0 - b6 5d fc 71 e3 70 1e af-f2 5b 29 ef 52 b6 77 dd   .].q.p...[).R.w.
    00c0 - 23 08 0a e2 fa 0f 7e 0b-d1 87 6c 04 1b 86 12 bc   #.....~...l.....
    00d0 - 8c 85 5a db 0f b2 b5 bf-28 01 fc e8 99 be e9 18   ..Z.....(.......

    Start Time: 1758715729
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 0C6CC48380A692503C9DCC7F4E74B608BAE2153844667F062D09153B47CB395D
    Session-ID-ctx: 
    Resumption PSK: D9BF71CB953AE07BDA2778A7CD3B1F7498A1A1BCF3715D43AFA2FBA9305F07ACEE9BD0D54A0F075ABBF72EC5E8221D82
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - b3 e0 25 4d 51 8b 9b bc-6d 7b 2e b9 70 74 42 b6   ..%MQ...m{..ptB.
    0010 - 93 db 92 c4 24 f1 28 c6-bd 95 e7 44 20 74 3b 9f   ....$.(....D t;.
    0020 - fc 4a 57 d0 81 54 4e 26-b3 a2 e0 3e ca 9c de 86   .JW..TN&...>....
    0030 - 92 28 fd 00 f3 18 24 88-7b d9 43 1c 07 b5 c1 96   .(....$.{.C.....
    0040 - 61 40 71 1c f0 05 13 eb-8a 72 48 68 5e 5e fa 97   a@q......rHh^^..
    0050 - 71 1c 24 2b 69 c5 91 c9-fb 0c c3 25 9e 3b 59 47   q.$+i......%.;YG
    0060 - 18 8b 7c bd d6 40 5a 46-5f 7b fb 83 5a 2b fc cf   ..|..@ZF_{..Z+..
    0070 - 69 67 66 8e 44 77 b0 63-24 34 93 ff 0c 5f a6 59   igf.Dw.c$4..._.Y
    0080 - 9b d7 a0 89 56 7d e6 fb-66 52 5b 89 8f bf 7a 5d   ....V}..fR[...z]
    0090 - 61 c1 ac 7f 2a ab 0b 3d-04 48 31 15 22 e2 cd fc   a...*..=.H1."...
    00a0 - 75 13 fa ff 3b 82 77 14-5a 9a 7d 36 c9 18 bd 54   u...;.w.Z.}6...T
    00b0 - 5b f2 7e 8a 3c a7 47 54-14 4a 0c eb 35 c4 f7 01   [.~.<.GT.J..5...
    00c0 - 09 9e 47 4b 1d b5 e2 18-61 a1 c1 2b 32 34 73 33   ..GK....a..+24s3
    00d0 - 89 c6 fa 2e 22 0d 76 34-c3 21 bb 3d f0 05 b6 18   ....".v4.!.=....

    Start Time: 1758715729
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
Correct!
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```

## What I learned
How to use openssl s_client to connect to services that require SSL/TLS encryption, and how to send data through an encrypted connection.

## References 
- openssl s_client command for SSL/TLS connections
- Secure Socket Layer/Transport Layer Security on Wikipedia
- OpenSSL Cookbook - Testing with OpenSSL

# Level 16 → Level 17
Find a specific SSL/TLS service and retrieve credentials

## My solve
Connected to bandit16, then used nmap to scan ports 31000-32000 on localhost to find open ports. Tested each open port with openssl s_client to determine which ones used SSL/TLS encryption. Submitted the current level's password to each SSL/TLS service until finding the one that returned credentials (an SSH private key) instead of echoing back the input.

```
bandit16@bandit:~$ nmap localhost -p 31000-32000
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-09-24 12:38 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00015s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.05 seconds

bandit16@bandit:~$ openssl s_client -connect localhost:31790 -quiet 
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

bandit16@bandit:/tmp/tmp.9oJHGWdIVr$ cat >> key
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

^C
bandit16@bandit:/tmp/tmp.9oJHGWdIVr$ ls
key
bandit16@bandit:/tmp/tmp.9oJHGWdIVr$ cat key
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

bandit16@bandit:/tmp/tmp.9oJHGWdIVr$ chmod a-r key
bandit16@bandit:/tmp/tmp.9oJHGWdIVr$ chmod u+r key
bandit16@bandit:/tmp/tmp.9oJHGWdIVr$ ssh -i key -p 2220 bandit17@bandit.labs.overthewire.org
The authenticity of host '[bandit.labs.overthewire.org]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit16/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit16/.ssh/known_hosts).
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

!!! You are trying to log into this SSH server with a password on port 2220 from localhost.
!!! Connecting from localhost is blocked to conserve resources.
!!! Please log out and log in again.

backend: gibson-1

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

bandit17@bandit:~$ 
```

## What I learned
How to use nmap for port scanning, how to identify SSL/TLS services, and how to distinguish between echo services and those providing unique responses.

## References 
- nmap command for port scanning
- openssl s_client for SSL/TLS connections
- Port scanner on Wikipedia

# Level 17 → Level 18
Find the single line that differs between two files

## My solve
Connected to bandit17 using the SSH private key obtained in the previous level. Used the diff command to compare passwords.old and passwords.new files, which highlighted the only line that was different between them. The password for the next level was the new line in passwords.new.

```
bandit17@bandit:~$ ls
passwords.new  passwords.old
bandit17@bandit:~$ diff passwords.old passwords.new
42c42
< CgmS55GVlEKTgx8xpW8HuWnHlBKP924b
---
> x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```

## What I learned
How to use the diff command to identify differences between files, which shows changes with < for the first file and > for the second file.

## References 
- diff command for comparing files line by line

# Level 18 → Level 19
Access a server that logs you out immediately upon login

## My solve
The challenge involved a server where the .bashrc file had been modified to log out the user immediately after SSH login. To bypass this, I used SSH's ability to execute commands directly on connection without starting an interactive shell.

Used SSH with a command at the end to read the readme file without triggering the modified .bashrc:
```
 @kali  ssh -p 2220 bandit18@bandit.labs.overthewire.org "cat readme"
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-1
bandit18@bandit.labs.overthewire.org's password: 
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```

## What I learned
How to execute commands directly via SSH without starting an interactive session, which is useful for bypassing login restrictions or modified startup files.

## References 
- ssh command with remote command execution
- Understanding .bashrc and shell initialization files

# Level 19 → Level 20
Use a setuid binary to access protected files

## My solve
Connected to bandit19 and found a setuid binary in the home directory. Running it without arguments displayed usage instructions. The binary allowed me to execute commands as the bandit20 user, so I used it to read the password file at /etc/bandit_pass/bandit20.

```
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```

## What I learned
How setuid binaries work - programs that run with the permissions of their owner rather than the user executing them, allowing for controlled privilege escalation.

## References 
- setuid on Wikipedia
- Understanding privileged execution in Linux

  # Level 20 → Level 21
Use a setuid binary that requires network communication

## My solve
Connected to bandit20 and examined the setuid binary. This binary needed to connect to a port where it would receive the current level's password and then send back the next level's password.

To solve this, I needed to:
1. Start a netcat listener on a chosen port in the background or in another terminal session
2. Make the listener send the current level's password when connected to
3. Run the setuid binary pointing to that port
4. Capture the response with the next password

Used either screen/tmux or background jobs to manage these parallel processes.

```
bandit20@bandit:~$ echo -n "0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO" | nc -l -p 6969 &
[1] 1234732
bandit20@bandit:~$ ./suconnect 6969
Read: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Password matches, sending next password
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
```

## What I learned
How to set up a simple network service using netcat, manage multiple processes, and use job control or terminal multiplexers in Linux.

## References 
- nc (netcat) for creating network connections
- Job control in Unix (bg, fg, jobs)
- screen/tmux for terminal session management

# Level 21 → Level 22
Investigate scheduled cron jobs to find password

## My solve
Connected to bandit21 and examined the cron jobs in /etc/cron.d/ directory. Found a cron job related to bandit22, which executed a script at regular intervals. Examined the script to find out what it was doing, which revealed it was copying the bandit22 password to a readable file in /tmp.

```
bandit21@bandit:/etc/cron.d$ ls
behemoth4_cleanup  cronjob_bandit23  leviathan5_cleanup    sysstat
clean_tmp          cronjob_bandit24  manpage3_resetpw_job
cronjob_bandit22   e2scrub_all       otw-tmp-dir
bandit21@bandit:/etc/cron.d$ cat cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
bandit21@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
bandit21@bandit:/etc/cron.d$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv 
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```

## What I learned
How to examine cron job configurations and understand scheduled tasks in Linux systems, including how to trace what scripts are doing when executed automatically.

## References 
- cron and crontab for scheduled job management
- crontab(5) manual page for understanding cron job syntax

# Level 22 → Level 23
Analyze a cron job script to find password location

## My solve
Connected to bandit22 and examined the cron jobs in /etc/cron.d/. Found the cron job for bandit23 which executed a shell script. Read the script to understand its logic - it created a filename based on the username, created a hash of that string, then used that hash to create a path to a file in /tmp where the password was stored.

To get the password, I needed to:
1. Analyze what the script would do when run as bandit23
2. Execute the same commands manually with "bandit23" as the username
3. Generate the correct filename hash
4. Read the file from the determined /tmp location

```
bandit22@bandit:~$ cd /etc/cron.d
bandit22@bandit:/etc/cron.d$ ls
behemoth4_cleanup  cronjob_bandit23  leviathan5_cleanup    sysstat
clean_tmp          cronjob_bandit24  manpage3_resetpw_job
cronjob_bandit22   e2scrub_all       otw-tmp-dir
bandit22@bandit:/etc/cron.d$ cat cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
bandit22@bandit:/etc/cron.d$ cd
bandit22@bandit:~$ cd /etc/cron.d
bandit22@bandit:/etc/cron.d$ ls
behemoth4_cleanup  cronjob_bandit23  leviathan5_cleanup    sysstat
clean_tmp          cronjob_bandit24  manpage3_resetpw_job
cronjob_bandit22   e2scrub_all       otw-tmp-dir
bandit22@bandit:/etc/cron.d$ cat cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
bandit22@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
bandit22@bandit:/etc/cron.d$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:/etc/cron.d$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349 
0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
```

## What I learned
How to read and understand shell scripts written by others, follow the logic of scripts that use variable substitution and hashing, and how to manually execute script logic to get desired results.

## References 
- cron and crontab for scheduled job management
- bash script analysis and execution

# Level 23 → Level 24
Create a shell script to leverage a cron job running as bandit24

## My solve
I checked the cron jobs in /etc/cron.d/ and found a script running as bandit24. The script executes any files in /var/spool/bandit24 owned by bandit23, then deletes them. 

I created a simple script to copy the bandit24 password to a readable location, made it executable, and placed it in the spool directory for the cron job to execute.

```bash
bandit23@bandit:~$ ls
bandit23@bandit:~$ mktemp -d
/tmp/tmp.2f6Cw9390z
bandit23@bandit:~$ ^C
bandit23@bandit:~$ cd /tmp/tmp.2f6Cw9390z
bandit23@bandit:/tmp/tmp.2f6Cw9390z$ nano run.sh

run.sh file is

#!/bin/bash

cat /etc/bandit_pass/bandit24 > /tmp/tmp.2f6Cw9390z/pass

Unable to create directory /home/bandit23/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.

bandit23@bandit:/tmp/tmp.2f6Cw9390z$ touch pass
bandit23@bandit:/tmp/tmp.2f6Cw9390z$ chmod -R /tmp/tmp.2f6Cw9390z
chmod: missing operand after ‘/tmp/tmp.2f6Cw9390z’
Try 'chmod --help' for more information.
bandit23@bandit:/tmp/tmp.2f6Cw9390z$ chmod -R /tmp/tmp.2f6Cw9390z/
chmod: missing operand after ‘/tmp/tmp.2f6Cw9390z/’
Try 'chmod --help' for more information.
bandit23@bandit:/tmp/tmp.2f6Cw9390z$ chmod 777 -R /tmp/tmp.2f6Cw9390z/
bandit23@bandit:/tmp/tmp.2f6Cw9390z$ chmod +x run.sh
bandit23@bandit:/tmp/tmp.2f6Cw9390z$ cp run.sh /var/spool/bandit24/foo
bandit23@bandit:/tmp/tmp.2f6Cw9390z$ cat pass
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
```

## What I learned
- Using cron jobs to understand automated system tasks
- Creating shell scripts to extract privileged information
- Managing file permissions for proper execution

## References 
- chmod for setting file permissions
- Basic bash scripting

# Level 24 → Level 25
Brute force a 4-digit pincode to a network service

## My solve
I needed to connect to a service on port 30002 that required the bandit24 password plus a 4-digit pincode. Since there are only 10,000 possible combinations (0000-9999), I created a script to try all possibilities.

I wrote a bash script that generates all possible pincodes and submits them along with the password to the service until it finds the correct one.

```bash
run.sh file

#!/bin/bash

(for i in {0001..9999}; do
echo "gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 $i"
done ) | nc localhost 30002

bandit24@bandit:~$ mktemp -d | cd
bandit24@bandit:~$ mktemp -d
/tmp/tmp.hX62xiIM4d
bandit24@bandit:~$ cd /tmp/tmp.hX62xiIM4d
bandit24@bandit:/tmp/tmp.hX62xiIM4d$ nano run.sh
Unable to create directory /home/bandit24/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.

bandit24@bandit:/tmp/tmp.hX62xiIM4d$ chmod +x run.sh
bandit24@bandit:/tmp/tmp.hX62xiIM4d$ ./run.sh
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Wrong! Please enter the correct current password and pincode. Try again.
Correct!
The password of user bandit25 is iCi86ttT4KSNe1armKiwbQNmB3YJP3q4
```

## What I learned
- How to implement a simple brute force attack
- Writing shell scripts to automate repetitive tasks
- Working with network services via command line

## References 
- Bash scripting for loops
- Using netcat to connect to network services
