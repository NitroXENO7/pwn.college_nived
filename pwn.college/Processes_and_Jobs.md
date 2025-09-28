# 1. Listing Processes
Using ps to view and identify running processes

## My solve
**Flag:** `pwn.college{UKL82hrKIs7ZXpmPnSTaPplawx_.QX4MDO0wiMxkjNzEzW}`

Used ps to list all running processes, identified the renamed /challenge/run program, and executed it directly to get the flag.

```
hacker@processes~listing-processes:~$ ps auxww
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND                                                               
root           1  0.0  0.0   1056   640 ?        Ss   07:03   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h                                                                                                                 
root           8  0.0  0.0 231708  2560 ?        S    07:03   0:00 /run/dojo/bin/sleep 6h                                                
root         133  0.0  0.0   4132  2560 ?        S    07:03   0:00 /challenge/24284-run-25677                                            
root         136  0.0  0.0   2744  1280 ?        S    07:03   0:00 sleep 6h                                                              
hacker       138  0.0  0.0 231576  3520 pts/0    Ss   07:03   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint                                                                                                      
hacker       144  0.0  0.0 231576  3520 pts/1    Ss   07:03   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint                                                                                                      
hacker       150  0.0  0.0 231940  4160 pts/0    S+   07:03   0:00 /run/dojo/bin/bash --login                                            
hacker       153  0.0  0.0 231576  3520 pts/2    Ss   07:03   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       165  0.0  0.0 231940  4160 pts/1    S    07:03   0:00 /run/dojo/bin/bash --login
hacker       166  0.0  0.0 231576  3520 pts/3    Ss   07:03   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       174  0.0  0.0 231576  2880 pts/4    Ss   07:03   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       186  0.0  0.0 231576  3520 pts/5    Ss   07:03   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       192  0.0  0.0 231940  4160 pts/2    S+   07:03   0:00 /run/dojo/bin/bash --login
hacker       194  0.0  0.0 231940  4160 pts/3    S+   07:03   0:00 /run/dojo/bin/bash --login
hacker       208  0.0  0.0 231940  4160 pts/4    S+   07:03   0:00 /run/dojo/bin/bash --login
hacker       218  0.0  0.0 231940  4160 pts/5    S+   07:03   0:00 /run/dojo/bin/bash --login
hacker       229  0.0  0.0 233600  3840 pts/1    R+   07:06   0:00 ps auxww
hacker@processes~listing-processes:~$ /challenge/24284-run-25677
Yahaha, you found me! Here is your flag:
pwn.college{UKL82hrKIs7ZXpmPnSTaPplawx_.QX4MDO0wiMxkjNzEzW}
```

## What I learned
How to use ps with options like -ef or aux to list all running processes and identify specific programs by their command paths.

## References 
pwn college description

# 2. Killing Processes
Using kill to terminate unwanted processes

## My solve
**Flag:** `pwn.college{YmLhiIsVxgH7UR93t7ZalnwhjXj.QXyQDO0wiMxkjNzEzW}`

Found the PID of the /challenge/dont_run process using ps, terminated it with kill, and then ran /challenge/run to get the flag.

```
hacker@processes~killing-processes:~$ ps auxwww
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   640 ?        Ss   07:09   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7  0.0  0.0 231708  2560 ?        S    07:09   0:00 /run/dojo/bin/sleep 6h
root         135  0.0  0.0   5204  3520 ?        S    07:09   0:00 su -c /challenge/.launcher hacker
hacker       136  0.0  0.0 231576  3520 ?        Ss   07:09   0:00 /challenge/dont_run
hacker       137  0.0  0.0 231708  2560 ?        S    07:09   0:00 sleep 6h
hacker       139  0.0  0.0 231576  3520 pts/0    Ss   07:09   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       145  0.0  0.0 231576  3520 pts/1    Ss   07:09   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       151  0.0  0.0 231576  3520 pts/3    Ss   07:09   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       156  0.0  0.0 231576  3520 pts/2    Ss   07:09   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       158  0.0  0.0 231940  4160 pts/0    S+   07:09   0:00 /run/dojo/bin/bash --login
hacker       166  0.0  0.0 231940  4160 pts/1    S+   07:09   0:00 /run/dojo/bin/bash --login
hacker       179  0.0  0.0 231576  3520 pts/4    Ss   07:09   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       187  0.0  0.0 231940  4160 pts/3    S+   07:09   0:00 /run/dojo/bin/bash --login
hacker       188  0.0  0.0 231940  4160 pts/2    S+   07:09   0:00 /run/dojo/bin/bash --login
hacker       201  0.0  0.0 231940  4160 pts/4    S    07:09   0:00 /run/dojo/bin/bash --login
hacker       214  0.0  0.0 233600  3840 pts/4    R+   07:10   0:00 ps auxwww
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{YmLhiIsVxgH7UR93t7ZalnwhjXj.QXyQDO0wiMxkjNzEzW}
```

## What I learned
How to use kill to terminate processes by their PID, allowing other processes to run.

## References 
pwn college description

# 3. Interrupting Processes
Using keyboard shortcuts to interrupt running processes

## My solve
**Flag:** `pwn.college{cE9V-zm49pbdjcSFerdxF5ibtLw.QXzQDO0wiMxkjNzEzW}`

Ran /challenge/run which wouldn't give the flag until interrupted, used Ctrl-C to send an interrupt signal, and obtained the flag.

```
hacker@processes~interrupting-processes:~$ /challenge/run 
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{cE9V-zm49pbdjcSFerdxF5ibtLw.QXzQDO0wiMxkjNzEzW}
```

## What I learned
How to use Ctrl-C to send an interrupt signal to a running process in the terminal.

## References 
pwn college description

# 4. Killing Misbehaving Processes
Using process management to handle resource conflicts

## My solve
**Flag:** `pwn.college{QbEwPbM0q91VhvWw3NQFZPSREXE.0FNzMDOxwiMxkjNzEzW}`

Found and killed the decoy process that was hogging the named pipe, then ran the challenge program to get the flag.

```
hacker@processes~killing-misbehaving-processes:~$ ps auxww
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.2  0.0   1056   640 ?        Ss   07:19   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7  0.1  0.0 231708  2560 ?        S    07:19   0:00 /run/dojo/bin/sleep 6h
root         138  0.0  0.0   4132  1280 ?        S    07:19   0:00 /bin/bash /challenge/.init
root         139  0.0  0.0   4132  1280 ?        S    07:19   0:00 /bin/bash /challenge/.init
root         140  0.0  0.0   5204  3520 ?        S    07:19   0:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
root         141  0.0  0.0   2744  1280 ?        S    07:19   0:00 sleep 6h
root         142  0.0  0.0   2744  1600 ?        S    07:19   0:00 sleep 6h
hacker       143  0.2  0.0  13516  9280 ?        Ss   07:19   0:00 /usr/bin/python /challenge/decoy
hacker       145  0.2  0.0 231576  3520 pts/0    Ss   07:19   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       151  0.2  0.0 231576  3520 pts/2    Ss   07:19   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       152  0.2  0.0 231576  3520 pts/1    Ss   07:19   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       163  0.0  0.0 231972  4160 pts/0    S+   07:19   0:00 /run/dojo/bin/bash --login
hacker       165  0.2  0.0 231576  3520 pts/3    Ss   07:19   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       178  0.2  0.0 231576  3520 pts/4    Ss   07:19   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       183  0.0  0.0 231972  4160 pts/1    S+   07:19   0:00 /run/dojo/bin/bash --login
hacker       185  0.0  0.0 231972  4160 pts/2    S+   07:19   0:00 /run/dojo/bin/bash --login
hacker       202  0.0  0.0 231972  4160 pts/3    S    07:19   0:00 /run/dojo/bin/bash --login
hacker       210  0.0  0.0 231972  4160 pts/4    S+   07:19   0:00 /run/dojo/bin/bash --login
hacker       220  0.0  0.0 233600  3840 pts/3    R+   07:20   0:00 ps auxww
hacker@processes~killing-misbehaving-processes:~$ kill 143
hacker@processes~killing-misbehaving-processes:~$ /challenge/run 
Sending the flag to /tmp/flag_fifo!
^C
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo 
pwn.college{5-lq.JhtJjveoHHRP2-7TnDjgOrzG4Kp4W8qbMjzGcV8-Kv}
pwn.college{SMvt-hIbekdEPfswinA5ury5anVu4y2fTsLFcw6kTY6tYp3}
pwn.college{BmRHcBRiJ78jCzWQxlycwH.WoLAFoA94aGl5CT5lor8MuZL}
pwn.college{u4OoCGRhjx4lNlpU2oN.PcajWu-GV8DrrYLvgM6VFZ9GsV.}
pwn.college{n1KOsdMQag21ucpAfrl.npkUhg-WigJZnTF5xSchs-uLoZE}
pwn.college{liG42brempu271WtH70mwleDUEzOjZNfi7Q8cv32hn2iOwC}
pwn.college{AcsYmWcsQqvbqM0VY9nNUSZA2INgHVwXmTPwjseGVJfQkzN}
pwn.college{Vz.qyhegNyLe94ILTb2J7S73FEBkuY4YKLEm3jj8vmyV6bf}
pwn.college{0aALwp3zp9eQ.CS.rMCtmGohHJE.ASGg6trGPddIsViYPw6}
pwn.college{WCkvWrK1V5JRxHpiKlItg8IsGaEg3sSizU26iwMFPJWhMLV}
pwn.college{XU.yZxUTh0Y0Ncq1608MJjyVu6mSQmULnwjyk4wQZtu0qGQ}
pwn.college{LMFVLAjZPgDmfDXEo6yKh3C56h7e3DzVaIG6k3H1EYd4Rpy}
pwn.college{LKf6R48UFvojn226zaEOlb9.o4zcbWhK-Cg2hi2OQ5rS6B4}
pwn.college{8MalZM3VfNsjC4RlPbTXbPl7SfgoV4klV5u20dezez4iCxW}
pwn.college{AU4AzzoDXa43o0Z-WoJBz5mGz9XR9ilU7FSs-bIPQLQ9ok0}
pwn.college{-BJrBMBoTE6JCMlfQOsGyx7z7A2XgUDAU13INcBjLNh8DZy}
pwn.college{4Hf6SbkCfgAPGuh1cGGN419.3kPrycmpFQyN5vwq5RZFESq}
pwn.college{9c65RWMRar4bTK8AQhqHcxEiooVL5uMwNY9kvWStaEJqjzw}
pwn.college{Be-w6iyxshYNArNu.SwF93EvzLeiJwCmwjatYBHdRUm4GUk}
pwn.college{yrurO5lmPYUZoYx9EuVfyQ4CmvGO-4tNswf3dASOjM2rBl3}
pwn.college{o3SnOT.gmNnqav00yN96sHo6L3lyoj2uU2luipLDn07GV11}
pwn.college{wJX2kQH3.B6kL0iWzqytSLkLWVt8kc9uhYB.vWhdYOsH50s}
pwn.college{kykjkAoC0OhAXyFasCiuXRyWHuiBFP02za.FxuhDcOzqW11}
pwn.college{fiRVR6zhnZCt5DADKm85WeQHELSZZLCDOjVC5kOQIBIcRp1}
pwn.college{f5BG0ijU5FjzGUv-TYUyWs0vT3GEjajSI7ynitY2AavP-Ou}
pwn.college{xqrQKdMouwGRvkS-gM-dcVi5X3ON05rvTenHIMIUWn9rKnE}
pwn.college{60q0G341PrpX1sseZl3PFmuQZbGylhMTSwyWts-jSpZ5Em4}
pwn.college{RguiaGjobGMduuXLIJMRiaRxn5oJflVK2SivwU2Na1CrmrO}
pwn.college{cs2DE.MotkMsZ7VMq6ebZeSWjwd1ksEMJuiJ-trpzZIzRCI}
pwn.college{GnkcejZNnqFNyMkPXAlgEofHcbw.Onpby2SPGr9BGY-Dkcs}
pwn.college{OAj8bCvYnuIXn3P1k4dXYiz6Gwh4pGZu-LqQWOfLREX0-eu}
pwn.college{eD6uGNg1HKyRSAyxE36ck1niO3dhWRt5RkktOzc7ftYxU8v}
pwn.college{Sh8KXYQ9eA4t6q3lNxCns.5y0CDVi3z5cL6WWzbVQ..NPSM}
pwn.college{zF-fd8w-C7ZFbvnhmRYZClX1CjTLkh4J-MXVXlMCXwIcA6h}
pwn.college{IHRbhy5I6N8Ty7xGcCM6snd3uDuiSy9xqQrrIyYg92DLutb}
pwn.college{8byIFOq2DMeFyk.-PytpyjOqBVIQX4OmWlIPiJrqpswXRFm}
pwn.college{ISd5Ee181OF1feq5qwwM6EMHUylBrMqzgb0HQenNb7lDeqQ}
pwn.college{oBedVHsRou0mssS9YAv4f1tOhcljD9d6QHvCul1Y6cJqzc7}
pwn.college{7zivms8.i7UpXPTyFP3t28oO0QTQoYC.UkhlQ8yTAe36TkU}
pwn.college{aPKCqHGanIfkltOC2CsQVd5kfjqd3IrfQu79.opXt61tve7}
pwn.college{r0DXfuuFL3SAka5KItjWADGt1tC4lIRinMUPb8tvnz1xXa0}
pwn.college{zzP59m1KAhWYFPv9eQYHt8bw8v9BrNS2uJlCwqDGHuSn31g}
pwn.college{9fDbEb91jyopceHh4HaFL0zT-f7Hb.6qCdw1ps11.wG.8kE}
pwn.college{eBhlwNp2oONXopMJWw6T-5E6P0DZM-uFZWpbHP4Cu5..jJw}
pwn.college{LMzRZUCuEzJE3BLpPLSoUhmWgI2qgFFh1HKmgXs9LmX.UOC}
pwn.college{WAjimG5Fj82lGy5CxTPE6ucgd7YTe106nm.y01xlUPpe8Gr}
pwn.college{V6totQFreWgXQPYK6xHy7DheIrhO2V4aTIdYUnw8NgqbUFt}
pwn.college{s.VUFKqgo926lRCu-JFQzHtvN5Q.fbvDD-UaVXYhY7FuX4j}
pwn.college{gWv5MBG6XHPTyFgntjSswazHUrIGXl-kEmmIqFY68z0jGv1}
pwn.college{H9aiEWwm.u4.yIKqqMixaFFNCll8Ch8E1-kYBqptAI28MzQ}
pwn.college{3r9BnPn8QcBCP2poRVH2m.MzPVqXiCWw4dTkwOD-7mjZxOK}
pwn.college{KBljcONi7ep4UATzEdWzAZ01-kKTH3rLefBM0LKs8Fty8aq}
pwn.college{CRTJi9VWieolBKzCvgVv23TpD1lMyKIl1BQ5DTGoJlPgsCD}
pwn.college{L4E-l7nb5sPwQcA82j4LiJUR2LeS9zHhc7WKntB.P9cGtNW}
pwn.college{V0kETNG3QufnQ84X49EMZf2o6MDFHsQfdTHzTuYW5PBF8gz}
pwn.college{E9hXMoQGzL-XzICcS1XSHBRxYC493g10j2ibBlnl5UlRtDp}
pwn.college{SXKipQelK2jcTahPxXYfJfmYxa2S4D4Hro9VjUw9Kr2aQEr}
pwn.college{JEhBHrOr0nZpkU-wrf7zP05vNWFqmtkLGZ9nHQ.0adMfYVn}
pwn.college{WZu0QKlzSwO68FX1pvn7kwj0fnFBMInwApHQoEiXbWxSA3p}
pwn.college{GlGXsM0CApyVIFYMJrO85gxZSynjg4InzOl11uQgYrcEdKj}
pwn.college{FwFLfFV8gDqz046lV.a42OtsDuOf3xB-QeMmm9rV5hQm9SG}
pwn.college{5V2h3U7HDG3-bR3vQG8vwmmhGBqS2K6YPXZzu--fZD4jeTa}
pwn.college{NqDitI5Cq8wPuoCRhnrW6xReJ5kcoErxknHOs0D3D0IkjxE}
pwn.college{ZWKe9kK4wzy1poL0ilQ.LJ5GGFsJs-w0yAemBWTvIxjChUf}
pwn.college{XUvqfSl3GdoHVP-Yh0U3ZsYKtSg5xTqHT6-pgCw91g3kvko}
pwn.college{frQEKdu35fZDkxQPajIC-DpG1x2zFPDekFb2BjqBOm1NHbV}
pwn.college{C.7zss2WRXjdJQrOevlXFCpU6uwMHWVu.NiZgrcjcRISQny}
pwn.college{S9WNxGRq6-VeMBgTxLAWxrU2eqQb7b1niHnozSySyMKHxN-}
pwn.college{RmrBYdBE6FIC2eLxojxsCj1v57c-yiOGJt4n14tlxzjeG8y}
pwn.college{HIOvctI5VADNWKgyOq-c6f3SAknKhiJCTk9PTQ6Galx66iX}
pwn.college{KFFnkXjRxtui2WdIwEbFvEQ9ZV2t7pz83fi748jgJkXjgWF}
pwn.college{2XkFCn23JptrZws3SY0ht32zyw5PZ7mDo751QkoMkaJ9Gwf}
pwn.college{5HZsNlVczmAzK1L3-xb2-OYsWg7GG.yg-WbO.y-pMLwABRy}
pwn.college{1UQnthFMA5XoKE6u9a95fATaFJUF2emBz7T7YnA3Sze6JLw}
pwn.college{C6B..o2Loe1mfjjks614iLVVtPw.n33WyPUaVqbW5O3CsRj}
pwn.college{w3ueAZDIWq81wRLqZ.MyvV.Lvj9ii7yqXmg754g0N1g2tXW}
pwn.college{urMGrwPAjrflCbhQ1-wpuoJD4gZgUaaHz8GMZ6EROL7n73C}
pwn.college{Mpqg7ueGqS9bmn55cOVni5LeZRIC2XcaBkvKoxL2OEC2PnT}
pwn.college{g2si4BLT7JRdW3xeElOpZdsf6dvqRV-tKKphIsFQUl-S5AA}
pwn.college{y48.DYSq9WFuqBmFAcF2vLhHLrxqOQDwguFYuKhtp3yejAr}
pwn.college{xuHSN3QNvcvSdvWFFQjY.h9KBtLIwtZ3lBqZ0l-HqEx5oVF}
pwn.college{DuRSCKd4MUsBTaHC98V-QmDnwazGDA6CaKJYqToC2ZIQZ8E}
pwn.college{TLWyIh7J6fHh3LR1IusaWe7mcqpeBwR2pgyu3YXsUqhQFgU}
pwn.college{UaYQWkqDGxt-.QffJba8bZHxWYQHxxZEhTmWYH-p5Ywi0Ka}
pwn.college{BuyxeETncs-0hZSgEFVv.7mmz1ilT40nARVnIbm33gVHkKV}
pwn.college{mwXIiu84q5IDJwers6Kt1GCEhIRp3ghPKCM-Jg3squfwcoh}
pwn.college{D5rP2XetK3eK6-8DVuNB8FQVNIspyBjUm3HdwvKXXwBIPhB}
pwn.college{RG8dJ3-FT3V7WogOIWVta2TrEemzqdoFYKZhNPG9IJjj8AE}
pwn.college{f48spKjfwadpVy12pPrzylKQ9cXHc-xsk34YkmOTc9gKHeu}
pwn.college{9Ootew4fPD7GNjoWHtVbKfwF0fCFn1MU04QG.LmXsOaq6k5}
pwn.college{1pUCG9YhlRUA5t0egizPzguVAI1jV7ctdpgkKMu3oh1dHrr}
pwn.college{cmiYz6-6TBcJyWKqtVw6I8MJ5RSAa-3weoWH-heF9Qh4BLx}
pwn.college{ZhBXzvrG19GsyBbznR7N5R5m-H7T1qbW.Nkd8PiHvr-yymI}
pwn.college{zoG3nqyCOdATQO7n0QkkunF03E39X5raVd1ibCxtC9BznXs}
pwn.college{.RKmJmG7Y548y1TMlM6DSVlLUNhs2W1vBgrAUqWHQK-qDNb}
pwn.college{8mooCsXYBbUyzdcm0SF9tFggivm-MGQh3DSKZ3anT.RJK4s}
pwn.college{DCszxkgfw-HkUN.GGMGtk1CtwYJbQZzsBZtp9eKOTiNVph2}
pwn.college{MhZKwuupY.0Lg6Hc7c7J4SBo06idr.aEfPgtoD5eLYTV-mI}
pwn.college{UzBTahmCIlZQvaC3y3pwL4fR4ldW3aTb.zc0YQHAjZgyneT}
pwn.college{aUoem669CBZ.4FOXDK1ETBwoXgJiE6SKmobRdkhwZJlPTy2}
pwn.college{XdK.wVsVUKcBPvbDLr8FZPvr5Q0xauaSNhTJJjuxckgPu7O}
pwn.college{IurnwMPjD4oOZKzwqn1gTAI5SfyG-GGZeZ5B29EMsUX9eWz}
pwn.college{OMDPIuP4Am47iEwWumItzFU1-ELqJu6b8WusB3zQ1VqtlEG}
pwn.college{VBumYH6Il0j30gp8h3x.SNX.0.NQ1.2U-ESM1z3fuaW.RDT}
pwn.college{0Mb3Ryj1-Jpz1kauGxwjn8lo-.rR3G0lChWKJEXCYSEnyBp}
pwn.college{6dlTuOcBzcKDEmHvbZbvVD9k4HF5Gau5itHYYApJsNTqu4D}
pwn.college{PXmOwah2zSUBeQE1J.QwSOUK7OLv1maAQac.ccH7gCHBc9c}
pwn.college{XyasSVUXoPomsUMB72znIxU5Ia.rZSOTXQPq4mqA.inz3H7}
pwn.college{rXtispMGOtBg6aW3USI.AAU4O254oFybHaFupDHp322PMaf}
pwn.college{Gx3IOy8KDRyAAK9gbZzfcVa3XBYPgYvxbrSHnQs-CxJS80T}
pwn.college{t1PwLuKoIdsmgJhX7wyIR8UcaVkfeGHlmrO3mCQiTV6Cyu6}
pwn.college{YXwYGvu-0HELhGld3EK5Cbw3WVVfPLrKV2AdSvJ8zY2-4WK}
pwn.college{3kAxhbS5IwU9vlXfHI5KzNU85IqgAtYDQn9bBcCYY.1mMur}
pwn.college{VqszgMmxQCTpjO9ukcSXmWbzwuIUoo-D8nFnsz6DA6eYG2O}
pwn.college{N70cjJok49vUY6wevgPPImHvRYldbD5yGxEy..2puswb-fD}
pwn.college{pVHJLnF5NMW7Df1oi7.Y2UtXfj.J02edSgPWU2UmoD1AMlY}
pwn.college{OKXrvXSyzONA5cDa6Zx0btz7zwknQbERsxQH8vBZNC0ShzZ}
pwn.college{ow1a3vu9DDLLXQx1e2Yk2JPch79da1Cc.gCU6YAo8-s-0O2}
pwn.college{6n4SlcAjaJKe2f-mNjoOFoZxI37xnjpcNddZzMZmx9kk4dv}
pwn.college{1Lo0IfDUl4k8L17Ncz.6FET2AaqJdjG4Fe4CgFmiIrW6Pzj}
pwn.college{ginGYVnobUCc9pRDA5qXFNkflb3ht.ka4OTMgGt4QocGzVW}
pwn.college{DLJGHBuQDiMffyu1SZSAJo5UkmBvH.-s3qx0X.MFZsJmI2-}
pwn.college{TYzqN-IiqwyexdBUsZgtjbn3XhfnjzfKAFg.TBGDkwKFrLY}
pwn.college{4CKWB4h7ic8uc-qixcE3UK5WR870wwLycnCVbtjXFrJiqaE}
pwn.college{Z4bj1MtKtmBLm-.f1cPp8AcCmmI8rmxrkE6ONDt3St8cjG3}
pwn.college{uWbRarVfV3fafQDz5nvZs3AanizPJztLGh-7DOHGVTGmHqm}
pwn.college{JcxcpB4RshF2E6yUN61BXsnOq6o858-vEtBkkfEVrtdCnE0}
pwn.college{QxUGha5ozu4P6ARri13sizmBM6-FLa7JTmSmid1.hLV6y1v}
pwn.college{0IKimLCL6at.RV.dFrDTYWY4wUlFcfzeeYbkgfGe6W9tpNw}
pwn.college{tX.vWHX1BeAW8czBQrsumJdzjW.e6GH1KhmOGwIKb6L9kgB}
pwn.college{dH9MFW3LA0cASaE8s.ViqUiAzeQdv9--XtdkfIKq.kZtJ2Y}
pwn.college{YttKpy7tYc8uoXbh9-ZJesLe.B8nkcJpFkBuhvoI.PhokwM}
pwn.college{EbRq5RWT.oReZyzzjuOizM5i0XL7949Qa0sO6jVtjlmcogB}
pwn.college{UxpKVS1k4eq.bVFnWLjM7eaPiBpAumiAylclLRLmpQFoUkm}
^C                                                                       
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo 
pwn.college{QbEwPbM0q91VhvWw3NQFZPSREXE.0FNzMDOxwiMxkjNzEzW}
```

## What I learned
How to identify and terminate processes that are interfering with resources needed by other programs.

## References 
pwn college description

# 5. Suspending Processes
Using keyboard shortcuts to suspend running processes

## My solve
**Flag:** `pwn.college{8Qxa36SrEZ19XuIGhbf21mU17c3.QX1QDO0wiMxkjNzEzW}`

Ran /challenge/run, suspended it with Ctrl-Z, then ran a second instance of /challenge/run to get the flag.

```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         213     179  0 07:23 pts/4    00:00:00 bash /challenge/run
root         215     213  0 07:23 pts/4    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         213     179  0 07:23 pts/4    00:00:00 bash /challenge/run
root         220     179  0 07:23 pts/4    00:00:00 bash /challenge/run
root         222     220  0 07:23 pts/4    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{8Qxa36SrEZ19XuIGhbf21mU17c3.QX1QDO0wiMxkjNzEzW}
```

## What I learned
How to use Ctrl-Z to suspend a running process and move it to the background.

## References 
pwn college description

# 6. Resuming Processes
Using fg to resume suspended processes

## My solve
**Flag:** `pwn.college{sMQK-N8qOSt6UiQYyae2TwXyIuQ.QX2QDO0wiMxkjNzEzW}`

Ran /challenge/run, suspended it with Ctrl-Z, then used fg to resume it and get the flag.

```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg /challenge/run
/challenge/run
I'm back! Here's your flag:
pwn.college{sMQK-N8qOSt6UiQYyae2TwXyIuQ.QX2QDO0wiMxkjNzEzW}
Don't forget to press Enter to quit me!

Goodbye!
```

## What I learned
How to use the fg command to resume suspended processes and bring them back to the foreground.

## References 
pwn college description

# 7. Backgrounding Processes
Using bg to resume suspended processes in the background

## My solve
**Flag:** `pwn.college{8gHQ5N9YAp2Cq1PoqZV-sSLZPUS.QX3QDO0wiMxkjNzEzW}`

Ran /challenge/run, suspended it with Ctrl-Z, resumed it in the background with bg, then ran a second instance to get the flag.

```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         213 S+   bash /challenge/run
root         215 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg /challenge/run
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         213 S    bash /challenge/run
root         223 S    sleep 6h
root         224 S+   bash /challenge/run
root         226 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{8gHQ5N9YAp2Cq1PoqZV-sSLZPUS.QX3QDO0wiMxkjNzEzW}
```

## What I learned
How to use the bg command to resume suspended processes in the background while maintaining control of the terminal.

## References 
pwn college description

# 8. Foregrounding Processes
Using fg to bring background processes back to the foreground

## My solve
**Flag:** `pwn.college{ULfErJrFX6c4HMUugYqi2pvOFUk.QX4QDO0wiMxkjNzEzW}`

Ran /challenge/run, put it in the background, then used fg to bring it back to the foreground to get the flag.

```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run                                                                      
hacker@processes~foregrounding-processes:~$ bg /challenge/run
bash: bg: /challenge/run: no such job
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg /challenge/run
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.

hacker@processes~foregrounding-processes:~$ fg /challenge/run
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{ULfErJrFX6c4HMUugYqi2pvOFUk.QX4QDO0wiMxkjNzEzW}
```

## What I learned
How to use the fg command to bring background processes back to the foreground for interaction.

## References 
pwn college description

# 9. Starting Background Processes
Using & to launch processes in the background

## My solve
**Flag:** `pwn.college{orJJxEtcx2IMZApF8LpovYwzcc3.QX5QDO0wiMxkjNzEzW}`

Ran /challenge/run in the background by appending & to the command to get the flag.

```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 198
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{orJJxEtcx2IMZApF8LpovYwzcc3.QX5QDO0wiMxkjNzEzW}

[1]+  Done                    /challenge/run
```

## What I learned
How to start processes directly in the background by appending & to the command.

## References 
pwn college description

# 10. Process Exit Codes
Using exit codes to pass information between programs

## My solve
**Flag:** `pwn.college{o2Fym4DGijOAqLnX67_cs_RG7X_.QX5YDO1wiMxkjNzEzW}`

Ran the get-code program, captured its exit code, and passed it to submit-code to get the flag.

```
hacker@processes~process-exit-codes:~$ /challenge/get-code 
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
218
hacker@processes~process-exit-codes:~$ /challenge/submit-code 218
CORRECT! Here is your flag:
pwn.college{o2Fym4DGijOAqLnX67_cs_RG7X_.QX5YDO1wiMxkjNzEzW}
```

## What I learned
How to use $? to access the exit code of the previously run command and use it in subsequent commands.

## References 
pwn college description
