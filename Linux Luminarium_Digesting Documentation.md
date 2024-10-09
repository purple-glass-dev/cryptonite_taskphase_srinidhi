## Section 1: Learning from documentation
```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{Mw-eA0JU66R0HC2LpARISIfra9p.dRjM5QDL3ITN0czW}
```

## Section 2: Learning complex usage
```
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{k2eNcZGhEcAPcjrDYu5OWKkaXMv.dVjM5QDL3ITN0czW}
```

## Section 3: Reading Manuals 
```
hacker@man~reading-manuals:~$ man challenge

CHALLENGE(1)                            Challenge Commands                           CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --kwhsre NUM
              print the flag if NUM is 270

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)
hacker@man~reading-manuals:~$ /challenge/challenge --kwhsre 270
Correct usage! Your flag: pwn.college{k2FwhsBSK7NMr_eBDX0a4CAyO4e.dRTM4QDL3ITN0czW}
```

## Section 4: Searching Manuals 
```
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --lxdtcs // You have to search the manual to get the correct argument
Initializing...
Correct usage! Your flag: pwn.college{85AEbo1iqqktluaGpv2B4HIkR0T.dVTM4QDL3ITN0czW}
```

## Section 5: Searching for manuals
```
hacker@man~searching-for-manuals:~$ man man
MAN(1)                                                       Manual pager utils                                                      MAN(1)

NAME
       man - an interface to the system reference manuals

SYNOPSIS
       man [man options] [[section] page ...] ...
       man -k [apropos options] regexp ...
       man -K [man options] [section] term ...
       man -f [whatis options] page ...
       man -l [man options] file ...
       man -w|-W [man options] page ...

DESCRIPTION
       man is the system's manual pager.  Each page argument given to man is normally the name of a program, utility or function.  The man‐
       ual page associated with each of these arguments is then found and displayed.  A section, if provided, will direct man to look  only
       in  that section of the manual.  The default action is to search in all of the available sections following a pre-defined order (see
       DEFAULTS), and to show only the first page found, even if page exists in several sections.

       The table below shows the section numbers of the manual followed by the types of pages they contain.

       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions, e.g. /etc/passwd
       6   Games
       7   Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]

       A manual page consists of several sections.

       Conventional section names include NAME, SYNOPSIS, CONFIGURATION, DESCRIPTION, OPTIONS, EXIT STATUS, RETURN VALUE, ERRORS,  ENVIRON‐
       MENT, FILES, VERSIONS, CONFORMING TO, NOTES, BUGS, EXAMPLE, AUTHORS, and SEE ALSO.

       The following conventions apply to the SYNOPSIS section and can be used as a guide in other sections.

       bold text          type exactly as shown.
       italic text        replace with appropriate argument.
       [-abc]             any or all arguments within [ ] are optional.
       -a|-b              options delimited by | cannot be used together.
       argument ...       argument is repeatable.
hacker@man~searching-for-manuals:~$
hacker@man~searching-for-manuals:~$ man -k challenge
lbotngfdcz (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man lbotngfdcz

CHALLENGE(1)                                                 Challenge Commands                                                CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --lbotng NUM
              print the flag if NUM is 533

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                       May 2024                                                     CHALLENGE(1)
hacker@man~searching-for-manuals:~$ /challenge/challenge --lbotng 533
Correct usage! Your flag: pwn.college{YlboSPE53EM316tSA2BGnYYK3gf.dZTM4QDL3ITN0czW}
```

## Section 6: Helpful programs
```
acker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 749
hacker@man~helpful-programs:~$ /challenge/challenge --give-the-flag 749
Correct usage! Your flag: pwn.college{AxZMgCQzrgu7ADvLe4USucS9SDN.ddjM4QDL3ITN0czW}

```
## Section 7: Help for Builtins
```
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune		display a fortune
      --version		display the version
      --secret VALUE	prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "o6tQqL0s".
hacker@man~help-for-builtins:~$ challenge --secret o6tQqL0s
Correct! Here is your flag!
pwn.college{o6tQqL0s5Nnh86SRdryFjvtodqZ.dRTM5QDL3ITN0czW}

```
