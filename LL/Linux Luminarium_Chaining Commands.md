## Section 1: Chaining with semicolons
```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{oqAjcFzvT73CZNkAI2YkVx5ZX37.dVTN4QDL3ITN0czW}
```

## Section 2: Your first shell script
```
hacker@chaining~your-first-shell-script:~$ touch x.sh
hacker@chaining~your-first-shell-script:~$ vi x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
You must first call the '/challenge/pwn' command, not '/challenge/run'!
hacker@chaining~your-first-shell-script:~$ vi x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{8rx7NP56JLKaqlJBdQFr72dx-ZA.dFzN4QDL3ITN0czW}
```

NOTE: A file was opened and the following was written in it 
` /challenge/pwn ; /challenge/college`

## Section 3: Redirecting script output
```
hacker@chaining~redirecting-script-output:~$ touch script.sh
hacker@chaining~redirecting-script-output:~$ vi script.sh
hacker@chaining~redirecting-script-output:~$ bash script.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{klwiiaXV-3TWV7RGlQ3W_fyHoA-.dhTM5QDL3ITN0czW}
```

NOTE: A file was opened and the following was written in it
`/challenge/pwn; /challenge/college`

## Section 4: Executable shell scripts
```
hacker@chaining~executable-shell-scripts:~$ touch script2.sh
hacker@chaining~executable-shell-scripts:~$ vi script2.sh
hacker@chaining~executable-shell-scripts:~$ chmod g+rwx script2.sh
hacker@chaining~executable-shell-scripts:~$ ./script2.sh
Congratulations on your shell script execution! Your flag:
pwn.college{EJpvLiKruJ9ZKZOMfzJ9jgBoVlG.dRzNyUDL3ITN0czW}
```
