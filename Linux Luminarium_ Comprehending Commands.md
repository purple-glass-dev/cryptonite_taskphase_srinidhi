## Section 1: Cat, not the pet but the command
```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{gdEsSmh2QwtPr1gvN_ehfFeCJqX.dFzN1QDL3ITN0czW}
```

## Section 2: catting absolute paths
```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{A1RIZ_fSoPAN8fyxQcyabUDUQQ9.dlTM5QDL3ITN0czW}
```

## Section 3: more catting practice
```
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /usr/local/share/flag. Go cat it out **without** cding into that
directory!
hacker@commands~more-catting-practice:~$ cat /usr/local/share/flag
pwn.college{EgRtMcClCDZ3Dn7sPKEFJv2W8A-.dBjM5QDL3ITN0czW}
```

## Section 4: Grepping for a needle in a haystack
```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{Y_iG683DIViRQc-5IHY06LxG4kU.ddTM4QDL3ITN0czW}
```

## Section 5: Listing files 
```
hacker@commands~listing-files:/$ ls /challenge
20135-renamed-run-20752  DESCRIPTION.md
hacker@commands~listing-files:/$ /challenge/20135-renamed-run-20752
Yahaha, you found me! Here is your flag:
pwn.college{ARFCQiKDZvGOhMyQm7nJnX5mhdO.dhjM4QDL3ITN0czW}
```

## Section 6: Touching files
```
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{8iCWA69MSMIrfibVAtMBHX3KBm6.dBzM4QDL3ITN0czW}
```

## Section 7: Removing files
```
hacker@commands~removing-files:~$ ls
delete_me  f
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{IL-ui9zHMCGcaAPret9_UqHn_4z.dZTOwUDL3ITN0czW}
```

## Section 8: Hidden files
```
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.           .flag-21199982310851  challenge  home   lib64   mnt  proc  sbin  tmp
..          bin                   dev        lib    libx32  nix  root  srv   usr
.dockerenv  boot                  etc        lib32  media   opt  run   sys   var
hacker@commands~hidden-files:/$ cat .flag-21199982310851
pwn.college{8mMhxN6JJozTSYa8lZoeAHY5nW8.dBTN4QDL3ITN0czW}
```
## Section 9: An epic filesystem quest
```
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
BLUEPRINT  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin        challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ cat BLUEPRINT
Tubular find!
The next clue is in: /usr/share/racket/pkgs/racket-doc/scribblings/scheme/compiled

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/share/racket/pkgs/racket-doc/scribblings/scheme/compiled
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/racket-doc/scribblings/scheme/compiled$ ls
WHISPER  compat_scrbl.dep  compat_scrbl.zo  info_rkt.dep  info_rkt.zo  scheme_scrbl.dep  scheme_scrbl.zo
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/racket-doc/scribblings/scheme/compiled$ cat WHISPER
Lucky listing!
The next clue is in: /usr/share/X11/locale/el_GR.UTF-8
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/racket-doc/scribblings/scheme/compiled$ cd /usr/share/X11/locale/el_GR.UTF-8
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/locale/el_GR.UTF-8$ ls
Compose  POINTER  XI18N_OBJS  XLC_LOCALE
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/locale/el_GR.UTF-8$ cat POINTER
Congratulations, you found the clue!
The next clue is in: /opt/linux/linux-5.4/include/linux/phy

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/locale/el_GR.UTF-8$ ls /opt/linux/linux-5.4/include/linux/phy
TEASER-TRAPPED  omap_control_phy.h  omap_usb.h  phy-mipi-dphy.h  phy-sun4i-usb.h  phy.h  tegra  ulpi_phy.h
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/locale/el_GR.UTF-8$ cat TEASER-TRAPPED
cat: TEASER-TRAPPED: No such file or directory
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/locale/el_GR.UTF-8$ cat /opt/linux/linux-5.4/include/linux/phy/TEASER-TRAPPED
Congratulations, you found the clue!
The next clue is in: /usr/share/seabios/optionrom
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/locale/el_GR.UTF-8$ cd /usr/share/seabios/optionrom
hacker@commands~an-epic-filesystem-quest:/usr/share/seabios/optionrom$ ls
SNIPPET  extboot.bin  kvmvapic.bin  linuxboot.bin  multiboot.bin  vapic.bin
hacker@commands~an-epic-filesystem-quest:/usr/share/seabios/optionrom$ cat SNIPPET
Great sleuthing!
The next clue is in: /usr/lib/x86_64-linux-gnu/ruby/2.7.0/enc/trans

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/share/seabios/optionrom$ cd /usr/lib/x86_64-linux-gnu/ruby/2.7.0/enc/trans
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/ruby/2.7.0/enc/trans$ ls -a
.         big5.so     ebcdic.so              emoji_sjis_docomo.so    escape.so   iso2022.so       japanese_sjis.so  transdb.so
..        cesu_8.so   emoji.so               emoji_sjis_kddi.so      gb18030.so  japanese.so      korean.so         utf8_mac.so
.DOSSIER  chinese.so  emoji_iso2022_kddi.so  emoji_sjis_softbank.so  gbk.so      japanese_euc.so  single_byte.so    utf_16_32.so
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/ruby/2.7.0/enc/trans$ cat .DOSSIER
Lucky listing!
The next clue is in: /usr/lib/debug/.build-id/1d
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/ruby/2.7.0/enc/trans$ cd /usr/lib/debug/.build-id/1d
hacker@commands~an-epic-filesystem-quest:/usr/lib/debug/.build-id/1d$ ls
43538e9bec024560d22d0c5f65a7fa043c77f6.debug  4c2fb9e0ffcfcae03642c0d6964b3fe5045d0c.debug  EVIDENCE
43cc4e650e97607e7d8f00c0945b716a0fcc8e.debug  96833980a019bc1e045e78e5cdacc77e46ef80.debug  d30df7b02168ad5433d5586568317f7dc7b8ab.debug
hacker@commands~an-epic-filesystem-quest:/usr/lib/debug/.build-id/1d$ cat EVIDENCE
Tubular find!
The next clue is in: /usr/lib/python3/dist-packages/sympy/integrals/rubi/rubi_tests/tests/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/lib/debug/.build-id/1d$ cd  /usr/lib/python3/dist-packages/sympy/integrals/rubi/rubi_tests/tests/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sympy/integrals/rubi/rubi_tests/tests/__pycache__$ ls
BRIEF                            test_hyperbolic_sine.cpython-38.pyc          test_sine.cpython-38.pyc
__init__.cpython-38.pyc          test_inverse_hyperbolic_sine.cpython-38.pyc  test_special_functions.cpython-38.pyc
test_1_2.cpython-38.pyc          test_inverse_sine.cpython-38.pyc             test_tangent.cpython-38.pyc
test_1_3.cpython-38.pyc          test_logarithms.cpython-38.pyc               test_trinomials.cpython-38.pyc
test_1_4.cpython-38.pyc          test_miscellaneous_algebra.cpython-38.pyc
test_exponential.cpython-38.pyc  test_secant.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sympy/integrals/rubi/rubi_tests/tests/__pycache__$ cat BRIEF
Congratulations, you found the clue!
The next clue is in: /usr/lib/debug/.build-id/dd

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sympy/integrals/rubi/rubi_tests/tests/__pycache__$ cd /usr/lib/debug/.build-id/dd
hacker@commands~an-epic-filesystem-quest:/usr/lib/debug/.build-id/dd$ ls -a
.  ..  .CUE  429eff2603e552a4d1af5e99fc6292ab86c3f8.debug
hacker@commands~an-epic-filesystem-quest:/usr/lib/debug/.build-id/dd$ cat .CUE
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{M18YPLfm6I9ZC2rHZqjSwxsdU4N.dljM4QDL3ITN0czW}
hacker@commands~an-epic-filesystem-quest:/usr/lib/debug/.build-id/dd$
```
## Section 10: Making directories 
```
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ cd /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{sOgbr7OYC9l_PKOHIeEotMpCCqN.dFzM4QDL3ITN0czW}
```

## Section 11: Finding files
```
hacker@commands~finding-files:~$ cd /
hacker@commands~finding-files:/$ find -name flag -exec cat {} +
find: ‘./tmp/tmp.MiOQGWw5Zc’: Permission denied
find: ‘./etc/ssl/private’: Permission denied
find: ‘./var/cache/apt/archives/partial’: Permission denied
find: ‘./var/cache/ldconfig’: Permission denied
find: ‘./var/cache/private’: Permission denied
find: ‘./var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/mysql-files’: Permission denied
find: ‘./var/lib/private’: Permission denied
find: ‘./var/lib/mysql’: Permission denied
find: ‘./var/lib/mysql-keyring’: Permission denied
find: ‘./var/lib/php/sessions’: Permission denied
find: ‘./var/log/private’: Permission denied
find: ‘./var/log/apache2’: Permission denied
find: ‘./var/log/mysql’: Permission denied
find: ‘./run/mysqld’: Permission denied
find: ‘./run/sudo’: Permission denied
find: ‘./root’: Permission denied
find: ‘./proc/tty/driver’: Permission denied
find: ‘./proc/1/task/1/fd’: Permission denied
find: ‘./proc/1/task/1/fdinfo’: Permission denied
find: ‘./proc/1/task/1/ns’: Permission denied
find: ‘./proc/1/fd’: Permission denied
find: ‘./proc/1/map_files’: Permission denied
find: ‘./proc/1/fdinfo’: Permission denied
find: ‘./proc/1/ns’: Permission denied
find: ‘./proc/7/task/7/fd’: Permission denied
find: ‘./proc/7/task/7/fdinfo’: Permission denied
find: ‘./proc/7/task/7/ns’: Permission denied
find: ‘./proc/7/fd’: Permission denied
find: ‘./proc/7/map_files’: Permission denied
find: ‘./proc/7/fdinfo’: Permission denied
find: ‘./proc/7/ns’: Permission denied
cat: ./usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
cat: ./usr/local/share/radare2/5.9.5/flag: Is a directory
pwn.college{Mmk6Xo0J5aLjhE0BZaIYdxis67n.dJzM4QDL3ITN0czW}cat: ./opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag: Is a directory
cat: ./opt/radare2/libr/flag: Is a directory
cat: ./nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag: Is a directory
cat: ./nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag: Is a directory

```
## Section 12: Linking Files
```
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
ln: failed to create symbolic link '/home/hacker/not-the-flag': File exists
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{scyZ4RAbsarL6iz8mfeWEV4U4X5.dlTM1UDL3ITN0czW}
```
