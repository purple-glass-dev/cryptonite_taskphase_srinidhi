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
hacker@permissions~permission-tweaking-practice:~$ /challenge/run
Round 0 (of 8)!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-------
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod go-rwx /challenge/pwn
You set the correct permissions!
Round 1 (of 8)!

Current permissions of "/challenge/pwn": rw-------
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-rwx---
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+rwx /challenge/pwn
You set the correct permissions!
Round 2 (of 8)!

Current permissions of "/challenge/pwn": rw-rwx---
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxrwx---
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+x /challenge/pwn
You set the correct permissions!
Round 3 (of 8)!

Current permissions of "/challenge/pwn": rwxrwx---
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxrwxr-x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o+rx /challenge/pwn
You set the correct permissions!
Round 4 (of 8)!

Current permissions of "/challenge/pwn": rwxrwxr-x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r--rwxr-x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u-wx /challenge/pwn
You set the correct permissions!
Round 5 (of 8)!

Current permissions of "/challenge/pwn": r--rwxr-x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": ----w----
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod a-rx /challenge/pwn
You set the correct permissions!
Round 6 (of 8)!

Current permissions of "/challenge/pwn": ----w----
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": --x-wx---
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod ug+x /challenge/pwn
You set the correct permissions!
Round 7 (of 8)!

Current permissions of "/challenge/pwn": --x-wx---
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": --xrwxr-x
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod go+rx /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{A8tlzPXTpCkb2VEOKecI4_ghUbi.dBTM2QDL3ITN0czW}
hacker@permissions~permission-tweaking-practice:~$
```

## Section 7: Permission setting Practice
```
hacker@permissions~permissions-setting-practice:~$ /challenge/run
Round 0 (of 8)!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-x--x-w-
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rx,g=x,o=w /challenge/pwn
You set the correct permissions!
Round 1 (of 8)!

Current permissions of "/challenge/pwn": r-x--x-w-
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w-r-----
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=r,o-rwx /challenge/pwn
You set the correct permissions!
Round 2 (of 8)!

Current permissions of "/challenge/pwn": -w-r-----
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-xrwxr--
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rx,g=rwx,o=r /challenge/pwn
You set the correct permissions!
Round 3 (of 8)!

Current permissions of "/challenge/pwn": r-xrwxr--
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -wxrw-rwx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=wx,g=rw,o=rwx /challenge/pwn
You set the correct permissions!
Round 4 (of 8)!

Current permissions of "/challenge/pwn": -wxrw-rwx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": ----wx-wx
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u-rwx,g=wx,o=wx /challenge/pwn
You set the correct permissions!
Round 5 (of 8)!

Current permissions of "/challenge/pwn": ----wx-wx
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rwx-w-r--
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rwx,g=w,o=r /challenge/pwn
You set the correct permissions!
Round 6 (of 8)!

Current permissions of "/challenge/pwn": rwx-w-r--
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r--rwx--x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=r,g=rwx,o=x /challenge/pwn
You set the correct permissions!
Round 7 (of 8)!

Current permissions of "/challenge/pwn": r--rwx--x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": --x-w-r-x
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=x,g=w,o=rx /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u+r /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{MGyP34V1hilbPuOayNV7kNYqD23.dNTM5QDL3ITN0czW}

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
