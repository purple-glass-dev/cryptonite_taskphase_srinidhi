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
from random import randint
import sys



def generator(g, x, p):
    return pow(g, x) % p


def encrypt(plaintext, key):
    cipher = []
    for char in plaintext:
        cipher.append(((ord(char) * key*311)))
    return cipher


def is_prime(p):
    v = 0
    for i in range(2, p + 1):
        if p % i == 0:
            v = v + 1
    if v > 1:
        return False
    else:
        return True


def dynamic_xor_encrypt(plaintext, text_key):
    cipher_text = ""
    key_length = len(text_key)
    for i, char in enumerate(plaintext[::-1]):
        key_char = text_key[i % key_length]
        encrypted_char = chr(ord(char) ^ ord(key_char))
        cipher_text += encrypted_char
    return cipher_text


def test(plain_text, text_key):
    p = 97
    g = 31
    if not is_prime(p) and not is_prime(g):
        print("Enter prime numbers")
        return
    a = randint(p-10, p)
    b = randint(g-10, g)
    print(f"a = {a}")
    print(f"b = {b}")
    u = generator(g, a, p)
    v = generator(g, b, p)
    key = generator(v, a, p)
    b_key = generator(u, b, p)
    shared_key = None
    if key == b_key:
        shared_key = key
    else:
        print("Invalid key")
        return
    semi_cipher = dynamic_xor_encrypt(plain_text, text_key)
    cipher = encrypt(semi_cipher, shared_key)
    print(f'cipher is: {cipher}')

    def dynamic_xor_decrypt(ciphertext, text_key):
        plain_text = ""
    key_length = len(text_key)
    for i, char in enumerate(ciphertext):
        key_char = text_key[i % key_length]
        decrypted_char = chr(char ^ ord(key_char))  
        plain_text += decrypted_char
    return plain_text

def decrypt(cipher, text_key, shared_key):
    semi_cipher = [char // (shared_key * 311) for char in cipher]
    plain_text = dynamic_xor_decrypt(semi_cipher, text_key)
    return plain_text

def decrypt_ciphertext():
    cipher = input("Enter the ciphertext: ")
    cipher = [int(x.strip()) for x in cipher.split(",")]

    text_key = input("Enter the text key: ")
    shared_key = int(input("Enter the shared key: "))

    decrypted_text= decrypt(cipher, text_key, shared_key)
    reverse_decrypted_text = decrypted_text[::-1]
    print(f"Decrypted Text: {reverse_decrypted_text}")

if __name__ == "__main__":
    decrypt_ciphertext()



if __name__ == "__main__":
    message = sys.argv[1]
    test(message, "trudeau")

```

The flag : picoCTF{custom_d2cr0pt6d_751a22dc}

NOTE : It's showing incorrect flag for me.

