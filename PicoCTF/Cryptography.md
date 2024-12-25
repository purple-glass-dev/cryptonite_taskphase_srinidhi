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

****

## miniRSA

I used an online RSA decoder for getting the flag, and feeding the correct values, I got this:

<img width="1427" alt="Screenshot 2024-12-24 at 12 20 56 PM" src="https://github.com/user-attachments/assets/6ff44821-9c39-4c4e-9ac1-5fe62bdef4ee" />

The flag : picoCTF{n33d_a_lArg3r_e_d0cd6eae}

****

## Custom Encryption

```python
from sympy import mod_inverse

# Dynamic XOR decryption function
def dynamic_xor_decrypt(cipher_text, text_key):
    decrypted_text = ""
    key_length = len(text_key)
    for i, char in enumerate(cipher_text):
        key_char = text_key[i % key_length]
        decrypted_char = chr(ord(char) ^ ord(key_char))
        decrypted_text += decrypted_char
    return decrypted_text

# Reverse the modular exponentiation to obtain the original ciphertext
def reverse_generator(g, x, p):
    return pow(g, x, p)

# Decrypt function to reverse the encryption process
def decrypt(cipher, key):
    decrypted_text = ""
    for num in cipher:
        decrypted_num = num // (key*311)  # Reversing the encryption operation
        decrypted_text += chr(decrypted_num)
    return decrypted_text

# Constants from the provided information
a = 95
b = 21
enc_flag = [237915, 1850450, 1850450, 158610, 2458455, 2273410, 1744710, 1744710, 1797580, 1110270, 0, 2194105, 555135, 132175, 1797580, 0, 581570, 2273410, 26435, 1638970, 634440, 713745, 158610, 158610, 449395, 158610, 687310, 1348185, 845920, 1295315, 687310, 185045, 317220, 449395]

p = 97
g = 31

# Reverse modular exponentiation to obtain shared key
u = reverse_generator(g, a, p)
v = reverse_generator(g, b, p)
shared_key = reverse_generator(v, a, p)

# Decrypt intermediate ciphertext
intermediate_ciphertext = decrypt(enc_flag, shared_key)

# Reverse dynamic XOR encryption
flag = dynamic_xor_decrypt(intermediate_ciphertext, "trudeau")

correct_flag = flag[::-1]

print("Decoded Flag:", correct_flag)
```

The flag : picoCTF{custom_d2cr0pt6d_66778b34}


