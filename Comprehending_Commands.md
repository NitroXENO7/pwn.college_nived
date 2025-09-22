# 1.cat: not the pet, but the command!
you cat command to read file

## My solve
**Flag:** `pwn.college{UJR92B2ijWdomeEAJvzMjGx_OxM.QXxcTN0wiMxkjNzEzW}`

used cat flag to read the flag file

```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{UJR92B2ijWdomeEAJvzMjGx_OxM.QXxcTN0wiMxkjNzEzW}

```

## What I learned
how to read contents of file with cat command

## References 
pwn college description

# 2.catting absolute paths
Using cat command with absolute paths

## My solve
**Flag:** `pwn.college{4dtStQyzrzwcr8Uwn2ztcshHnTb.QX5ETO0wiMxkjNzEzW}`

used cat command with argument /flag which is the flag file located in root directory
```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{4dtStQyzrzwcr8Uwn2ztcshHnTb.QX5ETO0wiMxkjNzEzW}

```

## What I learned
how to use cat with absolute paths

## References 
pwn college description

# 3.more catting practice
practice with cat with absolute paths

## My solve
**Flag:** `pwn.college{wFXdj7UCFzmNrloEN0RtORAJ5hI.QXwITO0wiMxkjNzEzW}`

used cat with absolute path to flag 
```
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /lib/file/flag. Go cat it out **without** cding into that directory!
hacker@commands~more-catting-practice:~$ cat /lib/file/flag 
pwn.college{wFXdj7UCFzmNrloEN0RtORAJ5hI.QXwITO0wiMxkjNzEzW}
```

## What I learned
Using cat with absolute paths

## References 
pwn college description

# 4.grepping for a needle in a haystack
use grep to search for flag in a very big file

## My solve
**Flag:** `pwn.college{0m5ZX4z_XM0Le9pSJEhPiPl9Eh-.QX3EDO0wiMxkjNzEzW}`

used grep command with arugments pwn.college and location of file to get flag from data.txt

```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt 
pwn.college{0m5ZX4z_XM0Le9pSJEhPiPl9Eh-.QX3EDO0wiMxkjNzEzW}
```

## What I learned
using grep command to find lines in a file with specified string

## References 
pwn college description

# 5.comparing files
use diff command to compare two files with fake and real flags to find flag

## My solve
**Flag:** `pwn.college{0ieV7NRJ9lRNa8WeuFjJ9Ef0bja.01MwMDOxwiMxkjNzEzW}`

used diff command with first and second file
```
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt 
74a75
> pwn.college{0ieV7NRJ9lRNa8WeuFjJ9Ef0bja.01MwMDOxwiMxkjNzEzW}

```

## What I learned
learned to use diff command

## References 
pwn college description

# 6.listing files
use ls to changed name of run file

## My solve
**Flag:** `pwn.college{UGoinkn8zyv9qViOwkFkcuztctB.QX4IDO0wiMxkjNzEzW}`

cd'd into challenge folder , used ls to list all items and ran the renamed file.

```
hacker@commands~listing-files:~$ cd /challenge/
hacker@commands~listing-files:/challenge$ ./16510-renamed-run-12673 
Yahaha, you found me! Here is your flag:
pwn.college{UGoinkn8zyv9qViOwkFkcuztctB.QX4IDO0wiMxkjNzEzW}
```

## What I learned
how to list all items in a folder

## References 
pwn college description


# 7.touching files
create file with touch command

## My solve
**Flag:** `pwn.college{YjN0SOxv4vwbkfNbYOd44Glhgwv.QXwMDO0wiMxkjNzEzW}`

cd'd into tmp folder , used touch to create 2 files and ran the run program.

```
hacker@commands~touching-files:~$ cd /tmp/
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{YjN0SOxv4vwbkfNbYOd44Glhgwv.QXwMDO0wiMxkjNzEzW}
```

## What I learned
how to create files with touch command

## References 
pwn college description

# 8.removing files
remove file with rm command

## My solve
**Flag:** `pwn.college{QRCxR6_vIySZWMwwBEW0t-0dM6u.QX2kDM1wiMxkjNzEzW}`

used rm to delete delete_me file and ran the run program.

```
hacker@commands~removing-files:~$ rm delete_me 
hacker@commands~removing-files:~$ /challenge/check 
Excellent removal. Here is your reward:
pwn.college{QRCxR6_vIySZWMwwBEW0t-0dM6u.QX2kDM1wiMxkjNzEzW}
```

## What I learned
how to delete file with rm command

## References 
pwn college description

# 9.moving files
move files with mv command

## My solve
**Flag:** `pwn.college{ss2ARRa6uLk2Rwe7x-owwK3DEo7.0VOxEzNxwiMxkjNzEzW}`

used mv to move flag file to /tmp/hack-the-planet and ran the check program.

```
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check 
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{ss2ARRa6uLk2Rwe7x-owwK3DEo7.0VOxEzNxwiMxkjNzEzW}
```

## What I learned
how to move file with mv command

## References 
pwn college description

# 10.hidden files
use ls with argument -a to see hidden files

## My solve
**Flag:** `pwn.college{c_dNAIjkAgnxeBjwXH2lWnfGy6H.QXwUDO0wiMxkjNzEzW}`

used ls with -a argument and got the flag

```
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.                      bin        etc    lib64   nix   run   tmp
..                     boot       home   libx32  opt   sbin  usr
.dockerenv             challenge  lib    media   proc  srv   var
.flag-203652099610814  dev        lib32  mnt     root  sys
hacker@commands~hidden-files:/$ cat .flag-203652099610814 
pwn.college{c_dNAIjkAgnxeBjwXH2lWnfGy6H.QXwUDO0wiMxkjNzEzW}
```

## What I learned
seeing hidden files with ls

## References 
pwn college description

# 11.An Epic Filesystem Quest
follow clues to find the flag file

## My solve
**Flag:** `pwn.college{E3gJZ8a69xSfVLHDVCgYh8QWWSP.QX5IDO0wiMxkjNzEzW}`

use ls, cd and cat to move around the system using clues and find the flag

```
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
README  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin     challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ cat README 
Lucky listing!
The next clue is in: /usr/share/sgml/dtd

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/share/sgml/dtd/
hacker@commands~an-epic-filesystem-quest:/usr/share/sgml/dtd$ ls 
xml-core
hacker@commands~an-epic-filesystem-quest:/usr/share/sgml/dtd$ ls -a
.  ..  .MEMO  xml-core
hacker@commands~an-epic-filesystem-quest:/usr/share/sgml/dtd$ cat .MEMO 
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/drivers/net/can/c_can

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:~$ cd /opt/linux/linux-5.4/drivers/net/can/c_can
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/net/can/c_can$ ls
Kconfig  Makefile  c_can.c  c_can.h  c_can_pci.c  c_can_platform.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/net/can/c_can$ ls -a
.  ..  .BRIEF  Kconfig  Makefile  c_can.c  c_can.h  c_can_pci.c  c_can_platform.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/net/can/c_can$ cat .BRIEF 
Lucky listing!
The next clue is in: /opt/splitmind/.git/logs

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:~$ cd /opt/splitmind/.git/logs/
hacker@commands~an-epic-filesystem-quest:/opt/splitmind/.git/logs$ ls
BLUEPRINT  HEAD  refs
hacker@commands~an-epic-filesystem-quest:/opt/splitmind/.git/logs$ ls -a
.  ..  BLUEPRINT  HEAD  refs
hacker@commands~an-epic-filesystem-quest:/opt/splitmind/.git/logs$ cat BLUEPRINT 
Yahaha, you found me!
The next clue is in: /usr/local/lib/python3.8/dist-packages/setuptools/tests/__pycache__
hacker@commands~an-epic-filesystem-quest:/opt/splitmind/.git/logs$ cd /usr/local/lib/python3.8/dist-packages/setuptools/tests/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/setuptools/tests/__pycache__$ ls
NUGGET                                  test_build_meta.cpython-38.pyc          test_install_scripts.cpython-38.pyc
__init__.cpython-38.pyc                 test_build_py.cpython-38.pyc            test_logging.cpython-38.pyc
contexts.cpython-38.pyc                 test_config_discovery.cpython-38.pyc    test_manifest.cpython-38.pyc
environment.cpython-38.pyc              test_core_metadata.cpython-38.pyc       test_namespaces.cpython-38.pyc
fixtures.cpython-38.pyc                 test_depends.cpython-38.pyc             test_packageindex.cpython-38.pyc
mod_with_constant.cpython-38.pyc        test_develop.cpython-38.pyc             test_sandbox.cpython-38.pyc
namespaces.cpython-38.pyc               test_dist.cpython-38.pyc                test_sdist.cpython-38.pyc
script-with-bom.cpython-38.pyc          test_dist_info.cpython-38.pyc           test_setopt.cpython-38.pyc
server.cpython-38.pyc                   test_distutils_adoption.cpython-38.pyc  test_setuptools.cpython-38.pyc
test_archive_util.cpython-38.pyc        test_easy_install.cpython-38.pyc        test_unicode_utils.cpython-38.pyc
test_bdist_deprecations.cpython-38.pyc  test_editable_install.cpython-38.pyc    test_virtualenv.cpython-38.pyc
test_bdist_egg.cpython-38.pyc           test_egg_info.cpython-38.pyc            test_warnings.cpython-38.pyc
test_bdist_wheel.cpython-38.pyc         test_extern.cpython-38.pyc              test_wheel.cpython-38.pyc
test_build.cpython-38.pyc               test_find_packages.cpython-38.pyc       test_windows_wrappers.cpython-38.pyc
test_build_clib.cpython-38.pyc          test_find_py_modules.cpython-38.pyc     text.cpython-38.pyc
test_build_ext.cpython-38.pyc           test_glob.cpython-38.pyc                textwrap.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/setuptools/tests/__pycache__$ cat NUGGET 
Yahaha, you found me!
The next clue is in: /usr/lib/R/library/translations/de/LC_MESSAGES
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/setuptools/tests/__pycache__$ cd /usr/lib/R/library/translations/de/LC_MESSAGES
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/translations/de/LC_MESSAGES$ ls
ALERT          R-grDevices.mo  R-methods.mo   R-stats.mo   R-tools.mo  RGui.mo       grid.mo      splines.mo  tools.mo
R-base.mo      R-graphics.mo   R-parallel.mo  R-stats4.mo  R-utils.mo  grDevices.mo  methods.mo   stats.mo    utils.mo
R-compiler.mo  R-grid.mo       R-splines.mo   R-tcltk.mo   R.mo        graphics.mo   parallel.mo  tcltk.mo
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/translations/de/LC_MESSAGES$ cat ALERT 
Lucky listing!
The next clue is in: /usr/share/tcltk/tcl8.6/encoding

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/translations/de/LC_MESSAGES$ ls  /usr/share/tcltk/tcl8.6/encoding
TIP-TRAPPED  cp1256.enc  cp857.enc  cp874.enc     euc-kr.enc      iso8859-10.enc  iso8859-6.enc  ksc5601.enc      macRomania.enc
ascii.enc    cp1257.enc  cp860.enc  cp932.enc     gb12345.enc     iso8859-13.enc  iso8859-7.enc  macCentEuro.enc  macThai.enc
big5.enc     cp1258.enc  cp861.enc  cp936.enc     gb1988.enc      iso8859-14.enc  iso8859-8.enc  macCroatian.enc  macTurkish.enc
cp1250.enc   cp437.enc   cp862.enc  cp949.enc     gb2312-raw.enc  iso8859-15.enc  iso8859-9.enc  macCyrillic.enc  macUkraine.enc
cp1251.enc   cp737.enc   cp863.enc  cp950.enc     gb2312.enc      iso8859-16.enc  jis0201.enc    macDingbats.enc  shiftjis.enc
cp1252.enc   cp775.enc   cp864.enc  dingbats.enc  iso2022-jp.enc  iso8859-2.enc   jis0208.enc    macGreek.enc     symbol.enc
cp1253.enc   cp850.enc   cp865.enc  ebcdic.enc    iso2022-kr.enc  iso8859-3.enc   jis0212.enc    macIceland.enc   tis-620.enc
cp1254.enc   cp852.enc   cp866.enc  euc-cn.enc    iso2022.enc     iso8859-4.enc   koi8-r.enc     macJapan.enc
cp1255.enc   cp855.enc   cp869.enc  euc-jp.enc    iso8859-1.enc   iso8859-5.enc   koi8-u.enc     macRoman.enc
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/translations/de/LC_MESSAGES$ cat /usr/share/tcltk/tcl8.6/encoding/TIP-TRAPPED 
Tubular find!
The next clue is in: /usr/share/javascript/jquery-ui/css

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/translations/de/LC_MESSAGES$ cd /usr/share/javascript/jquery-ui/css
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/jquery-ui/css$ ls
HINT  smoothness
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/jquery-ui/css$ cat HINT 
Great sleuthing!
The next clue is in: /usr/lib/python3/dist-packages/twisted/enterprise

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/jquery-ui/css$ ls /usr/lib/python3/dist-packages/twisted/enterprise
GIST-TRAPPED  __init__.py  __pycache__  adbapi.py
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/jquery-ui/css$ cat /usr/lib/python3/dist-packages/twisted/enterprise/GIST-TRAPPED 
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{E3gJZ8a69xSfVLHDVCgYh8QWWSP.QX5IDO0wiMxkjNzEzW}
```

## What I learned
general usage of cat, ls and cd commands

## References 
pwn college description

# 12.making directories
make a folder using mkdir and make a file in using touch

## My solve
**Flag:** `pwn.college{wDkJWSmBU_gjcI478JZyWug-wlr.QXxMDO0wiMxkjNzEzW}`

made a folder with mkdir and made a file in with touch

```
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ cd /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run 
Success! Here is your flag:
pwn.college{wDkJWSmBU_gjcI478JZyWug-wlr.QXxMDO0wiMxkjNzEzW}
```

## What I learned
using mkdir and touch to create files and folders

## References 
pwn college description


# 13.finding files
find flag file using find command

## My solve
**Flag:** `pwn.college{QyOSCba2cNqwkvf1ZiLjEWDEZMp.QXyMDO0wiMxkjNzEzW}`

use find command to find the flag file, additionally i used the -type f argument so it lists only files and not folders

```
hacker@commands~finding-files:~$ find / -type f -name flag
find: ‘/tmp/tmp.TpSOPGOVKK’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
/usr/share/icons/Adwaita/32x32/devices/flag
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/root’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
hacker@commands~finding-files:~$ cat /usr/share/icons/Adwaita/32x32/devices/flag
pwn.college{QyOSCba2cNqwkvf1ZiLjEWDEZMp.QXyMDO0wiMxkjNzEzW}
```

## What I learned
how to use find command to find files

## References 
pwn college description & google search about arguments for find command

# 14.linking files
make a symlink of a file

## My solve
**Flag:** `pwn.college{Itk1tV6A2sXRE4RR8_P6wkLPLpA.QX5ETN1wiMxkjNzEzW}`

used the ln -s command to symlink /flag to ~/not-the-flag so opening /challenge/catflag automatically opens /flag

```
hacker@commands~linking-files:~$ ln -s /flag ~/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag 
About to read out the /home/hacker/not-the-flag file!
pwn.college{Itk1tV6A2sXRE4RR8_P6wkLPLpA.QX5ETN1wiMxkjNzEzW}
```

## What I learned
How to symlink files

## References 
pwn college description 
