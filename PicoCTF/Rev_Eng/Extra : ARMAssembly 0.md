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

The flag : `picoCTF{f51e846f}`
