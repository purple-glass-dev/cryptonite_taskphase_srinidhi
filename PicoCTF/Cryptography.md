## C3

The contents of the ciphertext : 
`DLSeGAGDgBNJDQJDCFSFnRBIDjgHoDFCFtHDgJpiHtGDmMAQFnRBJKkBAsTMrsPSDDnEFCFtIbEDtDCIbFCFtHTJDKerFldbFObFCFtLBFkBAAAPFnRBJGEker
FlcPgKkImHnIlATJDKbTbFOkdNnsgbnJRMFnRBNAFkBAAAbrcbTKAkOgFpOgFpOpkBAAAAAAAiClFGIPFnRBaKliCgClFGtIBAAAAAAAOgGEkImHnIl`

The code for the encoder :

```python
import sys
chars = ""
from fileinput import input
for line in input():
  chars += line

lookup1 = "\n \"#()*+/1:=[]abcdefghijklmnopqrstuvwxyz"
lookup2 = "ABCDEFGHIJKLMNOPQRSTabcdefghijklmnopqrst"

out = ""

prev = 0
for char in chars:
  cur = lookup1.index(char)
  out += lookup2[(cur - prev) % 40]
  prev = cur

sys.stdout.write(out)
```

After some modification :
```python
import sys
user_input = "DLSeGAGDgBNJDQJDCFSFnRBIDjgHoDFCFtHDgJpiHtGDmMAQFnRBJKkBAsTMrsPSDDnEFCFtIbEDtDCIbFCFtHTJDKerFldbFObFCFtLBFkBAAAPFnRBJGEkerFlcPgKkImHnIlATJDKbTbFOkdNnsgbnJRMFnRBNAFkBAAAbrcbTKAkOgFpOgFpOpkBAAAAAAAiClFGIPFnRBaKliCgClFGtIBAAAAAAAOgGEkImHnIl"


lookup1 = "\n \"#()*+/1:=[]abcdefghijklmnopqrstuvwxyz"
lookup2 = "ABCDEFGHIJKLMNOPQRSTabcdefghijklmnopqrst"

out = ""
prev = 0
for char in user_input:
  cur = lookup2.index(char)
  for i in range(10000):
    if (i-prev) % 40 == cur:
      out += lookup1[i]
      prev = cur
      break
  
print(out)
```

Output:
```
#ap"q**1pnai[fl[)+jjy:e1=sbt x/++(*:pv(jv*)1v([chy:e:f
r ydr1v]th*wx1++(+pl+""):pm++(*mo[]uh"wa(mfvm++(:[*vr 

bgy:e:b:uah"w]x w
y
z
 zrfo[]r

mf(]w*rk+a"mpdy:ea])vr 

hef#
p:q(
r
1
r
11lr 





oqtw=ajgy:ehq fqootw=)+1 as:uyzz
```
Now writing a program to convert this ciphered text into the flag:
```python
chars = ""
from fileinput import input
for line in input():
    chars += line
b = 1 / 1

for i in range(len(chars)):
    if i == b * b * b:
        print (chars[i])
        b += 1 / 1
```

The flag : picoCTF{adlibs}
