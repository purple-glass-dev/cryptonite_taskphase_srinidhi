## Extra : Rotation
This was a simple exercise, I figured that the encryption method is just a bunch of shifting and for this challenge, I used the same online decoder as I used for the miniRSA project(later).

<img width="1432" alt="Screenshot 2024-12-25 at 6 22 40 PM" src="https://github.com/user-attachments/assets/cd8bc7d9-40a8-4f95-9758-98affab407a8" />

Since there are multiple shifts possible, a lot of possibilities were listed but I found the flag in the second line.

<br/>

The flag: picoCTF{r0tat1on_d3crypt3d_555957f3}

NOTE : The rotation pattern was [A-Z]+8.

<img width="365" alt="Screenshot 2025-01-12 at 10 56 37 AM" src="https://github.com/user-attachments/assets/7da76e15-cd39-4521-b83d-8811938c730e" />

****


## Extra : ReadMyCert

CSR -- Certificate Signing Request

I began by knowing the contents of the file by catting the readmycert.csr file. And I got the following.
```
srinidhia@srinidhis-mbp Downloads % cat readmycert.csr
-----BEGIN CERTIFICATE REQUEST-----
MIICpzCCAY8CAQAwPDEmMCQGA1UEAwwdcGljb0NURntyZWFkX215Y2VydF81YWVi
MGQ0Zn0xEjAQBgNVBCkMCWN0ZlBsYXllcjCCASIwDQYJKoZIhvcNAQEBBQADggEP
ADCCAQoCggEBAMCkf11rmV8rgqPvC2ZiPA6W+5RfOTwU6u3WpGvLA+2YFzocBPut
aATTxTPB+uaN2ZN3Z5J2CTFGmPzI4sUQfSqhZGuAqbfMyDDR8pRswmIYVJ6s0Apc
Toi7H8m3IShSbeE0pZUSIJpbK1a7V6lJqgwFMDI1qrgNhGgZaMA/l+d2J0vC3EYd
AijwSs8APcp6woWbFGYwdw5KaBsjn23oVz2G4h3/TmdB5g5e6Oq+kgi38NEpRDS0
ylXo9mUko3FqS4I6y9gOtDEI4uZaCJZuXHDmBpqZ04MfXbIVlHjF9NMOjDvXLonN
650oaANBm4bhBlgid0Fx48Z36tbtAVivZEcCAwEAAaAmMCQGCSqGSIb3DQEJDjEX
MBUwEwYDVR0lBAwwCgYIKwYBBQUHAwIwDQYJKoZIhvcNAQELBQADggEBAHZx6h9r
G/SE7RCoX6ndk5BOJprRiHpxOqPLAWcDyKHfStln0/HcQZzIrRVRsmoHiOmch+md
PBA1b+M5aj+3BWtPR9jOY4vht+ZmHAKa0WfQxwb2dBxsRPKTTDea0wN2u8BHLlSM
PbWPNuz+TKySL41xfwFuM4VN/ywn58GTvdb7HXgwNZCGgo2N1WhRq/dBMiagXMah
yb6gX4erugCu61T5tyD80hgsNBjaqyIdy/whRfC/Pmn3QHmdkqB5ZCPezwb2OLm4
5RDGv3WOB5q0BofoUGhVq757QE8qhL3oTvV2WlLoi3YWaZkJMCeR3vnH92cKC1Ov
FxdQuLOH8GMvl7U=
-----END CERTIFICATE REQUEST-----
```
On research, I found out a way to extract a flag from the file by using the following command.
<br/>
<br/>
The command used to get the flag : `openssl req -text -in readmycert.csr `

<br/> 
The above command will output the input file 'readmycert.csr' file in a human readable form.

```
srinidhia@srinidhis-mbp Downloads % openssl req -text -in readmycert.csr
Certificate Request:
    Data:
        Version: 1 (0x0)
        Subject: CN=picoCTF{read_mycert_5aeb0d4f}, name=ctfPlayer
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                Public-Key: (2048 bit)
                Modulus:
                    00:c0:a4:7f:5d:6b:99:5f:2b:82:a3:ef:0b:66:62:
                    3c:0e:96:fb:94:5f:39:3c:14:ea:ed:d6:a4:6b:cb:
                    03:ed:98:17:3a:1c:04:fb:ad:68:04:d3:c5:33:c1:
                    fa:e6:8d:d9:93:77:67:92:76:09:31:46:98:fc:c8:
                    e2:c5:10:7d:2a:a1:64:6b:80:a9:b7:cc:c8:30:d1:
                    f2:94:6c:c2:62:18:54:9e:ac:d0:0a:5c:4e:88:bb:
                    1f:c9:b7:21:28:52:6d:e1:34:a5:95:12:20:9a:5b:
                    2b:56:bb:57:a9:49:aa:0c:05:30:32:35:aa:b8:0d:
                    84:68:19:68:c0:3f:97:e7:76:27:4b:c2:dc:46:1d:
                    02:28:f0:4a:cf:00:3d:ca:7a:c2:85:9b:14:66:30:
                    77:0e:4a:68:1b:23:9f:6d:e8:57:3d:86:e2:1d:ff:
                    4e:67:41:e6:0e:5e:e8:ea:be:92:08:b7:f0:d1:29:
                    44:34:b4:ca:55:e8:f6:65:24:a3:71:6a:4b:82:3a:
                    cb:d8:0e:b4:31:08:e2:e6:5a:08:96:6e:5c:70:e6:
                    06:9a:99:d3:83:1f:5d:b2:15:94:78:c5:f4:d3:0e:
                    8c:3b:d7:2e:89:cd:eb:9d:28:68:03:41:9b:86:e1:
                    06:58:22:77:41:71:e3:c6:77:ea:d6:ed:01:58:af:
                    64:47
                Exponent: 65537 (0x10001)
        Attributes:
            Requested Extensions:
                X509v3 Extended Key Usage:
                    TLS Web Client Authentication
    Signature Algorithm: sha256WithRSAEncryption
    Signature Value:
        76:71:ea:1f:6b:1b:f4:84:ed:10:a8:5f:a9:dd:93:90:4e:26:
        9a:d1:88:7a:71:3a:a3:cb:01:67:03:c8:a1:df:4a:d9:67:d3:
        f1:dc:41:9c:c8:ad:15:51:b2:6a:07:88:e9:9c:87:e9:9d:3c:
        10:35:6f:e3:39:6a:3f:b7:05:6b:4f:47:d8:ce:63:8b:e1:b7:
        e6:66:1c:02:9a:d1:67:d0:c7:06:f6:74:1c:6c:44:f2:93:4c:
        37:9a:d3:03:76:bb:c0:47:2e:54:8c:3d:b5:8f:36:ec:fe:4c:
        ac:92:2f:8d:71:7f:01:6e:33:85:4d:ff:2c:27:e7:c1:93:bd:
        d6:fb:1d:78:30:35:90:86:82:8d:8d:d5:68:51:ab:f7:41:32:
        26:a0:5c:c6:a1:c9:be:a0:5f:87:ab:ba:00:ae:eb:54:f9:b7:
        20:fc:d2:18:2c:34:18:da:ab:22:1d:cb:fc:21:45:f0:bf:3e:
        69:f7:40:79:9d:92:a0:79:64:23:de:cf:06:f6:38:b9:b8:e5:
        10:c6:bf:75:8e:07:9a:b4:06:87:e8:50:68:55:ab:be:7b:40:
        4f:2a:84:bd:e8:4e:f5:76:5a:52:e8:8b:76:16:69:99:09:30:
        27:91:de:f9:c7:f7:67:0a:0b:53:af:17:17:50:b8:b3:87:f0:
        63:2f:97:b5
-----BEGIN CERTIFICATE REQUEST-----
MIICpzCCAY8CAQAwPDEmMCQGA1UEAwwdcGljb0NURntyZWFkX215Y2VydF81YWVi
MGQ0Zn0xEjAQBgNVBCkMCWN0ZlBsYXllcjCCASIwDQYJKoZIhvcNAQEBBQADggEP
ADCCAQoCggEBAMCkf11rmV8rgqPvC2ZiPA6W+5RfOTwU6u3WpGvLA+2YFzocBPut
aATTxTPB+uaN2ZN3Z5J2CTFGmPzI4sUQfSqhZGuAqbfMyDDR8pRswmIYVJ6s0Apc
Toi7H8m3IShSbeE0pZUSIJpbK1a7V6lJqgwFMDI1qrgNhGgZaMA/l+d2J0vC3EYd
AijwSs8APcp6woWbFGYwdw5KaBsjn23oVz2G4h3/TmdB5g5e6Oq+kgi38NEpRDS0
ylXo9mUko3FqS4I6y9gOtDEI4uZaCJZuXHDmBpqZ04MfXbIVlHjF9NMOjDvXLonN
650oaANBm4bhBlgid0Fx48Z36tbtAVivZEcCAwEAAaAmMCQGCSqGSIb3DQEJDjEX
MBUwEwYDVR0lBAwwCgYIKwYBBQUHAwIwDQYJKoZIhvcNAQELBQADggEBAHZx6h9r
G/SE7RCoX6ndk5BOJprRiHpxOqPLAWcDyKHfStln0/HcQZzIrRVRsmoHiOmch+md
PBA1b+M5aj+3BWtPR9jOY4vht+ZmHAKa0WfQxwb2dBxsRPKTTDea0wN2u8BHLlSM
PbWPNuz+TKySL41xfwFuM4VN/ywn58GTvdb7HXgwNZCGgo2N1WhRq/dBMiagXMah
yb6gX4erugCu61T5tyD80hgsNBjaqyIdy/whRfC/Pmn3QHmdkqB5ZCPezwb2OLm4
5RDGv3WOB5q0BofoUGhVq757QE8qhL3oTvV2WlLoi3YWaZkJMCeR3vnH92cKC1Ov
FxdQuLOH8GMvl7U=
-----END CERTIFICATE REQUEST-----
```

The flag : picoCTF{read_mycert_5aeb0d4f}

****
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
b = 1

for i in range(len(chars)):
    if i == b * b * b:
        print (chars[i])
        b += 1 
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


