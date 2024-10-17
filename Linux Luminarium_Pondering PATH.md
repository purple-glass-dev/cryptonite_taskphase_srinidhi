## Section 1: The PATH variable
```
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ ls
ssh-entrypoint: ls: No such file or directory
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{wG00m9FrMWF1DCrrJ96m30LYDj1.dZzNwUDL3ITN0czW}
```

## Section 2: Setting PATH
```
hacker@path~setting-path:~$ ls /challenge/more_commands/
win
hacker@path~setting-path:~$ PATH=/challenge/more_commands/
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{gTz6WUBCFOxN_2dFavSMt1aSWfS.dVzNyUDL3ITN0czW}
```

## Section 3: Adding commands
```

```

## Section 4: 
```
```
