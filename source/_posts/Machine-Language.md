---
title: Machine Language
toc: true
date: 2021-03-06 13:08:42
tags: ["Notes", "Coursera", "Nand2Tetris"]
categories: ["Nand2Tetris"]
thumbnail: /images/Nand2Tetris/hackHardware.png
---

## Overview (Unit 4.1)

**Alan Turing** raised the idea of **Universality** and considered the theoretical model.

This idea was turned into practice by **Von Neumann**, who built the first serious architecture of a general computing machine.

## How the Instructions look in a computer

`0100010 0011 0010`

`     ADD   R3   R2` : 	Add R3 to R2

---

## Memory Hierarchy

Accessing memory directly could be costly, because the addresses are long, and getting a value from a large bulk of memory is very slow compared to the CPU speed.

Therefore, instead of just having a large block of memory, we do it in a whole sequence of memories that get bigger and bigger.

**Register** (Data Registers, Address Registers) -> **Cache** -> **Main Memory** -> **Disk**

---

## Hack Computer

### Hardware

![Hardware Structure](/images/Nand2Tetris/hackHardware.png)

Say, this is a 16-bit computer:

* Data memory (**RAM**): a sequence of 16-bit registers
  * `RAM[0], RAM[1], RAM[2],`… 
* Instruction memory (**ROM**, read-only): a sequence of 16-bit registers: 
  * `ROM[0], ROM[1], ROM[2],`… 
* Central Processing Unit (CPU): performs 16-bit instructions 
* **Buses**: Instruction bus / data bus / address buses

### Software

**Hack program** is sequence of instructions written by the Hack machine language.

**Hack Machine Language:**

* 16-bit A-instructions
* 16-bit C-instructions

### How does the program run? (Control)

1. The Hack program loads in the ROM;
2. `reset` button is pushed;
3. The program start running.

### Registers

The Hack computer recognizes 3 registers:

* D: used to store data
* A: used to store data / address the memory 
* M: represents the currently addressed memory register: `M = RAM[A]`

---

## The A-instruction Syntax

`@value` means (1) set the register to the value `value`; (2) select the register `reg[value]`, or the M register above.

**Example:**

```assembly
# Set RAM[100] to -1
@100  # A = 100
M = -1  #RAM[100] = -1
```

Because A is for "addressing".

### Binary Syntax

The number after ampersand "@" is a small non-negative number ($0 ~ 2^15 - 1$).

So, the "@" becomes **a leading zero** in Binary syntax.

```assembly
# @21 would be
0 00000 00000 10101
```

---

## The C-instruction Syntax

```assembly
dest = comp; jump
```

![C-instruction Syntax]/images/Nand2Tetris/C-instruction%20Syntax.png)

**Note:**

1. Compute the value of `comp`, and store it into `dest`;
2. `jump` represents comparing with **zero**;
3. `JMP` means unconditional jump. A convention is do `0; jmp`, and this is an unconditional jump;
4. If the Boolean Expression (`comp jump 0`) is true, then jump to execute the next instruction stored in RAM[A];
5. Remember to "address" the register first.

**Example:**

```assembly
# Sets RAM[300] to the value of the D register plus 1
@300 # A = 300
M=D+1 # RAM[300] = D + 1
```

```assembly
# If (D-1 == 0) jumps to execute the instruction stored in ROM[56]
@56 # A = 56
D-1;JEQ # if (D-1 == 0) goto to instruction ROM[A]
```

### Binary Syntax

![C-instruction Binary Syntax](/images/Nand2Tetris/C-instruction%20Binary%20Syntax.png)

The complete specification is:

![C-instruction Specification](/images/Nand2Tetris/C-instruction%20Specification.png)





