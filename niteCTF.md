### Web Exploitation : Cybernotes 
The first step was to open the link to the cybernotes website. After doing that, I clicked into the login page.
<img width="1438" alt="Screenshot 2024-12-20 at 11 39 58 AM" src="https://github.com/user-attachments/assets/bbb40ae9-1be5-438c-9729-c2f7d231c3b8" />

<img width="1439" alt="Screenshot 2024-12-20 at 11 41 27 AM" src="https://github.com/user-attachments/assets/b4064704-9268-4875-b1a2-c5044c5b9baa" />

I knew that anything I entered into the UserID and Pwd field would not work, so I entered Forgot Password but only to get this :

<img width="1440" alt="Screenshot 2024-12-20 at 11 42 30 AM" src="https://github.com/user-attachments/assets/5b88c545-c25c-4916-8f60-2e6f7b906b43" />

I wasn't really sure how to continue, so I began by inspecting the elements which I thought would yield me the result but that didnt work. I hit a roadblock so I didn't continue.

<img width="1440" alt="Screenshot 2024-12-20 at 11 44 13 AM" src="https://github.com/user-attachments/assets/f0c8a8f8-f13a-41a1-b5a5-8a4035b88ad2" />

<img width="1440" alt="Screenshot 2024-12-20 at 11 45 01 AM" src="https://github.com/user-attachments/assets/73f76264-7d2e-4949-9034-2a50f6687724" />

****

### Cryptography: RSAabc

Two files were given, one a python file and another is a text file
<br/>
I opened the text file to find this, in the very first line
```
mrgπeτfΟΔςoΝeηiδyegsλexlwVαehιΠπμZe
```
I saw that the letters and symbols were the same as the keys & values in the dictonary in the python program
```
import sympy as sp
from Crypto.Util.number import *
file=open("flagg.txt","r+")
flag=file.read()
language = {
    'A': 'Α', 'a': 'α',
    'B': 'Β', 'b': 'β',
    'C': 'Σ', 'c': 'σ',
    'D': 'Δ', 'd': 'δ',
    'E': 'Ε', 'e': 'ε',
    'F': 'Φ', 'f': 'φ',
    'G': 'Γ', 'g': 'γ',
    'H': 'Η', 'h': 'η',
    'I': 'Ι', 'i': 'ι',
    'J': 'Ξ', 'j': 'ξ',
    'K': 'Κ', 'k': 'κ',
    'L': 'Λ', 'l': 'λ',
    'M': 'Μ', 'm': 'μ',
    'N': 'Ν', 'n': 'ν',
    'O': 'Ο', 'o': 'ο',
    'P': 'Π', 'p': 'π',
    'Q': 'Θ', 'q': 'θ',
    'R': 'Ρ', 'r': 'ρ',
    'S': 'Σ', 's': 'ς',  
    'T': 'Τ', 't': 'τ',
    'U': 'Υ', 'u': 'υ',
    'V': 'Ω', 'v': 'ω',
    'W': 'Ψ', 'w': 'ψ',
    'X': 'Χ', 'x': 'χ',
    'Y': 'Υ', 'y': 'υ',
    'Z': 'Ζ', 'z': 'ζ'
}
def googly(number, position):
    mask = 1 << position
    return number ^ mask



def string_to_int(message):
    return int.from_bytes(message.encode('utf-8'), byteorder='big')

def int_to_string(number):
    return number.to_bytes((number.bit_length() + 7) // 8, byteorder='big').decode('utf-8')

def rsa_encrypt(message, public_key):
    n, e = public_key
    message_as_int = string_to_int(message)
    ciphertext = pow(message_as_int, e, n)
    return ciphertext

def reverse_alphabet(char):
    if char.isupper():  
        return chr(155 - ord(char))  
    elif char.islower():  
        return chr(219 - ord(char)) 
    elif(char=='_' or '{' or '}'):
        return 'e' 
ct=[] 
nlist=[]
file1=open("out.txt","w",encoding="utf=8")
for ch in flag:
    if(not sp.isprime(ord(ch))):
        transformed_char = reverse_alphabet(ch)
        file1.write(transformed_char)
    pre=ord(ch)%26
    if(pre<5):
        pre+=5
    p=getPrime(pre)
    q = getPrime(1024)
    n = p * q
    phi_n = (p - 1) * (q - 1)
    e = 65537 
    d = sp.mod_inverse(e, phi_n)
    pubkey = (n, e)
    privkey = (n, d)
    message = ch
    ciphertext = rsa_encrypt(message, pubkey)
    if(sp.isprime(ord(ch))):
        if(ch.isupper()):
            eng=chr(65+ciphertext%26)
            lan=language.get(eng)
            file1.write(lan)
            ciphertext=googly(ciphertext,ciph.bit_length()-ord(eng))
        else:
            eng=chr(97+ciphertext%26)
            lan=language.get(eng)
            file1.write(lan)
            ciphetext=googly(ciphertext,ciph.bit_length()-ord(eng))
    ct.append(ciphertext)
    nlist.append(n)

file1.write("\nct: \n")
for i in ct:
    file1.write(str(i)+", ")
file1.write("\nn: \n")
for j in nlist:
    file1.write(str(j)+", ")

```
I first started by decoding the msg from the text file using the help of the dictorary but that didnt yield any proper result. So I didnt proceed.

****

### Binary Exploitation : Print the gifts

When I opened the folder given in the challenge, I saw a ELF file as the first file in the folder called "chall", so I decided to use Ghidra disassembler to try and get the binary file. Only to get this:
<img width="1436" alt="Screenshot 2024-12-20 at 12 05 15 PM" src="https://github.com/user-attachments/assets/063a8bdb-3608-43f8-a4b8-1db195d4756c" />

I tried reading through the file but I couldnt find any hints. So I didnt proceed

