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