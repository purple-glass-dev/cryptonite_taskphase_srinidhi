## Extra : ARMAssembly 0
The code given to us is in this challenge is a assembly file
```
  .arch armv8-a  ;This line tell us that this challenge is a64-bit ARMassembly file
	.file	"chall.c" ;This line indicates that the creator of the challenge wrote this in C language
	.text
	.align	2
	.global	func1
	.type	func1, %function
func1:
	sub	sp, sp, #16 
	str	w0, [sp, 12] ;storing w0 into the stack ;argv[1]
	str	w1, [sp, 8] ;storing w1 into the stack ;argv[2]
	ldr	w1, [sp, 12] ;w1=argv[1]
	ldr	w0, [sp, 8] ; w0=argv[2]
	cmp	w1, w0 ; comparing the two registers 
	bls	.L2 ; |bls| =Branch if LeSs than ; if argv[1]< argv[2] then we are going to branch the argument into label L2
	ldr	w0, [sp, 12] 
	b	.L3 ; return argv[1]
.L2:
	ldr	w0, [sp, 8] ; return argv[2]
.L3:
	add	sp, sp, 16 
	ret
	.size	func1, .-func1
	.section	.rodata
	.align	3
.LC0:
	.string	"Result: %ld\n"
	.text
	.align	2
	.global	main
	.type	main, %function

; |argv|=ARGument Vector points to a list of pointers. ; argv[0],argv[1],argv[2]
main:
	stp	x29, x30, [sp, -48]!  # |stp| = STore Pair. This stores the pair of registers(Memory in the CPU which is named), |sp| = Stack Pointer
	add	x29, sp, 0
	str	x19, [sp, 16]
	str	w0, [x29, 44]
	str	x1, [x29, 32]
	ldr	x0, [x29, 32] ;|ldr| = LoaD Register [x29,32] to 'x0' 
	add	x0, x0, 8 ;adding the number '8'[Specifcally no. 8 becase the width of 64 bit ] to 'x0'
	ldr	x0, [x0]
	bl	atoi #atoi-- converts string to integer
	mov	w19, w0
	ldr	x0, [x29, 32]
	add	x0, x0, 16
	ldr	x0, [x0]
	bl	atoi
	mov	w1, w0
	mov	w0, w19
	bl	func1
	mov	w1, w0
	adrp	x0, .LC0
	add	x0, x0, :lo12:.LC0
	bl	printf
	mov	w0, 0
	ldr	x19, [sp, 16]
	ldp	x29, x30, [sp], 48
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0"
	.section	.note.GNU-stack,"",@progbits 
```

From this we can conclude that func1 is just a max function which is comapring the two arguments(2 integers given in  the challenge)
<br/>
After this I compared the maximum number between the numbers given to me in the challenge ==>4112417903 and 1169092511
<br/>
and since 4112417903 is greater, I'll have to find the flag by finding the hex code. 
<br/>
<br/>
So in terminal I first imported `python3`, to get this
```
Python 3.12.6 (main, Sep  6 2024, 19:03:47) [Clang 15.0.0 (clang-1500.3.9.4)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
```
Showing that I already have it installed on my system. Next to retrieve my hexcode, I wanted to use the `hex()` function which is inbuilt
```
>>> hex(4112417903)
'0xf51e846f'
```
Since the quetion requires me to remove the '0x', my flag will be of the format `picoCTF{f51e846f}`
<br/>
The flag : `picoCTF{f51e846f}`
 ****

## ARMAssembly 1

Like ARMassembly0, this program is also written in assembly language
```
  .arch armv8-a
	.file	"chall_1.c"
	.text
	.align	2
	.global	func
	.type	func, %function
func:
	sub	sp, sp, #32 ; subracting 
	str	w0, [sp, 12] ; storing w0 in [sp,12]
	mov	w0, 68 ;moving the value 68 to w0
	str	w0, [sp, 16] ; storing w0=68 in [sp,16]
	mov	w0, 2 ; moving 2 to w0
	str	w0, [sp, 20] ; storing w0=2 in [sp,20]
	mov	w0, 3 ; moving 3 to w0
	str	w0, [sp, 24] ; storing w0=3 in [sp,24]
	ldr	w0, [sp, 20] ;w0=2
	ldr	w1, [sp, 16] ;w1=68
	lsl	w0, w1, w0 ; shifts the number 68(bin=1000100) by 2 bits(new number : 68*4 = 272), and the new value is stored in w0=272
	str	w0, [sp, 28] ;storing w0=272 in [sp,28]
	ldr	w1, [sp, 28] ;w1=272
	ldr	w0, [sp, 24] ;w0=3
	sdiv	w0, w1, w0 ; w0 = 272/3 = 90
	str	w0, [sp, 28] ; storing 90 in [sp,28]
	ldr	w1, [sp, 28] ; w1= 90
	ldr	w0, [sp, 12] ;w0=68
	sub	w0, w1, w0 ; w0=w1-w0 = 90-68 =22
	str	w0, [sp, 28] ; storing 22 in [sp,28]
	ldr	w0, [sp, 28] ; w0=22
	add	sp, sp, 32 
	ret 
	.size	func, .-func
	.section	.rodata
	.align	3
.LC0:
	.string	"You win!"
	.align	3
.LC1:
	.string	"You Lose :("
	.text
	.align	2
	.global	main
	.type	main, %function
main:
	stp	x29, x30, [sp, -48]!
	add	x29, sp, 0
	str	w0, [x29, 28] ; storing 22 in [x29,28]
	str	x1, [x29, 16] ; storing x1 in [x29,16]
	ldr	x0, [x29, 16] ; x0=x1
	add	x0, x0, 8 ; x0 = (x1*256) + (x1*256)
	ldr	x0, [x0] ; x0= (x1*256) + (x1*256)
	bl	atoi 
	str	w0, [x29, 44] ; storing 22 in [x29,44]
	ldr	w0, [x29, 44] ; w0=22
	bl	func 
	cmp	w0, 0 ; 22 and 0 not equal therefore, it keeps going to "You Lose" ; in order for w0=0(from the func; the argument must be 90)
	bne	.L4 ; |bne| = Branch if Not Equal ; Jumping to L4
	adrp	x0, .LC0
	add	x0, x0, :lo12:.LC0
	bl	puts
	b	.L6
.L4:
	adrp	x0, .LC1  
	add	x0, x0, :lo12:.LC1
	bl	puts
.L6:
	nop
	ldp	x29, x30, [sp], 48
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0"
	.section	.note.GNU-stack,"",@progbits

```
So in terminal I first imported python3, to get this

```
Python 3.12.6 (main, Sep  6 2024, 19:03:47) [Clang 15.0.0 (clang-1500.3.9.4)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
Showing that I already have it installed on my system. Next to retrieve my hexcode, I wanted to use the hex() function which is inbuilt
```
```
>>> hex(90)
'0x5a'
```
Since the quetion requires me to remove the '0x', my flag will be of the format picoCTF{5a}
To get a 32-bit flag, we will need 8-digits after '0x'
<br/>

The flag : picoCTF{0000005a} 

****

## GDB Baby step-1

The document given in the challenge was a ELF file which I had to somehow reverse engineer to find the value stored in the EAX register(return value of the main function). 
<br/> 
The process started with figuring out how to convert the ELF file into assembly language and I preferred to use Ghidra disassembler to that job.
<br/> 
The installation process on my mac was particulary hard, but after getting through the installation which involved >> Installing Ghidra from Github >> Installing the correct JDK. I was able to upload the file into the Ghidra disassembler.
<br/>
<br/>
Work done in terminal :

```
 ~ % cd Downloads
 Downloads % cd ghidra
 ghidra % ./ghidraRun
```
<img width="794" alt="Screenshot 2024-12-17 at 5 28 08 PM" src="https://github.com/user-attachments/assets/e933de09-99ec-419a-a8fb-7367b8cebc0b" />

I was given a detailed file, all converted in assembly language, and then did function>>main, to find my flag next to the EAX register.

<img width="1438" alt="Screenshot 2024-12-17 at 5 28 54 PM" src="https://github.com/user-attachments/assets/c7a3907f-84c2-4d2e-ae3b-fe8ef9813051" />

Therefore , 0x86342 is the number I was looking for. Converting from hexadecimal to decimal form --
```
 ghidra % python3
Python 3.13.1 (main, Dec  3 2024, 17:59:52) [Clang 16.0.0 (clang-1600.0.26.4)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> 0x86342
549698
```
The flag : picoCTF{549698}

****

## VaultDoor3

My first attempt was to understand what the program was trying to do:
<img width="1440" alt="Screenshot 2024-12-17 at 8 03 00 PM" src="https://github.com/user-attachments/assets/219fa7df-eba8-4bd0-be50-63fb9674207d" />

<img width="1044" alt="Screenshot 2024-12-17 at 8 03 33 PM" src="https://github.com/user-attachments/assets/80a40503-2884-40fe-90c9-fa42ee45f697" />

So, I understood that the loops are changing the pwd. So I'll give the paramater of the program to the given 32 character string.

```
public class random{
    public static void main(String args[]) {

    String password = "jU5t_a_sna_3lpm18gb41_u_4_mfr340";
    char[] buffer = new char[32]; // creating a character array of size 32
        int i; // Defining an integer i 
        for (i=0; i<8; i++) { 
            buffer[i] = password.charAt(i);
        }
        for (; i<16; i++) { 
            buffer[i] = password.charAt(23-i);
        }
        for (; i<32; i+=2) { 
            buffer[i] = password.charAt(46-i);
        }
        for (i=31; i>=17; i-=2) { 
            buffer[i] = password.charAt(i);
        }
        String s = new String(buffer); 
        System.out.println(s);

    }
}
```
Output:
```
srinidhia@srinidhis-mbp Downloads % cd "/Users/srinidhia/Downloads/" && javac random.java && java random
jU5t_a_s1mpl3_an4gr4m_4_u_1fb380
```

`jU5t_a_s1mpl3_an4gr4m_4_u_1fb380` is the modified password. 

<br/>
<br/>
Trying this password in the ocrrect flag format, I got granted access.

```
Enter vault password: picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_1fb380}
Access granted.
```

The flag : picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_1fb380}

****


 

