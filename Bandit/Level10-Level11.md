## Level 10 -- Level 11
```
bandit10@bandit:~$ ls
data.txt
bandit10@bandit:~$ base64 data.txt
VkdobElIQmhjM04zYjNKa0lHbHpJR1IwVWpFM00yWmFTMkl3VWxKelJFWlRSM05uTWxKWGJuQk9W
bW96Y1ZKeUNnPT0K
bandit10@bandit:~$ base --help
Command 'base' not found, did you mean:
  command 'bake' from snap bake (0.1.3)
  command 'basex' from deb basex (10.5-1)
  command 'ase' from deb ase (3.22.1-3)
  command 'bash' from deb bash (5.2.21-2ubuntu1)
  command 'basez' from deb basez (1.6.2-3)
See 'snap info <snapname>' for additional versions.
bandit10@bandit:~$ base64 --help
Usage: base64 [OPTION]... [FILE]
Base64 encode or decode FILE, or standard input, to standard output.

With no FILE, or when FILE is -, read standard input.

Mandatory arguments to long options are mandatory for short options too.
  -d, --decode          decode data
  -i, --ignore-garbage  when decoding, ignore non-alphabet characters
  -w, --wrap=COLS       wrap encoded lines after COLS character (default 76).
                          Use 0 to disable line wrapping
      --help        display this help and exit
      --version     output version information and exit

The data are encoded as described for the base64 alphabet in RFC 4648.
When decoding, the input may contain newlines in addition to the bytes of
the formal base64 alphabet.  Use --ignore-garbage to attempt to recover
from any other non-alphabet bytes in the encoded stream.

GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
Full documentation <https://www.gnu.org/software/coreutils/base64>
or available locally via: info '(coreutils) base64 invocation'
bandit10@bandit:~$ base64 -d data.txt
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```
