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