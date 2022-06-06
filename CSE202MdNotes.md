# CSE 202 Notes 5/24/2022 Introduction

**Outline** 
* What is cse 202
* Cse202 topics 
* Student learning outcomes
* Course syllabus
* Abstraction of Computer Systems 
* Amdahl's Law

**CSE 202**

* Compouter organizatoin and architercture
* Programmer's perseepctive - How programs are compiled and executed. 


**Student Learning outcomes**
1. Manipulate machine represntation of the different data types
2. Analyze and write assembly code
3. Apply code optimization techniques to improve prgram performance
4. Describe how programs are compiled, linked, loaded in memory, and run on the cpu. 
5. Imporve the performance of programs using the property of locality
6. Manipulate simple process creation and signals
7. Apply the mechanizsms of virtual memory and paging 

**Imporving Peformance**
* Modern CPU's - multiple cores that can exsecute instructions in parallel
* One core - multiple functional units (execute operations in parallel)

**Amdahl's Law** 
"The performance improvement to be gained from using some faster mode of execution is lmited by the fraction of the time the faster mode can be used. 

<a href="https://ibb.co/z7QD909"><img src="https://i.ibb.co/s6bzxMx/0bee3f0621a34ac514cdafc613717338.png" alt="0bee3f0621a34ac514cdafc613717338" border="0"></a>

# 5/25/2022

**Amdahl's Law**
Total Trip is 2500 25 hours for the trio at 100 km/hr on average.
   1. Montana has just sbolished its speed limit (1500 km of the trip) the truck can travvel at 150 km/hr in Montana

Speedup = 1/((1-.6)+.6/1.5)

Alpha: fraction 1500/2500

k: speedup factor of fraction aplha (15/10 = 1.5)


**Can use vscode remote development to connect to sunlab machines** 
Youtube video will be posted

## Data Represnetation 

**Outline**

* Bits and bytes
* Bit-level manipulations 
* Integer represntations 
* Floating-point representation
* Integer Arithmetic
* Floating-point operations
  

**Student Learing outcomes**

* Manipualte numbers in binary and hexadecimal systems
* Recognize how bytes are stored in memory using little or big endia
* Use but-level operations
* Use the different representations of integers/reals and the casting from one reprsentation to the other
* Use the arithemtic operationjs on integers/reals and indectify overflow situations 

### Bits and bytes

* How are numbers represented in the machine 
* Positive integers - unsigned encoding
* Positive/Negative integers - signed encoding (2's compliment)
* Real numbers - Floating-Point ecoding (scientific notation)
* Text - ASCII/Unicode encoding


* Decimal (base 10) - 10 digits {0,1,2,3,4,5,6,7,8,9}
* Binary (base 2) - 2 digits {0,1}
* Hexadecimal (Base 16) - digits {0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F}

The computer only uses binary but hexadecimal is used to allow for easier use of binary

* Decimal
  * (175)-10 = 1*10^2+7*10+5*10^0
* Binary
  * (11001010)-2+1*2^7+1*2^6 + 1*2^3 + 1*2^1
* Hexadecimal
  * (2A5CF)-16 = 2*16^4 +10*16^3 + 12 *16^1 + 15*16^0

<a href="https://ibb.co/BPJ7WLs"><img src="https://i.ibb.co/DbF6c4K/2ef3dc62c36cabeda2d10c965599732d.png" alt="2ef3dc62c36cabeda2d10c965599732d" border="0"></a>

* Decimal to Binary
  * Successive divisions b2 and collect the remainders (0 or 1) or find a sum of powers of 2
* Decimal to Hexadecimal
  * Successive divisions by 16 and collect the remainders (0 to F) or find a sum of powers of 16
* Binary to Hexadecimal 
  * Group bits by 4 (one hex digit) starting formt the lowest bit
* Hexadecmimal to Binary
  * Exand each hex digit into 4 bits.

<a href="https://ibb.co/2qWL0k4"><img src="https://i.ibb.co/hsLnxmz/b2d11008d0e04aaaa3be70e2a0b1f94a.png" alt="b2d11008d0e04aaaa3be70e2a0b1f94a" border="0"></a>

<a href="https://ibb.co/Wx8t7Gh"><img src="https://i.ibb.co/C1C24mc/f04cc3a33269345d06ffdf23f8fe333e.png" alt="f04cc3a33269345d06ffdf23f8fe333e" border="0"></a>

**Bits and range of numbers**
* 8 bits - 0x00 to 0xFF (0 to 255)- (2^8-1)
* 16 bits - (0-65,535) (2^16-1)
* 32 bits - (0-4,294,901,760)
* 64 bits - (0-18,446,744,073,709,551,615)

<a href="https://ibb.co/WP8VyqJ"><img src="https://i.ibb.co/z796Rjv/d6d119d5a633a5640bd331f6b2e31527.png" alt="d6d119d5a633a5640bd331f6b2e31527" border="0"></a>


**How is data stored in memory**
* Array of bytes
* Each byte has an address (the index in the array)
* Range of the index = size of the memory space
  
<a href="https://ibb.co/tsf60z7"><img src="https://i.ibb.co/G2wDZ9K/9371e008a303e1dfa79857bc55153d54.png" alt="9371e008a303e1dfa79857bc55153d54" border="0"></a>


<a href="https://ibb.co/4fYtwJx"><img src="https://i.ibb.co/X43LfVT/0e204a90a372d798381587da4de9aefb.png" alt="0e204a90a372d798381587da4de9aefb" border="0"></a>


 Word(short) - (2 bytes) `BF 7A`
 Double word(int) -(4 bytes) `1F 30 BF 7A`
 Quadword(long)-(8 bytes) `FF 10 25 00 1F 30 BF 7A`

## Little Endian
<a href="https://ibb.co/xgYxvB4"><img src="https://i.ibb.co/94hQX1M/4a8e88d7d65646fc15954a5395c384b2.png" alt="4a8e88d7d65646fc15954a5395c384b2" border="0"></a>

## Big Endian
<a href="https://ibb.co/MnRyWss"><img src="https://i.ibb.co/cJNKM11/e697ba6c7a4ab54db72b53b310e099a5.png" alt="e697ba6c7a4ab54db72b53b310e099a5" border="0"></a>


* Little endian - lowest byte at lowest address - Intel Processor family - ARM processors
* Big endian - Highest byte at lowest address - IBM and Oracle (Sun) machines
* Invisible to the programmer - might be an issue when transferring data bewween different machines - use network standard instead-

**How to check status of machine**

```C
#include <stdio.h>
typedef unsigned char* byte_pointer;
void show_bytes(byte_pointer start, size_t len){
    for(int i=0; i<len; i++)
        printf("%x", start[i]);
        printf("\n");
}
int main(){
 int little = 0x11223344;
 show_bytes((byte_pointer)&little, sizeof(int));
}
```
World return 44332211 to indicate Little Endian Machine

## Bitwise Operations
* Boolean Algebra - Operations on a set of two values {0,1} representing false and true
* Boolean algebra is used in the design of digital systems (computers)
* Bitwise operations - (NOT,AND,OR,XOR) - C bit level operations - `~, &, |, ^`

<a href="https://ibb.co/JpvZLVL"><img src="https://i.ibb.co/C9bLdgd/1f62456d4b978ff465435021a9104f37.png" alt="1f62456d4b978ff465435021a9104f37" border="0"></a>

Bitwise operations can be used on specific binary patterns on each bit. 
<a href="https://ibb.co/xJPcz13"><img src="https://i.ibb.co/Lnbq9xv/7c4d5e0fce1cb11a4667d93b91f1b53d.png" alt="7c4d5e0fce1cb11a4667d93b91f1b53d" border="0"></a>

<a href="https://ibb.co/8BB8LmT"><img src="https://i.ibb.co/ZJJTpft/ca6c0793fe8e84a9d7938940a88434f8.png" alt="ca6c0793fe8e84a9d7938940a88434f8" border="0"></a>

<a href="https://ibb.co/NSmFfVT"><img src="https://i.ibb.co/pyR1N0h/82ff758135425e12d17f5981ad54a04f.png" alt="82ff758135425e12d17f5981ad54a04f" border="0"></a>

doubled boolean operators returns -true/false

binary is considered false when equal to zero

`~`is used as `!` when considering boolean

```C
#include <stdio.h>
int main(){
    char x = 0x66;
    char y = 0x39;
    printf("x&y = %x\n", x&y);
    printf("x|y = %x\n", x|y);
    printf("~x|~y = %x\n", ~x|~y);
    printf("x&&~y = %x\n", x&&~y);
    printf("x&&y = %x\n", x&&y);
    printf("x||y = %x\n", x||y);
    printf("!x||!y = %x\n", !x|!y);
    printf("x&!y = %x\n", x&!y);
}
```
```
x&y = 20
x|y = 7f
~x|~y = df
x&!y = 46
x&&y = 1
x||y = 1
!x||!y = 0
x&&~y = 0
```

### Shift operations

* x << k : shift x k positions to the left
* x >> k : shift x k positions to the right
<a href="https://ibb.co/v11qWGp"><img src="https://i.ibb.co/7vvCD5P/a71af90dfcec622354dab5c6b7f5839c.png" alt="a71af90dfcec622354dab5c6b7f5839c" border="0"></a>

**(x<<4)>>4 removes second digit, leaving first (Only for 1 byte[0000 0000])**

# 5/26/2022

When shifting to the **right** 
* logical for unsigned- insert 0 on the left
* Arithmetic for signed- insert the sign bit on the left

<a href="https://ibb.co/Qv0LzXh"><img src="https://i.ibb.co/qY6KXxh/Screen-Shot-2022-05-26-at-10-08-04-AM.png" alt="Screen-Shot-2022-05-26-at-10-08-04-AM" border="0"></a>

## Integer representation 
* Unsigned-nonnegative integers
* Signed- positive and negative integers

For every unsinged number there is only 1 way to represent a value in binary - bijection

**Sign magnitude**
* Sign magnitured - one bit for the sign and the remaining bits for the value 
* Sign bit = 0 positive number
* sign bit = 1 negative number

`1111 1111` -127
`0111 1111` 127

**2s compliment**

`1000 0000` -128
`0111 1111` 127

- zero has 1 representation 
- 2s compliment is used is most modern computers 
- 2s compliment is also a bijection

2s compliment examples 
* B2T4(0001)= 2^0 = 1
* B2T4(1011)= -2^3+2^1+2^0=-5
* B2T4(1111)= -2^3+2^2+2^1+2^0=-1

In my head I am thinking that 2s compliment just means that when the most significant digit is selected, the 1s just indicate the differece from the max negative value.

In hexadecimal the largest value is repreesented by `7F` `0111 1111`

## Floating point representation

* Used to encode real numbers in the form `x=m.2^e`
* Standard was exstablished in 1985 - IEEE Standard 754

**Real Numbers in binary**
`1101.11`=2^3 +2^2 + 1 + 2^-1 + 2^-2 = 13 + 1/2 + 1/4 = 13.75

Real numbers are represented using the scientific notation `x=(-1)^s.m.2^2`

- s:sign
- m: mantassa or significand 
- e: exponent

**Type float- Single precision representation (32 bits)**
- Sign: 1 bit
- exponent: 8 bits
- mantissa: 23 bits 
  

<a href="https://ibb.co/GH4L3Q8"><img src="https://i.ibb.co/mNVwF52/Screen-Shot-2022-05-26-at-10-43-32-AM.png" alt="Screen-Shot-2022-05-26-at-10-43-32-AM" border="0"></a>

**Type double- double precision representation (64 bits)**
- sign: 1 bit
- exponent: 11 bits
- mantissa: 52 bits 
  
<a href="https://ibb.co/xmzmcsH"><img src="https://i.ibb.co/PT1TbYQ/Screen-Shot-2022-05-26-at-10-45-28-AM.png" alt="Screen-Shot-2022-05-26-at-10-45-28-AM" border="0"></a>

<a href="https://ibb.co/f0MpXJg"><img src="https://i.ibb.co/ZTd8f9j/Screen-Shot-2022-05-26-at-10-48-29-AM.png" alt="Screen-Shot-2022-05-26-at-10-48-29-AM" border="0"></a>

**Converting to decimal**
1. convert from d=hex to binary
2. look at first digit
3. look at exponent (not 0 or 255) value of exponent, minus bias. 
4. Add 1 to mantissa 
5. X=(M*2^e)

**If not normalized**
* E = 0 Therefore dont add 1 to manitssa and convert from binary to decimal and multiply by 2^e

**If not normalized**
* e is max value therefore e=255 

<a href="https://ibb.co/vH2VMnv"><img src="https://i.ibb.co/Qfspxwj/Screen-Shot-2022-05-26-at-11-02-33-AM.png" alt="Screen-Shot-2022-05-26-at-11-02-33-AM" border="0"></a>

## Signed - Unsigned conversion 
* Bit pattern is the same (value of the bits)- interpretation is different
* T2U signed to unsigned
  * add most signifigant value instead of subtract
* U2T unsigned to signed 
  * Subtract most signifigant value instead of add

**Casting from unsigned to signed is changing the intrepretaion for the same binary pattern**


```C
#include <stdio.h>
int main(){
 int a = -1;
 unsigned b = 2147483648; //2 to 31st
 printf("a = %u = %d\n", a, a);
 printf(“b = %u = %d\n", b, b);
}
```
The cast can be completed in the print.

## Converting from unsigned to larger data type 
**for unsigned**
* Add leading zeros-Zero extension

**For signed**
* add sign bit - sign extension
  * Duplicate value of signed digit to all new values 

**When comparing signed and unsigned values, -1 as signed is equal to the largest value in the unsigned variable**

# 5/31 Chapter 2 Continuted 

`bash run_test.sh` is used to run test in PP0. 

On slide 71, demonstrating duplication of significant digit. 

All equal -5

`1011`- 
`11011`
`111011`

For conversion to smaller bits, First half of bits is lost. This can cause a change in data. With the newly most signinficant bit becoming the sign bit. 

<a href="https://ibb.co/9s2fTq3"><img src="https://i.ibb.co/862R5j4/image.png" alt="image" border="0"></a>

* Implicit casting (signed-unsigned) leads to non-intuitive behavior - prgoram bugs that are difficult to find
* C is the only language that supports the type unsigned

### Integer Arithmetic
* Arithmetic operations are performed on finite bit representation - problems may occur
* Adding two positive numbers result in a negative number
* Overflow: The integer result cannot fint within the word size limits of the data type. 

<a href="https://ibb.co/hfB2Nr8"><img src="https://i.ibb.co/jRy3Yq4/image.png" alt="image" border="0"></a>

Way of knowing if unsigned addition is okay

```C
int uadd_ok(unsigned short x, unsigned short y){
  unsigned short s = x+y;
  return s>=x;
}
```
Will return 1 if okay. 

<a href="https://ibb.co/RTpQx9B"><img src="https://i.ibb.co/F4b8SK0/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/5KCmR4b"><img src="https://i.ibb.co/cYR0r34/image.png" alt="image" border="0"></a>


**Within negation, smallest possible value in 2s compliment is impossible to be negated. This is because the positive value does not exist for that number.**

To negate bits:

1. ~x
2. +1

Example: 
1. `0101`:5
2. ~`0101`=`1010`=-8+2=-6
3. `1010`+1= `1011`=-8+2+1=-5


#### Integer Multiplication

Although the bits required to hold the product pay be larger than the initial values, the value will be stored in the mumber of bits in each value.

<a href="https://ibb.co/bPgBgMW"><img src="https://i.ibb.co/VtWSWcj/image.png" alt="image" border="0"></a>

**Multiplication by constants**
* Multiplication takes more time than any other logic/arithematic operation
* Compulers try to replace the multiplications by constant factors with combinations of + and shoft operations 
* Shifting a value one position to the left is equivalent to performing unsinged multiplication by 2. 

**Think multiplying by power of 10 in base 10 system you add 0s. In binary add zeros for subsiquient powers of 2**

Example: 
11*4 =`1011` * `0100` = `101100`

<a href="https://ibb.co/hK7N6Dw"><img src="https://i.ibb.co/p30T7J5/image.png" alt="image" border="0"></a>

**Divisions by powers of 2** 
* Division is even slower than the multiplication (30+ clock cycles)
* Shifting a value one position to the right is same as dividing by powers of 2 

<a href="https://ibb.co/Kxqz2WF"><img src="https://i.ibb.co/xqj816J/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/0m85486"><img src="https://i.ibb.co/TYpyjp7/image.png" alt="image" border="0"></a>

A bias is added to the values when performing division on negative values 

# 6/1/2022 

## Floating point multiplcation/addition

* Calculate exact result
* Make it fit in the desired percision
  * Overflow if exponent too large
  * Round to fit the significant bits
* Rounding 
  * Approximating a value to its closest bits 

<a href="https://ibb.co/PN8CpH0"><img src="https://i.ibb.co/zrwfcvD/image.png" alt="image" border="0"></a>

* Rounding
  * Even - avoid statistical bias
  * All other rounding will over- or under estimate consistently

* Rounding (binary)
  * To the nearest 1/4 (2 bits to the right of the binary point)
  * Even (least significant bit = 0)

<a href="https://ibb.co/SwW2htz"><img src="https://i.ibb.co/KxRYM2J/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/wQP2kpD"><img src="https://i.ibb.co/qgc2Smb/image.png" alt="image" border="0"></a>

* Addition multiplication 
  * Complex Operations - performed by specialized FP units 
  * Need rounding - overflow detection handling special cases

<a href="https://ibb.co/hFW0szS"><img src="https://i.ibb.co/QvN09w4/image.png" alt="image" border="0"></a>

## Chapter 3 Assembly Basics

**What is assembly language**

* Human version of the machine code
* Used for fine-grain optimization
* Used to identify program vulnerabilities
* Intel family (x86-64) machine language found in laptops, desktops, super computers, and large data centers.


```c
#include <stdio.h>
#include <stdlib.h>

extern int absdiff(int, int);

int main(int argc, char **argv) {
 int x = atoi(argv[1]);
 int y = atoi(argv[2]);
 printf("|%d - %d| = %d\n", x, y, absdiff(x, y));
 return 0;
}
```
```s
.global absdiff
absdiff:
 movl %edi, %eax  # %eax = x
 subl %esi, %eax  # %eax = x - y
 jge .L1
 negl %eax        # %eax = -%rax
.L1:
 ret              # %eax = |x-y|
```

### Instruction Set

* Architecture (ISA: Instruction Set Architecture)
  * The part of the cpu that executes the assembly code (instructions, registers)

* Example of ISAs
  * Intel: x86,IA32,x86-64
  * ARM: used in mobile phones 

<a href="https://ibb.co/5FLxysX"><img src="https://i.ibb.co/tXDPtYw/image.png" alt="image" border="0"></a>

* Assembly code
  * Registers - Data storage
  * Instructions - data manuipulation

**Registers**
* Eight (8) 64-bit registers - %rax to %rsp
* Eight (8) 64-bit registers -%r8 to %r15
  
<a href="https://ibb.co/6sZW5ZC"><img src="https://i.ibb.co/zf54w5v/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/DgsLHp2"><img src="https://i.ibb.co/n8ZRNCJ/image.png" alt="image" border="0"></a>

1. %rax
2. %rbx
3. %rcx
4. %rdx
5. %rsi
6. %rdi
7. %rbp
8. %rsp

<a href="https://ibb.co/BsxJvbs"><img src="https://i.ibb.co/88pwGq8/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/M51Qrzp"><img src="https://i.ibb.co/84xtqy2/image.png" alt="image" border="0"></a>

#### Operands
Instructions may manuipulate different types of operands

* Immediate valuese- constant integer data ($0x40)
* Register values - one of the 16 integer registers (%rax to %r15)
* Memory values - up to 8 consecutive bytes of memory at the address stored at a register. 

<a href="https://ibb.co/pjLf1WW"><img src="https://i.ibb.co/chr6ybb/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/qR3S1vj"><img src="https://i.ibb.co/RCkFHqb/image.png" alt="image" border="0"></a>

#### Data move operations
<a href="https://ibb.co/6s2DFgh"><img src="https://i.ibb.co/4Nc4pPy/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/TYzMkxh"><img src="https://i.ibb.co/XjmxbrJ/image.png" alt="image" border="0"></a>

# 6/2 Chapter 3 continued 

Watch beginning of recording for help with start of Programming Assignment

Uninon-structure pointing to same location in memory interpreting the same data differently.


```c
void swap(long *xp, long *yp){
  long t0 = *xp;
  long t1 = *yp;
  *xp=t1;
  *yp=t0;
}
```

```s
swap:
 movq (%rdi), %rax -- %rax=*xp
 movq (%rsi), %rdx -- %rdx=*yp
 movq %rdx, (%rdi) -- (%rdi)=*yp
 movq %rax, (%rsi) -- (%rsi)=*xp
 ret 
```

**Reverse engineer the assembly code into its equivalent C code**

```s
decode:
movq (%rdi),%r8   #r8=*xp
movq (%rsi),%rcx  #%rcx=*yp
movq (%rdx),%rax  #%rax = *zp
movq %r8,(%rsi)   #*yp = *xp
movq %rcx,(%rdx)  #*zp = *yp
movq %rax,(%rdi)  #*xp = *xp

```

<a href="https://ibb.co/m6n6D0z"><img src="https://i.ibb.co/ZWQWLST/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/6s7m2jf"><img src="https://i.ibb.co/dKwrS8z/image.png" alt="image" border="0"></a><br /><a target='_blank' href='https://imgbb.com/'>upload image</a><br />

<a href="https://ibb.co/4YmjcCv"><img src="https://i.ibb.co/CM1nq4C/image.png" alt="image" border="0"></a><br /><a target='_blank' href='https://imgbb.com/'>upload image</a><br />

```C
long scale(long x, long y, long z){
 long t = x + 4 * y + 12 * z
 return t;
}

```

```s
scale:
 leaq (%rdi,%rsi, 4), %rax -- %rax = 4*y+x
 leaq (%rdx,%rdx, 2), %rdx -- %rdx = 2*z+z=3z
 leaq (%rax,%rdx, 4), %rax -- %rax = 12z+4*y+x
 ret
```

<a href="https://ibb.co/cgxnpnN"><img src="https://i.ibb.co/2n54L4j/image.png" alt="image" border="0"></a><br /><a target='_blank' href='https://imgbb.com/'></a><br />

**Arithmetic and logical operations**

```C
long arith(long x, long y, long z){
 long t1 = x^y; long t2 = z*48;
 long t3 = t1&0x0F0F0F0F; long t4=t2-t3;
 return t4;
}
```

```s
arith:
 xorq %rsi,%rdi           --%rdi=x^y(t1)
 leaq (%rdx,%rdx, 2),%rax --%rax= z+2z= 3z
 salq $4,%rax             --%rax= 16*3z= 48z (t2)
 andl $252645135, %rdi    --%rdi = t1 & 0x0F0F0F0F(t3)
 subq %rdi, %rax          --%rax = t2 - t3 (t4)
  ret                       --%rax = t4 
```


**inclass practice**

```c
long arith2(long x, long y, long z){
 long t1 = - - -; long t2 = - - -;
 long t3 = - - -; long t4 = - - -;
 return t4;
}
```


```s
arith2:
 orq %rsi,%rdi    -- %rdi = x|y = t1
 sarq $3,%rdi     -- %rdi =(x|y>>3) = t2
 notq %rdi        -- %rdi = ~(x|y>>3) = t2
 movq %rdx, %rax  -- %rax = z = t3
 subq %rdi, %rax  -- %rax = z - ~(x|y>>3) =t4
ret 
```

<a href="https://ibb.co/FXfJGK8"><img src="https://i.ibb.co/1MpKHLR/image.png" alt="image" border="0"></a><br /><a target='_blank' href='https://imgbb.com/'>upload image</a><br />

**Practice from assembly to C**

```s
decode:
 subq %rdx,%rsi  #%rsi = y-z
 movq %rsi,%rax  #%rax = y-z
 imulq %rdi      #%rax = x*(y-z)
 salq $63, %rax  #%rax = (x*(y-z))<<63
 sarq $63, %rax  #%rax = ((x*(y-z))<<63)>>63
 xorq %rdi, %rax #%rax = x^((x*(y-z))<<63)>>63
ret 
```
is an arithmatic shift so if least signifigant is 1 all bits will be 1. 

Code will return x or compliment if x is odd or even 
```C
long decode(long x, long y, long z) {

}

```


# Assembly Control 6/6

**Assembly control: used for the conditional behavior of the code**

**Program Status**

* Every program running on the cpu has a status (context) described by:
  * %rip (instruction Pointer) - PC (Program Counter)- Address of the next instruction to be executed
  * (%rax,...%r15)- temporary data in the registers
  * %rsp(Stack Pointer)- Location of the stack top
  * Conditionals code - status of recent operations (zf,cf,sf,of) - Four 1-bit registers

<a href="https://ibb.co/FYNBMsr"><img src="https://i.ibb.co/qgXRf0S/image.png" alt="image" border="0"></a>

* Conditional codes are altered by 
  * All arithmetic/logical instructions
  * Comparison and Test instructions

<a href="https://ibb.co/gwHzcXs"><img src="https://i.ibb.co/0Z8hzWP/image.png" alt="image" border="0"></a>

* Instructions that access the condition codes
  * Set instructions - set by a single byte to 0 or 1 depending on some combinations of the condition codes
  * Consditional jump instructions - go some other part of the program depending of the vale in the condition codes
  * Conditional data transfer instructions - move data if certain conditionals are true. 
  

<a href="https://ibb.co/kGS4wD5"><img src="https://i.ibb.co/x271BgX/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/9ZqZkrc"><img src="https://i.ibb.co/XYzYrCj/image.png" alt="image" border="0"></a>


```c
# define COMP ?
typedef type_t ?
type_t comp(type_t a, type_t b){
  return a COMP b;
} 


```

```s
comp: 
cmpl %esi,%edi #a-b, int 
setl %al        # set %al to 1 if a-b<0  a<b

```
```s
comp:
 cmpq %rsi, %rdi # a - b 
 setne %al # SET  %al to 1 if a-b!=0 Comp:!=

```
<a href="https://ibb.co/jgrD90N"><img src="https://i.ibb.co/ZWMxR4j/image.png" alt="image" border="0"></a>

**Jump Instructions**

* all `jmp` instructions use a label - a direct value that indicated the target address
* Except `jmp *operand` - may use a register or a memory location that holds the target address

* The targer address (jmp instructions) may be 
  * Absolute an absolute address in memory
  * PC-relatove: relative to the value of %rip target address=PC + label value
  * PC = the address of the instruction after the jump instructions

<a href="https://ibb.co/wLR5hcp"><img src="https://i.ibb.co/FWKR4H8/image.png" alt="image" border="0"></a>



* jmp instructinos are used to implement program flow control constructs
  * if else
  * switch 
  * loops
  
**IF-Else**

In c

```
if(condidtion)
  then statments
else
  else statements 
```

in assembly
```
t= condition
if(!t)
  goto false
  then statements
  goto done
false: 
  else statments
done: 
```


<a href="https://ibb.co/h75jQ9D"><img src="https://i.ibb.co/GxwLYpc/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/swNFCGs"><img src="https://i.ibb.co/QNT6kRY/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/m5PKVV3"><img src="https://i.ibb.co/d4HvwwR/image.png" alt="image" border="0"></a>


<a href="https://ibb.co/pb6QkWj"><img src="https://i.ibb.co/bQjFGH5/image.png" alt="image" border="0"></a>

* Conditional Data Moves
  * Preferred when?
    * Avoid delay caused by branch perdiction
    * When computations are simple
  * Not preferred when?
    * Expensive computations
    * Risky computations
    * Computations with side effects



<a href="https://ibb.co/yV5rS8n"><img src="https://i.ibb.co/GFkqTVv/image.png" alt="image" border="0"></a>


* loops
  * Do-While loop
  * While loop
  * For loop

**do-while**

```
do{
  body_statements
}while(test_expr)
```

```
loop:
body statements
t=test_expr
if(t)
  goto Loop
```

<a href="https://ibb.co/yhm9Hb1"><img src="https://i.ibb.co/VH01fPZ/image.png" alt="image" border="0"></a>


<a href="https://ibb.co/G7yM7JX"><img src="https://i.ibb.co/H76P720/image.png" alt="image" border="0"></a>


**While Loop**

```
while(test_expr)
{
  body_statements
}
```

```
goto test
loop:
 body_statements
test:
  t= test_expr
  if(t)
  goto loop
```


<a href="https://ibb.co/ww7yS7c"><img src="https://i.ibb.co/2sSqvSZ/image.png" alt="image" border="0"></a>

**for loop**

<a href="https://ibb.co/k8bwKM6"><img src="https://i.ibb.co/fp6yMQG/image.png" alt="image" border="0"></a>


**Switch Statement**

