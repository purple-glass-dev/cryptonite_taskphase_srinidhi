## Section 1: The Root 
The task is to invoke the code written within the file name `pwn` which we are accessing through <br/>`/pwn` <br/>which is the absolute path.
<br/>
Flag :
pwn.college{4NOnHUZUzfpuv61148qvw32P-tS.dhzN5QDL3ITN0czW}

## Section 2: Program and absolute paths
1. To access the flag, I have to execute the code within the `run` file which inturn is within the `challenge` directory.<br/>
`hacker@paths~program-and-absolute-paths:~$ /challenge/run`<br/>
Flag :
pwn.college{QKSGf6m9CDqFCQjDOMjjKrCCabS.dVDN1QDL3ITN0czW}

## Section 3: Position thy self 
1. `hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/doc/fontconfig directory.
Please use the `cd` utility to change directory appropriately.`
2. `hacker@paths~position-thy-self:~$ cd /usr/share/doc/fontconfig`
3. `hacker@paths~position-thy-self:/usr/share/doc/fontconfig$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{IWJRKavrMWkldX-UFe5EX6cZJAk.dZDN1QDL3ITN0czW}`


## Section 4: Position Elsewhere 
```
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/doc directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /usr/share/doc
hacker@paths~position-elsewhere:/usr/share/doc$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{UMTnGI1Oh1CIEPJ8_bxq4Z-Dslb.ddDN1QDL3ITN0czW}
```
## Section 5 : Position yet elsewhere
```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /etc directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /etc
hacker@paths~position-yet-elsewhere:/etc$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{4Yi2h04rYXt1_LeQNTW6y-a3i5W.dhDN1QDL3ITN0czW}
```
## Section 6: Implicit relative paths, from /
```
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{QK4612kV4bIg9iHnG_BZxBHM3iN.dlDN1QDL3ITN0czW}
```
## Section 7 : Explicit relative paths, from /
```
hacker@paths~explicit-relative-paths-from-:/$ cd /.
hacker@paths~explicit-relative-paths-from-:/$ /challenge/run
Incorrect...
You invoked this challenge with an absolute path. This challenge needs a relative path!
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{clm70Z3q6KxewKzwA8oL21zf-d8.dBTN1QDL3ITN0czW}
```
## Section 8: Implicit relative path
```
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ run
ssh-entrypoint: run: command not found
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{EccT5RFZlYIQJmCXm9vefvqxTYJ.dFTN1QDL3ITN0czW}
```
## Section 9: Home Sweet Home
```
Note that the expansion of ~ is an absolute path, and only the leading ~ is expanded. This means, for example, that ~/~ will be expanded to /home/hacker/~ rather than /home/hacker/home/hacker.
<br/>
NOTE: cd will use your home directory as the default destination:

hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ cd
hacker@dojo:~$

hacker@paths~home-sweet-home:~$ /challenge/run ./f
The argument you provided is not an absolute path!
hacker@paths~home-sweet-home:~$ /challenge/run /f
The argument you provided is not under your home directory!
hacker@paths~home-sweet-home:~$ /challenge/run ~/f
Writing the file to /home/hacker/f!
... and reading it back to you:
pwn.college{IWnLOT7Db7GXn-6-G5SWTqCP-6A.dNzM4QDL3ITN0czW} ```
```



