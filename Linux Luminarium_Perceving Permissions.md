## Section 1: Changing file ownership
```
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ ls -l
total 32
-rw-r--r-- 1 hacker hacker   4 Oct  9 13:47 COLLEGE
-rw-r--r-- 1 hacker hacker   8 Oct  9 13:49 PWN
-rw-r--r-- 1 hacker hacker   0 Oct  9 16:01 challenge
-rw-r--r-- 1 root   hacker  58 Oct  3 12:30 f
-rw-r--r-- 1 hacker hacker   0 Oct  9 16:00 grep
-rw-r--r-- 1 hacker hacker 829 Oct  9 13:44 instructions
-rw-r--r-- 1 hacker hacker  93 Oct  9 13:44 myflag
lrwxrwxrwx 1 hacker hacker   5 Oct  9 17:15 not-the-flag -> /flag
-rw-r--r-- 1 root   hacker  77 Oct  9 16:53 out
-rw-r--r-- 1 root   hacker  77 Oct  9 16:53 output
-rw-r--r-- 1 hacker hacker 435 Oct  9 13:41 the-flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{0RKsGWXczSadJAJSH3liZ15XU2d.dFTM2QDL3ITN0czW}
```

## Section 2: Groups and files
```
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{IP6ilI8lyFdXmA0tE-pngIAhfRG.dFzNyUDL3ITN0czW}
```

## Section 3: Fun with group names
```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp15488) groups=1000(grp15488)
hacker@permissions~fun-with-groups-names:~$ chgrp grp15488 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{oKPMKhisOrTWh7O1m0QZCl3s4yc.dJzNyUDL3ITN0czW}
```

## Section 4: Changing Permissions 
```
hacker@permissions~changing-permissions:~$ ls -l /flag
-r-------- 1 root root 58 Oct 17 09:05 /flag
hacker@permissions~changing-permissions:~$ chmod a+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{w70vbgtIH2Py5Wki0hHilKPV8mr.dNzNyUDL3ITN0czW}
```

## Section 5: Executable files
```
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r--r--r-- 1 hacker hacker 32 Jul  4 06:37 /challenge/run
hacker@permissions~executable-files:~$ chmod a+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{4kwCJh--QtgfaCiEL8cft_u2yrr.dJTM2QDL3ITN0czW}
```

## Section 6: Permission Tweaking Practice
```

```

## Section 7: Permission setting Practice
```

```

## Section 8: The SUID bit
```
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{EdKTzHQ1o2wkxyGTtJENLSv7TJ2.dNTM2QDL3ITN0czW}
```
