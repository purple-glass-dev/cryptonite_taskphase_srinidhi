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
`hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/doc directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /usr/share/doc
hacker@paths~position-elsewhere:/usr/share/doc$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{UMTnGI1Oh1CIEPJ8_bxq4Z-Dslb.ddDN1QDL3ITN0czW}`

## Section 5 : Position yet elsewhere
`hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /etc directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /etc
hacker@paths~position-yet-elsewhere:/etc$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{4Yi2h04rYXt1_LeQNTW6y-a3i5W.dhDN1QDL3ITN0czW}`



