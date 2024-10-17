## Section 1: Listing processes
1. `ps` stands for Process Snapshot (OR) Process Status
```
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 18:02 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/defa
root           7       1  0 18:02 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 18:02 ?        00:00:00 /challenge/10924-run-11981
root          72      68  0 18:02 ?        00:00:00 sleep 6h
hacker        73       0  0 18:02 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        92      73  0 18:04 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/10924-run-11981
Yahaha, you found me! Here is your flag:
pwn.college{cjcNAmNCgXtU_PBQRkjUOFl-hUa.dhzM4QDL3ITN0czW}
Now I will sleep for a while (so that you could find me with 'ps').
```

## Section 2: Killing processes
```
hacker@processes~killing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 18:06 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/defa
root           7       1  0 18:06 ?        00:00:00 /run/dojo/bin/sleep 6h
root          71       1  0 18:06 ?        00:00:00 su -c /challenge/.launcher hacker
hacker        73      71  0 18:06 ?        00:00:00 /challenge/dont_run
hacker        74      73  0 18:06 ?        00:00:00 sleep 6h
hacker        75       0  0 18:06 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        92      75  0 18:06 pts/0    00:00:00 ps -ef
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{4t-OTFPeeKhF4hJBrRMNLARupWb.dJDN4QDL3ITN0czW}
```

## Section 3: Interuppting Processes
```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{slnaIY3slcYMMDFQcqhIU9Wxrab.dNDN4QDL3ITN0czW}
```

## Section 4: Suspending processes
```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 18:13 pts/0    00:00:00 bash /challenge/run
root          84      82  0 18:13 pts/0    00:00:00 ps -f

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
root          82      65  0 18:13 pts/0    00:00:00 bash /challenge/run
root          89      65  0 18:13 pts/0    00:00:00 bash /challenge/run
root          91      89  0 18:13 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{Y1gPVWediQFLs8yp1XNFQfwPoTo.dVDN4QDL3ITN0czW}
```

## Section 5: Resuming Processes
```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{48Bms7vjooD5f9hV4A8ABtaE_P0.dZDN4QDL3ITN0czW}
Don't forget to press Enter to quit me!

Goodbye!
```

## Section 6: Backgrounding Process
```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S+   bash /challenge/run
root          84 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 T    bash /challenge/run
root          89 S+   bash /challenge/run
root          91 R+   ps -o user=UID,pid,stat,cmd

I found a second version of me, but it's suspended! Please resume it in the
background with the 'bg' command, then run me again.
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S    bash /challenge/run
root         103 S    sleep 6h
root         104 S+   bash /challenge/run
root         106 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{Q7t_Qi91YV6sNB6aJkQOccnLgrz.ddDN4QDL3ITN0czW}
```
## Section 7: Foregrounding process
```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg /challenge/run
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.
hacker@processes~foregrounding-processes:~$ fg /challenge/run
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{olK7VISiUk0NToOJ729Hapjyiiu.dhDN4QDL3ITN0czW}
```

## Section 8: Starting Background processes
```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run
You've started me in the foreground! You must start me in the background (by
appending '&' to the command) to get the flag!
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 87


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{Aor75K4Sb_f1YEs5TT7HCV7Dd22.dlDN4QDL3ITN0czW}
[1]+  Done                    /challenge/run
```

## Section 9: Process Exit codes
```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
171
hacker@processes~process-exit-codes:~$ /challenge/submit-code
You must run /challenge/submit-code with the exit code you retrieved from
/challenge/get-code as the first argument:

Usage: /challenge/submit-code [EXIT_CODE]
hacker@processes~process-exit-codes:~$ echo $?
1
hacker@processes~process-exit-codes:~$ /challenge/submit-code 171
CORRECT! Here is your flag:
pwn.college{QUGNJxass_gIxfM-T2oVmf_v6y-.dljN4UDL3ITN0czW}
```
