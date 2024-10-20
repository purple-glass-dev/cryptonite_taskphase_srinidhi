## Section 1: Becoming root with su
```
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{QlsKeahz17mASXZ4BDCsdjDVjaW.dVTN0UDL3ITN0czW}
```

## Section 2 : Other users with su
```
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{0WM1wCq8HrPokXaOTnACdqTncNw.dZTN0UDL3ITN0czW}
```

## Section 3: Cracking Passwords
```
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:18 100% 2/3 0.05470g/s 318.5p/s 318.5c/s 318.5C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{kyx8hBoq0qUTB7MLnrTILX48PZT.ddTN0UDL3ITN0czW}
```

## Section 4: Using sudo
```
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{ktab8Fo5Zadx30wqRqN_iNQr9mS.dhTN0UDL3ITN0czW}
```
