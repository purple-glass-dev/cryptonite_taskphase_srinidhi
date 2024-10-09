## Section 1: Matching with *
```
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{kJl0G9Oc8k8XbVmuUhdznOCiWet.dFjM4QDL3ITN0czW}
```
## Section 2: Matching with ?
```
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{QwyAmraIUFOGH0pwp8J4UjV_x1o.dJjM4QDL3ITN0czW}
```
## Section 3: Matching with []
```
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ ls
file_a  file_c  file_e  file_g  file_i  file_k  file_m  file_o  file_q  file_s  file_u  file_w  file_y
file_b  file_d  file_f  file_h  file_j  file_l  file_n  file_p  file_r  file_t  file_v  file_x  file_z
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!
pwn.college{QA-Rw21s_BEDAb3AX2tc77RQfpc.dNjM4QDL3ITN0czW}
```
## Section 4: Matching paths with []
```
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{cfksmTTO8957V5OKuHZiky5tg3R.dRjM4QDL3ITN0czW}
```
## Section 5: Mixing globs
```
hacker@globbing~mixing-globs:~$ cd /challenge/files/
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [ecp]*
You got it! Here is your flag!
pwn.college{styAssB7EzcOHlvGo-0j_ZAJ7DY.dVjM4QDL3ITN0czW}
```
## Section 6: Exclusionary globbing 
```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files/
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{0cbEsnrQt2VzEg-ibXxUA4r8L5E.dZjM4QDL3ITN0czW}
```
