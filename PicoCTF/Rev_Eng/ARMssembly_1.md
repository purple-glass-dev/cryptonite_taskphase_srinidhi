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
	str	w0, [sp, 28] ; storing 23 in [sp,28]
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
>>> hex(4112417903)
'0xf51e846f'
Since the quetion requires me to remove the '0x', my flag will be of the format picoCTF{f51e846f}
```

The flag : picoCTF{f51e846f}

