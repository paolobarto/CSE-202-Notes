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

# 6/7 Switch statements continued

<a href="https://ibb.co/74vG245"><img src="https://i.ibb.co/VmVv2mZ/Screen-Shot-2022-06-07-at-10-04-53-AM.png" alt="Screen-Shot-2022-06-07-at-10-04-53-AM" border="0"></a>

<a href="https://ibb.co/5hfLg34"><img src="https://i.ibb.co/60fF7Sw/image.png" alt="image" border="0"></a>

## Procedures (Functions)

* Outline 
  * The Run-time stack
  * Control Transfer
  * Data Transfer
  * Local Storage in the Stack/Registers
  * Recursive Procedures


<a href="https://ibb.co/tDtXVCX"><img src="https://i.ibb.co/jD2Rn4R/image.png" alt="image" border="0"></a>

* When a function P calls function Q
  * Code switches from one code to another
  * Transfer of control
  * Transfer the data

**Calling Process**

* Procedure p calls procedure q(procedure,function,method,subroutine,handler,...)
* Steps to implement the call:
  * Passing data 
  * Passing control
  * Allocating and deallocating memory


* Passing Control
  * After the call: PC(%rip) = starting @ of q
  * After return: %rip = @ of the instructions after the call in p
  * Passing Data
    * P may pass one or more parameters to Q
    * Q may return one value to P
  * Allocating and deallocating memory - If q allocated memory for its local variables, Q must free space before it returns 

**Runtime Stack**
* The stack is used to implement the calls:
  * P calls Q - Control and data information of P are pushed in the stack - popped when q returns (pushq and popq)
  * %rsp points to the top of the stack - grows towards lower addresses
    * Decrement %rsp - allocate space
    * Inscrement %rsp - deallocate space

* If the number of arguments is less than 6, only registers are used - no space allocated on the stack
* Some procedure might not need a stack frame if their local variables can be held in registers and they do not call other procedures

**Control Transfer**

<a href="https://ibb.co/WytDZN8"><img src="https://i.ibb.co/bBJHTjw/image.png" alt="image" border="0"></a>

**Data Transfer**
* Arguments and return value - most of them are done through registers in x86-64 IA
  
<a href="https://ibb.co/Gkxf1BM"><img src="https://i.ibb.co/xGCKcPg/image.png" alt="image" border="0"></a>

* Function proc has four arguments u, a, v, and b. Given the body of the function and its assembly code, determine a valid ordering and types of the four parameters.

```c
*u += a
*v += b
return sizeof(a)+sizeof(b)

```

%edi(a:int) %sil(b:short), %rdx(u) %rcx(v)
```s
proc:
addq %edi, (%rdx)
addb %sil, (%rcx)
movl $6, %eax
ret

```

**Data Transfer**
* Local storage on the stack
  * Callee may need to put local varaiables in the stack
    * Not enough registers to hold the local variables
    * The local variables are refferred to using pointers (& local variable)
    * The local variables are arrays or structures


* Local storage in the registers
  * Registers %rbx, %rbp, and %r12-%r15 are callee-saved registers
  * P calls Q. Q must preserve the value of the callee saved registers
  * If Q does not ise the callee saved registers, nothing to do
  * If Q uses the callee saved registers, Q must save the registers on the stack, uses them, and restores the old value of the used registers from the stack before returning 

  **Recursive calls**
  * Recursive calls are supported by the stack disipline 

<a href="https://ibb.co/Mk9ndGr"><img src="https://i.ibb.co/GQF7mty/image.png" alt="image" border="0"></a>

# 6/8/2022 Assembly: Data

**Outline**
* Array allocation and access
* Heterogeneous data structures (struct and union)
* Data alignement
* Combining control and data in machine level programs

## Arrays
* `T A[N]` - Contiguous memory region
* Size of allocated region: `sizeof(T) * N bytes`
* `A` is the pointer to the first byte of the memory region
* `A[i]` is located at the address `A + sizeof(T) * i`

<a href="https://ibb.co/L0HmWb1"><img src="https://i.ibb.co/zmDpYjZ/image.png" alt="image" border="0"></a>


<a href="https://ibb.co/m5NXSPp"><img src="https://i.ibb.co/1Gzdb4c/image.png" alt="image" border="0"></a>


## 2D Arrays
* `T A[R] [C]` - Contiguous memory region
* Stored in row-major order
* Size of the allocated region: `sizeof(T) * R * C` bytes
* A is the pointer to the first byte of the memory region `(A[0][0])`
* `A[0][0]` is located at the address `A + sizeof(T)*(C * i +j)`
* c is number of columns in row 

<a href="https://ibb.co/DVJFN4w"><img src="https://i.ibb.co/w0kqTyp/image.png" alt="image" border="0"></a>

## Heterogeneous data structures

```c
struct record{
  int i;
  int j;
  int a[2];
  int *p;
};

```

<a href="https://ibb.co/CHdQ7YM"><img src="https://i.ibb.co/2k2dtCs/image.png" alt="image" border="0"></a>

```c
typedef union{
  struct {
    long u;    t1.u->0
    short v;   t1.v->8
    char w;    t1.w-> 10
  } t1; sizeof(t1) = 11 bytes
  struct {  
    int a[2];   t2.a[0]->0 t2.a[1]->4
    char *p;    p->8
  }t2;    sizeof(t2) = 16 bytes
} utype; size(utype) = 16 bytes

```

### Improving Data Alignement
* Improve the memory system performance by reducing memory access (transfer blocks of data)
* x86-64 CPUs require that the address data must be a multiple of some calue K (typically 2,4, or 8)
* Any primitive type of size K bytes must have an address that is a multiple of K

```
char - 1
short - 2
int, float - 4
double, long, char* - 8
```
<a href="https://ibb.co/0Y7jyL6"><img src="https://i.ibb.co/QYgFvVT/image.png" alt="image" border="0"></a>

**For structures, gaps may be inserted in the feild allocation to ensure that each strcutre member satisfies the alignment requirements**

* Pointers to structure S1 must satisfy a 4-byte alignment (`struct S1 *p`)
* The value of `p` must be a multiple of 4 (`p->i` or `p->j`)
* Compilers may also need to add padding at the end of the structure so that each element in an array of structures will satisfy its alignment requirements.
  

```c
struct rec{
  char *a;  //a-> 0
  short b;  //b->8 +6 gap
  double c; //c->16
  char d;   //d->24+3 gap
  float e;  //e->28
  char f;   //f->32 + 7 gap
  long g;   //g->40
  int h;    //g->48 rec ends at offset
}; 56, 52+4 padding
sizeof(rec) = 56 bytes
```

rearranged from smallest size to largest.
```c
struct rec{
  char d;   d->0
  char f;   f->1
  short b;  b->2
  float d;  d->4
  int h;    h->8
  char *a;  d->12 + 4 gap
  double c; c->24
  long g;   g->32
}; sizeof(rec)= 40 bytes
```


# 6/9 FLoating point in Assembly

## Pointers
* Every pointer has an associated type (int*, char*, void*)
* Every pointer has a value - address of a variable or null (0)
* Pointers are initalized with the & operator
* Pointers are derefernced with the * operator
* Arrays and pointers are closly related (a[3] is equavalient to *(a+3),a+3 is calculated as a + sizeof(T) * 3)
* Casting from one type of pointer to another - change the type, but not the value - the type is used for pointer arithmetic 

```
char *p; (int *) p+7 -> (p+7 * 4)
          (int*) (p + 7) —> (p + 7)
```
* Pointers to functions: storing and passing references to code
* The pointer stores the address of the first instruction in the machine representation of the function

```
int fun(int x, int *p);
int (*fp)(int, int*);
fp = fun;
int y=1;
int result = fp(3, &y);
```

<a href="https://ibb.co/LNvF8FL"><img src="https://i.ibb.co/rdvjmjC/image.png" alt="image" border="0"></a>

need to use -g to allow compiler to have access to variables
```
run -g 
```

**Data and Code issues**

* The stack stores data (local variables) and state information ( saved registers and return addresses)
* Corrupted stack can lead to serious program errors
* Buffer overflow is common source of stack corruption


* Solution 1: Stack Randomization 
  * Stack Addresses were predictable in old systems
  * Change the position of the stack from one run of a program to another


* Solution 2: Stack corruption detection
  * Store a special canary value (gaurd value) in the stack (between localnbuffer and the rest of the stack state)
  * Canary calues are generated randombly each time the program executes

* Solution 3: Limiting executable code regions
  * Indicate if a memory region is code or data
  * Only code regions that can be exectuted
  * Handled by hardware


## Floating-Point Code
* How floating-point values are stored and accessed
* How to process floating point data
* How floating point parameters and return values passed

<a href="https://ibb.co/B49R0Bj"><img src="https://i.ibb.co/Q84GyMn/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/kqNtX0h"><img src="https://i.ibb.co/F8RFzJB/image.png" alt="image" border="0"></a>


```c
float fadd(float x, float y){
  return x+y;
}
```

```s
# x in %xmm0, y in %xmm1
addss %xmm1, %xmm0
ret
```


```c
double dincer(double *p, double v){
  double x = *p;
  *p = x+v;
  return x;
}

```


```s
# p in %rdi, v in %xmm0
movapd %xmm0, %xmm1 # Copy v; mov aligned, packed double
movsd (%rdi), %xmm0 # x = *p; mov scalar double
addsd %xmm0, %xmm1 # tmp = x + v; add scalar double
movsd %xmm1, (%rdi) # *p = tmp
ret
```


```s

#double fun(int *ap, double b, long c, float *dp);
#%rdi(ap), %xmm0(b), %rsi(c), %rdx (dp)
fun:
 vmovss (%rdi), %xmm1             #
 vcvtsi2sd (%rdi), %xmm2, %xmm2
 jbe .L8
 vcvtsi2ssq %rsi, %xmm0, %xmm0
 vmulss %xmm1, %xmm0, %xmm1
 vcvtps2pd %xmm1, %xmm0
 ret
.L8:
 vaddss %xmm1, %xmm1, %xmm1
 vcvtsi2ssq %rsi, %xmm0, %xmm0
 vaddss %xmm1, %xmm0, %xmm0
 vcvtps2pd %xmm0, %xmm0
 ret

```

**Summary**

* Data storage
  * Arrays
  * Structs and unions
  * Data alignment
* Issues with combining data with control
* Basic floating-point code




# 6/9 Computer Architecture

**Outline**
* Processor Design process
* Instruction execution phases
* Pipelined Execution
* Pipeline limitations
* Solutions to pipline limitations

**Learning Outcomes**
* Describe the process of designing a process
* Describe the instruction execution cycle
* Understand pipelineing and its limitations
* Understand how the performance of a processor is determined


**Processor Design**
* ISA - Instruction set architecture - set of instructions that the processor is able to run
* Link Between: 
  * Compiler writers - write code that runs on ISA
  * Processor designers - design circuit that runs ISA


**Processor Design**
* Learn the inner working of a system you use daily
* Understand how the overall computer system works (later chapters)
* Career in embedded systems (contain processors)
* Work in processor design team (CAD tools)


<a href="https://ibb.co/F8JmT3S"><img src="https://i.ibb.co/5svGH4N/image.png" alt="image" border="0"></a>


**Combinational Logic**
* Operations performed by the processor
  * addition/subtraction
  * mul/div
  * bitwise operations
  * Comprison/Test Operations

**Sequential Logic**
* Storage of data/instructions
  * Registers
  * Memory
  * Condition codes


<a href="https://ibb.co/g6rwsPv"><img src="https://i.ibb.co/R7gPLBh/image.png" alt="image" border="0"></a>


**Instruction execution cycle**

<a href="https://ibb.co/g9TfPGW"><img src="https://i.ibb.co/548Sndj/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/B2P3np6"><img src="https://i.ibb.co/QvcQDgH/Screen-Shot-2022-06-09-at-11-33-45-AM.png" alt="Screen-Shot-2022-06-09-at-11-33-45-AM" border="0"></a>


# 6/10 Processor Architecture


<a href="https://ibb.co/Pc4pVSm"><img src="https://i.ibb.co/X7pBGw2/image.png" alt="image" border="0"></a>


By creating the same 5 phases in an instruction, each phase can be completed by using parallelism.

<a href="https://ibb.co/C03Yvvf"><img src="https://i.ibb.co/x5tBGGN/image.png" alt="image" border="0"></a>

**Instruction Execution Cycle**
* The Pipeline increases the number of instructions executred per unit of time
* The Pipeline does not chnage the time to execute one instruction
* Modern processors: 5 to 15 pipleline stages
* Works well when instructions are independent 

<a href="https://ibb.co/1QqMMCG"><img src="https://i.ibb.co/B3ZGGh2/image.png" alt="image" border="0"></a>


**Processor performance analysis**
* Pipeline - Ideally CPI =1, CPI - Cycles per instruction
* Stalling may increase CPI
  * Load/use adds 1 bubble in the pipeline
  * Branch Prediction adds 2 bubbles in the pipleine
  * ret adds 3 bubbles in the pipline 

<a href="https://ibb.co/5jGgMgv"><img src="https://i.ibb.co/M1Zx2xp/image.png" alt="image" border="0"></a>

* Load instructions - 25% of all the instructions - 20% of the load instructions cause load hazards
* Conditional branches 20% of all the instructions - 60% are taken and 40% not taken
  

<a href="https://ibb.co/Mh6H4f3"><img src="https://i.ibb.co/dcgvqtz/image.png" alt="image" border="0"></a>


* Other issues
  * Multi-cycle instructions - FP division.multiplications - up to 60 cycles - issue these instructions to specialized hardware
  * Memory access instructions - may take 3-20 cycles (cache or main memory) - up to 1,000,000 cycles if data is in the hard disk

# Program Optimization

**Program Performance**
* Asymptotic Complexity - Big-O Notation
* Performance of the program as a function of the input size - ignore constraints
* Constant matter when you want to improve the execution time of a program
* O(n)-O(n/2)-O(n/10)


**Optimize program performance at different levels**
* Alorgithm
* Data Structures
* Procedures or functions
* Loops

**Must understand how programs are executed on modern processors**
* Instruction execution cycle
* Memory Access
* Measuring program performance and bottlenecks
* Optimize performance without altering the code behavior and modularity

**Compilers try to optimize while benerating code machine**
```
gcc -00 no optimization
gcc -01 basic set of optimization
gcc -02 (or higher O3) - extensive optimization
```

**Optimizations performed by compilers**
* Register allocation
* Code selection and ordering 
* Dead code elimination
* Eliminate minor inefficiencies
* Compilers have difficulty overcoming "optimization blockers"
* Memory aliasing and procedure calls

**Compilers have limitations**
* Operate under constraint (cannot modify the prgram behavior and cannot make generalizations)
* Programmer knows the range of data, comilers don't
* Perform opimizations with individual functions or procedures
* Alalysus based on static information (cannot anticipate runtime data)
* When in doubt compilers are conservative. 


-------



**Optimizing Blockers**


**General Optimization Techniques**
* Code motion
* Reducing procedure calls
* Eliminating unneeded memory references


# 6/13 Program performance

* Optimizations performed by Compilers
  * Register allocation
  * Code selection and ordering (scheduling)
  * Dead code elimination
  * Eliminate minor inefficencies


* Memory Aliasing
  * When two pointers may designate the same memory location


* Function calls and side effects

```c
long f();
long func1(){
  return f() + f() + f() + f();
}
long func2(){
  return 4*f();
}
```

func1 and func2 seem to do the same thing


**General optimization techniques**
* Code motion
* Reducing procedure calls
* Eliminateing unneeded memory references. 


**Code motion**
* Identify computations that are performed multipe times (inner loops)
* Moving code without affecting the behavior of the program
* Done by compilers with caution to avoid side effects 

Ex. Moving legnth size function out of loop since will call each iteration


**Reducuing procedure calls**
* Procedures introduce overhead
* Procedures block optimizations

**Eliminating unnecessary memory references**
* Memory access operations are slower than other opertions
* Eliminate memory erferences when possible 

Similar to reducing funciton calls, can choose to referance locations in memory much less

* Compilers will not make such optimizations because of possible memory aliasing

combine3(v,get_vec_start(v)+2);

combine4(v, get_vec_start(v)+2);

## Understanding modern processors
* To optimize programs, we need to understand how the processor executes the instructions
* Exploit the independency between instructions to execute as many as possible in parallel
* The order of the execution may be changed as long as the overall sequential behavior is not altered

* Two lower bounds (HW) characterize the maximum performance of a program
* Latency bound - a series of operations must be performed in strict sequence (data dependency)
* Throughouput bound - Raw computing capacity of the processor’s functional units


* Modern processors are
  * Pipelined - one instruction/cycle - (CPI=1)
  * Superscaler - many instructions may be executed at the same time (CPI<1)
  * Out-of-order - the order of execution of the instructions may be changed to increase parallelism 

<a href="https://ibb.co/LkkQQrP"><img src="https://i.ibb.co/YRRDDXW/image.png" alt="image" border="0"></a>


* Functional Unit Performance
  * Latency - number of cycles to complete one operation
  * Issue time - minimum number of cycles between two independent operations of the same type
  * Capacity - number of functional units capable of executing the same operation (number of operations that can be issued at the same time)
  * Throughput - number of operations that can be executed per clock cycle - (Capacity/issue) operations per cycle


**Data flow graph**
* A program can be represented as a data flow graph
* A data flow graph show data dependencies between the operations
* Data flow graphs allow identitfying critical paths in the program

# 6/14

**Loop unrolling**
* Low level optimization that reduces the number of iterations for a loop by increasing the numbers of elements computed in each iteration
* Redusces the # of operations that do not contribute to the program result (loop indexing and conditional branching)
* Exposes or shows ways in which we can reduce the number of operations in the critical path
* Perfomred by gcc for optimization level  `-03` or higher

**Loop unrolling with multiple accumulators**

* multiple accumulators
  * Compilers don't risk transformations with FP operations to avoid errors (associativity)
* Reassociation transformation
  * Shifting the order in which the elements are processeed
  * Combine: change the order in which the vector elements are combined

**Limiting Factors**
* Processor Capacity
  * Program requires N iterations
  * Processor has C functional units for the operations
  * The processor unita have an issue time I
  * Program needs (N*I)/C cycles to execute

**Register Spilling**
* A program has a degree of parallelism P that exceeds the number of registers. The compiler will resort to spilling, storing some of the temporary values in memory, by allocating space on the runtime stack

**Branch mis-prediction penalties**
* Execute the instructions at the predicted branch without committing changes to registers or memory until the outcome of the branch condition is known
* Use conditional data moves to execute both branches and commit only at the right branch
* 19-cycle mis-prediction penalty
* Mis-predictions rate is low in modern processors 
* Loop conditions are always taken except for the last iteration
* Branch prediction is reliable for regular paths in the code
* If a number < 0 - prediction will do poorly because it is difficult to predict the sign (dependent on the data)

**Write/read dependency**
* Load operations look in the store unit buffer for the @ to load. If the @ is found, it takes the value from the store unit without waiting for the data to be written to memory


1. High-level design
2. Basic Coding principles
3. Low-Level optimizations


**High-level design**
* Choose appropreaite and efficient algorithms and data structures
* Avoid asympomatic poor performance


**Basic coding principle**
* Avoid optimization blockers
  * Excessive function calls
  * Move computaitons out of loops when possible
  * Eliminate unnecessary memory references - introduce temporary result - store result in an array or global variable only when the final value has been computed
  
**low level optimization**
* Unroll loops to reduce overhgead and enablke further optimization
* Find ways to increas ILP using multiple accumulators and re-association with loop unrolling
* Rewrite conditional operations in functional style to enable using conditional data transfers 


## Program profiling

**OPtimizations should not alter the behavior of the program**\
**Extensive testing is required after applying optimizations**


* A profiler is a tool used to identifty performance bottlenecks in a program
* Eliminate performance bottlenecks
* Apply OPtimization techniques
* Usefule for large programs only


* `gprof` on Unix
* Determine hoe much CPU time was spend on each function in the program
  * Gice a sense of the funcitons contribution to the overall run time
  * Cound the number of tiumes each function is called
  * Understand the dynamic behavoir of the program


**Properties of `gprof`**
  * Timings are not percise
  * Calling information is reliable
  * Timing of the library functions is not shows 

<a href="https://ibb.co/0D60wBm"><img src="https://i.ibb.co/QbTW58p/image.png" alt="image" border="0"></a>

# 6/15 Memory Hierarchy

**Memory**
* RAM abstractiopnp: array of bytes
* Computer RAM is packaged as multiple chips
* RAM is volatile (data lost when power turned off)

**Types of Ram(Volatile)**
* Static RAM (SRAM) - fully sequential circuit (two gates with two loops) - keeps its state
* Dynnamic RAM (DRAM) - one transistor circuit - equivalent to a capacitance (leaks) - needs refreshing to keep its state


**Types of non-Volatile memory**
* ROM- read-only memory - data written once when manufactured
* PROM - Programmable ROM - can be programmed once
* EPROM- Erasable PROM - can be erased and reprogrammed - bulk erase
* EEPROM - Electronically EPROM - can be electronically erased and reporgrammed
* FLash Memory - EEPROM with partial erase capacity (block level) - < 100,000 erasing 


## Disk
* Disk - platters - two surfaces - tracks - sectors 
* Disk capacity - Maximum number of bits that can be stored 
* Capacity determined by:
  * Recording Density - bits/inch segement (track)
  * Track density - tracks/inch radial segment
  * Areal density - bits/in^2 -(reconding density * track density)

<a href="https://ibb.co/kDwYxFw"><img src="https://i.ibb.co/z2BKrwB/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/qRqfJcy"><img src="https://i.ibb.co/K94kKf0/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/Kcg3dZK"><img src="https://i.ibb.co/kVTWjnm/image.png" alt="image" border="0"></a>

**Disk Access Time**
* Disk Access Time = seek time + rotation time + transfer time
* Seek Time - time to position r/w heads over the track (targer sector - 3 to 9 ms)
* Rotational latency - time waiting for the target sector to pass under r/w head - time to rotatie half a full spin - typical RPM = 7200 RPMs
* Transfer Time - time to read the bits in the target sector

<a href="https://imgbb.com/"><img src="https://i.ibb.co/zS0s9jM/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/2Md4VXk"><img src="https://i.ibb.co/ZgxD4yM/image.png" alt="image" border="0"></a>

* Disk Access Time
  <a href="https://ibb.co/2FLZB0P"><img src="https://i.ibb.co/HKMhQLY/image.png" alt="image" border="0"></a>

* Access time domionatied by seek time and rotational latency
* Accessing the first but is the most time consuming,  the rest of the sector bits are transfered fast

**CPU - Disk interaction**
1. CPU sens a request to the disk controller 
2. Disk controller transfers the sector to the memory address (DMA) 
3. Disk Controller notifices the CPU when the data is ready


* How to reduce the gap by minimizing the access time to memory
  * Create layers of memory between the CPU and the Main memory
  * Memory with fast access is near the CPU and stores the most frequently accessed data
  * Explot a fundamental property of computer programs - locality

## Locality
* Programs tend to used data and instructions with addresses near of equal to those they have used recently
  * Temporal Locality: recently referenced data/instructions are likely to  be referenced again in the near future (loops)
  * Spatial locality: data/instructions with enarby addresses to be refernced close together in time

**Temporal Locality**
  * Reference variable sum at each iteration
  * cycle through loop instructions

**Spatial Locality**
  * Reference array elements sequentially
  * Refernce instructions in sequence

**Measurement**
* Locality is determined qualitatively
* Requires programming experience

## Memory Hierarchy 
* Fast Storage technologies are more expensive, have less capacity and consume more power
* The gap between CPU and MM speed slows the CPU
* Well-written programs exhibits good lovality
* Organize data storage as a memory hierarchy


## Cache Memory
* **Cache**: Smaller, faster memory that holds a subset of the data fromt he alrger, slower memory
* Programs tend to access data at level k more often than they access data at level k+1 locality
* Memory that costs as cheap storage at the top, but allow access rate at the fast storage near the bottom. 

<a href="https://ibb.co/MG3xn7d"><img src="https://i.ibb.co/pR9B2dq/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/5GwzfjX"><img src="https://i.ibb.co/xXdcRgK/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/K7nh872"><img src="https://i.ibb.co/pZqwkZf/image.png" alt="image" border="0"></a>

**Cache Organization**
**Cache size = (S x E x B) bytes**
* Direct mapping - E=1, S=number of lines
* 2-way Set Associative - E=2, S = number of lines/2
* K-way set associative - E=k, S=number of lines/k
* Fully associative - E = number of lines -s = 1


<a href="https://ibb.co/wBYc7Pj"><img src="https://i.ibb.co/pbnhQM5/image.png" alt="image" border="0"></a>



# 6/20 Cache memory

**Organization**
* direct Mapping - more conflict miss (all addresses with the same set nuymber are madded to the same line)
* 2-way associative - flkexability to map addresses to two different lines in a set
* E-way set associative - Flexability to map addresses to E different lines (compare tage to K tags at the same time)
* Fully Assocaiative - Any address may be mapped to any line - more hardware to compare all athe tags in parallel

**Types of Cache misses**
* Cold (compulsory) miss - when the cache is empty
* Conflict miss - when two blocks are assigned to the same chache line
* Capacity miss - when the size of the referenced blocks is greater than the chache size

**Write Issues**
* Write operation - same as read operation but 
  * Should data be updated in the cache only or in the cache and the MM 
  * Write operations with HIT
    * Write through - wroite immeddiately to the cache and the main memory
    * Write-back - defer write to memory until the cache line is replaced (one dirty bit to indicate if a chache line is differenet from MM or not)
  * Write operations with Miss
    * Write-allocate - load into cache and upate line in chache- good if more writes to the location in the future
    * No-write-allocate - write directly to memory - no load into cache
  * Line Replacement
    * When multiple lines may be selected to replace and load a new line, which line is select3ed
    * FIFO - First line loaded is selected to be replaced
    * LRU - Least Recently Used line is selected
    * Random - line selected randomly


**Miss Rate**
* Miss Rate 
  * Fraction of memory references not found in the cache
* Hit Rate
  * Fraction of memory references that hit (1-miss rate)
* Hit Time
  * Time to deliver data from a cache line to the processor (included chacking if the line is in the cache)(L1:4 Cycles, L2 10 cycles)
* Miss Penalty 
  * Additional Time requied because of a miss

<a href="https://ibb.co/KD0cZ04"><img src="https://i.ibb.co/nBgq2gd/image.png" alt="image" border="0"></a>


* Cache size
  * Increase the hit rate but will increase the hit time
* Block size
  * Can help increaese the hit rate, but imply a smaller number of cache lines and an increase in the miss penaly
* Associativity
  * Higher associativity reduced conflict misses, but requires more complex hardware to compare the tags and select the lines for replacement (miss penalty)

<a href="https://ibb.co/M9YhjP5"><img src="https://i.ibb.co/6N3ZpDJ/image.png" alt="image" border="0"></a>


* Repeated referecnes to local variable are good - will be cached in registers
* Stride-1 reference patterns are good because chaches store data as contiguous blocks (spatial locality) 

<a href="https://ibb.co/KypgSvh"><img src="https://i.ibb.co/mzVKgWT/image.png" alt="image" border="0"></a>


# 6/21 Exception control flow

**Outline**

* Execptions
* Processes
* Process Control
* Signals 


**Control Flow**
* Sequence of instructions executed by the processor
* Control flow may be modified by:
  * `jump` instructions
  * `call` and `return` instructions


* Not enough to react to events that are external to the running program or the CPU
  * Arrivbal data from the disk or network adapter
  * Errors at exewcution time
  * User interrups program using `ctrl-c`
* Abrupt changes in the control flow: `Exception Control Flow (ECF)`


**Why ECF**

* Basic mechanisms that the OS uses to implement I/O, processes and virtual memory
* How programs interact with the OS (system calls)
* Create applications with ECF mechanismas (creating/waiting/deleting processes, detected and responsing to exveptional events) -shells and web servers
* Understand concurrency and how its implemented (processes and threads)
* How the try-throw-catch mechnaism is implemented 

<a href="https://ibb.co/n0sr79p"><img src="https://i.ibb.co/H2D7t6Z/image.png" alt="image" border="0"></a>

**Mechanisms**
*  Low-level mechanisms 
   *  Exceptions-change in control flow in response to a system event (change in system state) - Implemented by hardware and operating system
* High-level mechanisms
  * Processes Context Switch (Processes) - Implemented by OS and hardware timer
  * Signals - implemented by the OS

**Exceptions**
* Transfer of control to the OS kernal in response to some event
* Examples of events: division by 0, page fault, overflow, I/O operations completed, intrerrupting a program using `ctrl-c`
  
<a href="https://ibb.co/x5g4KnQ"><img src="https://i.ibb.co/s31BpTr/image.png" alt="image" border="0"></a>

**Exception Table**
* each type of event has a unique exception number k
* k is the index into the exception table
* Handler k is called each time exception k occurs
* Base address (@) of the exception table stored in a dedicated register

**Asychronous Exceptions**
* Caused by events external to the processor
* Inidicated by setting the processor's interrupt pin
* Handler returns to the next instruction
* Examples
  * Timer interrupt: used by the kernal to take back control from user programs
  * I/O interrupt from external device 

**Synchronous exceptions**
* Caused by events that occur as a result of executing an instruction (faulting instruction)
* Traps
  * Intententional
  * System calls/ breakpoint traps
* Faults 
  * Unintentional but possibly recoverable
  * Page faults, floating-point exceptions
  * either re-execute current instruction or aborts
* Aborts
  * Unintentional and recoverable
  * illegal instruction, parity errors, machine check
  * abort current program 

## Processes
* High level mechanisms for exception control flow
  * Processes context switch (processes)
  * Signals
  * Non-local jumps

* A process is an instance of a running program
* One of the most profound ideas in cs
* Not a program (executable code save on disk)
* Not the processor (machine that executes the program)
* When a program is loaded in memory, a process is created


 Each process has its own two key abstractions

* logical Control Flow
  * each process seems to use the CPU exclusively (implemented by the OS kernal using context switching)
* Private address Space
  * Each process seems to use the main memory exclusively

**Multiprocessing - the illusion**
  * Computern runs many processes simultaneously (web browers, email clients, editors, background tasks)

* **Multiprocess**- The traditional reality
  * Sigle processor executes multiple processes concurrently
  * Address space managed by virtural memory system
  * Register values for non-exectuing processes saved in memory


* **The modern reality** 
  * Multicore processors
  * Mutliple CPU's on single chip that share the main memory
  * Each core can execute a seperate process
  * Scheduling processes on cores done by the OS kernal

### Concurrent Processes
* Each processes has a logical control flow
  * Two processes run currently if their flows overlap in time, otherwise they are sequential 

<a href="https://ibb.co/936nTs1"><img src="https://i.ibb.co/Kzd6qFf/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/F8FbbtD"><img src="https://i.ibb.co/kqtggFS/image.png" alt="image" border="0"></a>

**Process**
* Process Control
  * How are processes created? Terminated? Stopped?
  * Process has a unique ID (pid)
  * Process has three different states

1. Running
   1. Executing or waiting to be executed
2. Stopped
   1. Execution suspended until futher notice
3. Terminated
   1. Execution stopped permanently
  
**Terminating a process**
* A process becomes terminated for
  * Recieving a singal whose default action is to terminate
  * Returning from the main funciton
  * Calling the system function `exit()`
  * `void exit(int status)` terminates with an exit status
  * Normal status is 0, non-zero status for error
  * Return 0; in main means return with normal status
  * Exit is called once but never returns
  

**Creating a process**
* Parent process creates a new running child process by calling the function fork()
  * fork() return 0 to the child process
  * fork() return the child's process id (pid) to the parent process
  * fork() returns a negative value for error. 


# 6/22 Processes Continued


Error handling in functions is produced by creating a wrapper function for the given function. Calling a Unix error function displaying the current Error.

* Creating a process
  * Parent process creates a new running child process by calling the function fork()
  * Child is a clone of the parent
    * Child get an identitcal but seperate copy of the parent virtual address space
    * Child gets identitcal (but seperate) copy of the parent's virtual address space
    * Child gets identical copies of the parent's fild descriptors
    * Child has a different PID than the parent
    * fork() is called once but retuns twice.

Example:
* The shell uses fork() to run programs you invoke from the command line
* Web servers (like apache) use fork() to create multiple server processes (each handles requests in its own space). If one dies or leaks memory....
* Google chrome uses for() to handle each page within a seperate process. Prevents client-side code on one page from bringing your whole browser doen
* fork() is used to spawn processes in some parallel programs on different machines 

* Process Graph
  * Graph to model the behavior of concurrent programs
  * Capturing the partial ordering of statements in a concurrent program
  * Each vertex is the execution of a statement
  * a - b means a happens before b
  * Edges can be labeled with current values of variables
  * Each graph begins with a vertiex  with no input edge
  * Any topological sort of the graph corresponds to a feesable ....


<a href="https://ibb.co/6gtSWz7"><img src="https://i.ibb.co/kQDTSjs/image.png" alt="image" border="0"></a>

<a href="https://ibb.co/yyjVtt7"><img src="https://i.ibb.co/G2SFyyN/image.png" alt="image" border="0"></a>


**Reaping Child Process**

* Action of erasing a terminated child process
* When a process terminates, it still consumes system resources
* Terminated process is called a zombie process
* The parent reaps a terminated process using wait or waitpid functions and the kernal deletes the zombie child process. 

* If a parent process does not reap a child process, when the parent terminates, the orphaned child will become a child of the init process
* Explicit reaping is required in long-running processes

Things like terminals will create child process without end and need to be explicitly terminated.

**synchronizing parent process with children**
* Parent reaps explicitly a child by calling the wait funciton
* Suspends the current process until one of its children terminates
* Return value is the pid of the child process that terminated
* If child_status != null, the integer it points to will have a value that indicates the reason is child is terminated and the exit status

<a href="https://ibb.co/wJ3Ck6x"><img src="https://i.ibb.co/YDY8Cjq/image.png" alt="image" border="0"></a>


<a href="https://ibb.co/9s85zxS"><img src="https://i.ibb.co/18vWhCj/image.png" alt="image" border="0"></a>



# 6/23

**Shell**
* shell waits correctly for, and reaps, foreground jobs
* issue with background jobs


## Signals

* High level software form of exceptional control flow
* Processes and the kernal can interrupt other proceess using signals
* Signal is small message that notifies a process that an event of some type has occurred in the system
  * Simlar to exceptiions and interrupts
  * Sent from the kernal to a process
  * Signals have a unique id

* If a process attempts to divide by 0, the kernal sends a SIGFPE(8) to the process
* If a process executes an illegal instruction, the kernal sends a SIGILL(4) to the process
* If a process makes an illegal memory refereance, the kernal sends a SIGSEGV (11) to the process
* If you type CTL-C while a process is running in the foreground, the kernal sends a SIGINT(2) to the process
* A process can forcibly terminate another process by sending it a SIGKILL

**Sending Signals**
* The kernal sends (delivers) s signal to a destination process bu updating some state in the context of the destination process
* The kernal sends a signal for one of the following reasons
  * Kernal has detected a system even such as /0 (SIGFPE) of the termination of a child (SIGCHLD) 
  * Another process has invoked the kill system

**Receiving Signals**
* A destination process receives a singal when it is forced by the kernal to react in some way to the divery of the signal
* Possible ways to react:
  * Ignore the signal
  * Terminate the process
  * Catch the singal by executing a user-level function called signal handler 

**Pending and Blocked signals**
* Pending: signal is sent but not yet recieved - ONly one signal pending for any particular type - If a signal of type k is pending, any other singal of type k sent to the process is discarded
* A process can block the reciept of certain signals - blocked signals can be sent but will not be recieved until the signal is unblocked
* Kernal maintains two bit vectors in the context of each process
* Pending vector- set of pending signals - kernal sets bit k in pending when a signal of type k is delivered - kernals clears bit k in pending when a signal of type k is recieved
* Blokcked vector (signal mask) - set of blocked signals - can be set and cleared by using sigprocmask function (singal mask)

<a href="https://ibb.co/j3dJmms"><img src="https://i.ibb.co/ygD4tt7/image.png" alt="image" border="0"></>

**Sending Signals**
* From the keyboard (ctrlc or ctr)


* The funciton alarm()
* A process can send a SIGNALARM toitself calling the alarm function
  `unsinged int alarm(unsigned int time)`
* The function arranges for the kernal to send a SIGALRM signal to the calling process after time seconds have elapsed


**Recieving Signals**
* Whenever the kernal switches context to process p, it computes pnb = pending & ~blocked set of pending non-blocked signals for process p
* if(pnb==0), pass control to the next instruction in the logical flow of p
* if(pnb!=0), chose at least, non-zero bit k in pnb and force process p to recieve the signal
  * The recipet of the singal triggers some action by p
  * Repeat for all non-zero k in pnb
* Pass control to the next instruction in the logcal flow of p 
* Deafuly predifined actions for signals
  * Process terminates
  * Process stops until restarted by a SIGCONT signal
  * Process ignores the signal
* A process can change the deafult action by defining a handler for the signal
* The only exceptions are SIGSTP and SIGKILL

**Installing signal handlers**
`handler_t *signal(int signum, handler_t *handler);`
* THe signal function modifies the deafult action associated with the recipt of signal signum
* handler is SIG-IGN (ignore) of SIG-DFL (revert to deafult action)
* Or handler is the @ of a user-level signal handler
* Called when the process recieves a signal


* Installing the handler: calling signal()
* Catching the signal: when the handler is called
* Handling the signal: whent he handler is running 
When the handler executes its return statemtn, control is usually passed back to the instruction in the control flow of the process that was interrupter by the receipt of the signal.

* A singnal handler is a seperate logic flow (not a process) that runs concurrently with the main program
* **Nested handlers** - handlers can be interrupted by other handlers 

**Blocking and unblocking signals**


**Signal Handlers**
* Handlers can be tricky for the following reasons:
  * They run concurrently with the main program and chare the same global variables
  * The rules for how and when signals are recicieved are often unintuitive 


# 6/27 missed first 30 minutes

**Explicitly waiting for signals**
* Waiting for signals with sigsuspend
  * `int sigsuspend(const sigest_t *mask)`
* Temporarily replaces the current blocked set with mask and suspends the process until the reciept of a signal
* If the handler is run, sigsupend retruns after the handler returs and restores back to the resolved code



## non-Local jumps 

* Powerful (but dangerous) user-level mechanism for transferring control to an arbitray location
* Break the procedure call discipline
* Useful for error recovers and signal handling

`int setjmp(jmp_buf j)`

`void longjmp...`


**Setjmpp**
* must be called before long jmp
* Identifies a return sitr for a sibsequent longjmp
* Called once, returns one of more times
* Remebers where you are by storing the current register context, stack pointer, and PC value in `jmp_buf`
* returns 0 the first time

**longjmp**
* Return from setjmp remembered by jmp buffer j again...
* ... this time returning i instead of 0
* Called after setjmp
* Called once, but never returns
* Restores register context (stack pointer, base pointer, PC value)


## Virtual memory

* RAM - Array of contiguous bytes
* Physical addressing : CPU sends a physical address to read from or to write in main memory
* Used in simple systems that do one specific thing and run the same programs in the main memory
* Modern computers use virtual addresses that are translated into physical addresses at runtime
* One of the greatest ideas in computer science
* Each process has the impression to work with a private infinte memory space

**Address spaces**
* Linear address space - contiguous integer addresses: {0,1,2,3,...., N-1} requires n bits (N=2^n)
* Virtual address space - Virtual addreess on n bits
* Physical address space - physical address on m bits
  

**Caching**
* Virtual memory (VM)- Array of contiguous bytes stored on disk
* Content from VM is cached in the physical memory
* Data transferred from VM to PM in blocks called pages
* Size of one page is a power of 2 (P=2^p)

**Virtual Page may be**
* Unallocated: not allocated yet in the memory (stack or heap regions) - no data or disk space associated with the @ range
* Uncached: allocated page that is not cached in the physical memory
* Cached: allocated page that is currently cached in the physical memory (region of .text or .data currently being used by the process)

* The partition into pages is driven by the miss penalty of the PM (10x slower than SRAM, 10,000x faster than disk)
  * Large page (block) size: typically 4KB to 2MB
  * Fully associative-any VP can be placed in any PP or frame
  * Highly sophisticated - expensive algorithms
  * Too complicated and open-ended to be implemented in HW
  * Write-back rather than write-through


* The OS uses a data structure (page table) to manage VM
  * Valid bit - page cached/uncached (1/0)
  * Field @ - location of the page in MM or VM 
  * Memory resident kernal data structure 
  * Size = virtual @ space/page size
  *  