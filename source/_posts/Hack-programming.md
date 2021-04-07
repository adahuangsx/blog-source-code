---
title: Hack Programming
toc: true
date: 2021-03-13 16:21:12
tags: ["Notes", "Coursera", "Nand2Tetris"]
categories: ["Nand2Tetris"]
thumbnail: /images/Nand2Tetris/hackHardware.png
---

# Working with Registers and Memory

### Let's recall

* D: data register
* A: address / data register 
* M: the currently selected memory register: `M = RAM[A]`

### Typical operations

```java
// D=10
@10
D=A
// D++
D=D+1
// D=RAM[17]
@17
D=M
// RAM[17]=D
@17
M=D
// RAM[17]=10
@10
D=A
@17
M=D
// RAM[5] = RAM[3]
@3
D=M
@5
M=D
```



## How to end the program properly?

The program will keep executing even if the instructions are run out (blank instructions). An evil hacker will put some uncontrollable codes to slide the flow of control to a memory area they can control.

This attack is called **NOP slide**, Null Instructions or Null Opcodes. 

Note that the computer can never stand still. It is always doing something even when the keyboard is idle. There are many processes running in the back ground. **A good practice** is to end everything in the program with an infinite loop, like:

```vhdl
...
...
...
@4     // A - "4" because this line is ROM[4]
0;JMP  // "0" is always "== 0", so it is stuck in these 2 lines.
```

 

---

## Build-in Symbols

### virtual registers

Hack has 16 virtual registers from `R0` to `R15`. They have exactly the same value as its position: `R5` has the value of `5`. 

**The reason** we need this is: the A-instruction has 2 functionalities, so it may get confusing sometimes. We will not know if it is an address or a number until seeing the next instructions. Therefore, we give it different labels:

![](D:\Winter 20\blog\themes\wikitten\source\images\Nand2Tetris\why virtual registers.png) 

PS: Hack is case-sensitive. "R5" != "r5"

### Base Addresses of I/O Maps

```vhdl
SCREEN   16384
KBD      24576
```

### Remaining symbols

They are used in the implementation of the Hack virtual machine.



---



# Branching

The code of branching is taught in the C-instruction `jump` unit.

To make the Hack assembly code more readable, we introduce the label. (就是代码块的跳转标记). Its syntax is:

```java
		@LABEL		// use the label
		D;JGT
		...
(LABEL)	 @233		// declare the label
		M=D
		...
```

`@LABEL` translates to `@n`, where  `n` is the instruction number following the (`LABEL`) declaration.

Similar to `goto`.

---

# Variables

In Hack, we only have 1 type of variables, which is 16-bit.

 For example, there is a variable called "temp":

```java
// Program: Flip.asm flips the values of RAM[0] and RAM[1]:
// temp = R1
// R1 = R0 
// R0 = temp
...
@temp
M=D // temp = R1
...
@temp
D=M
@R0
M=D // R0 = temp
```

**That is how `@temp` works:** Find some available register, and use it to represent the variable `temp`. So from now on, every occurrence of `@temp` will be translated into `@n`.

Another nice virtue is that the program is **relocatable** code, as long as the base address is known.

**Note:** 怎么判断`@` 符操作是branching还是variable？
variable没有`(LABEL)` 这样的declaration，而branching一定有代码段中的标记。variable的声明在变量区。

---

# Iteration

**Recommended Tips:**

* Write Pseudo code first, then translate it into machine language;
* Debug by simulating with **trace table**;



---

# Pointers

![](D:\Winter 20\blog\themes\wikitten\source\images\Nand2Tetris\pointers in one slide.png)

The typical operation is **the red instruction**: set the address register to a given value. Before this unit, `A` is never on the left of the equation.

`A = xx` 就可以看做是`@xx`，这样后面一行如果看到`M`，就更容易理解了。

---

# Input & Output

## Example: Rectangle Drawing

### Coding Practice:

赋值常数给变量：

```java
@SCREEN
D=A
@addr
M=D
// addr = 16384
```

赋值简单的值（如初始化）：

```java
@i
M=0
// i = 0   
// ??? 为什么不是RAM[i] = 0?
// 解答：i在这里是变量，自动分配一个地址，比如n，给这个变量。所以现在i表示的是n那个数字。
```

取地址赋值（唯一的A在等式左边）：

```java
@addr 	// A = addr
A=M		// 此时M为RAM[addr], 即@RAM[addr]
M=-1	// *addr = -1
// RAM[addr] = 1111111111111111
```


