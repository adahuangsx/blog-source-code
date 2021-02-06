---
title: Binary and Arithmetic
toc: true
date: 2021-02-05 19:08:31
tags: ["Notes", "Coursera", "Nand2Tetris"]
categories: ["Coursera", "Nand2Tetris"]
thumbnail: https://i.ytimg.com/vi/kcORYKPL53o/maxresdefault.jpg
---

Adding two numbers in binary representation is pretty simple. Here we are gonna build an Adder for binary numbers.

## Why does the Adder matter most?

<u>**Adder** + Negative representation = **Subtraction**</u>

<u>**Multiplication** and **Division** are not hardware's work, but software's.</u>

## Three steps to build an Adder

* Half Adder: adds 2 bits
* Full Adder: adds 3 bits (used in "carry a 1")
* Adder: adds 2 numbers

### Half Adder: adds 2 bits

When we focus on a single slice of bits adding, like "1 + 1", it has 2 outputs: a carry bit "1" and a result bit "0".

(truth table)

(chip code)



`CHIP HalfAdder` is the first thing we need to implement in **Project 2**.

### Full Adder: adds 3 bits 

The last **Half Adder** is only for the case when carry is "0", while **Full Adder** includes adding the carry and 2 bits together.

(truth table)

(chip code)

### Adder: adds 2 numbers

Assuming the numbers are **16-bit long**, we can implement it by connecting <u>16 Full Adders</u> or <u>15 Full Adders and 1 Half Adder</u> for the right-most bits.

---


## Negative Numbers

**2's complement** is elegant, and it enables us to do subtraction (negative addition) exactly the same way as addition.

### Computing "-x"

By solving this, we can deal with subtraction! So, **no more hardware needed** for it!~
$$
-x = 2^n-x = 1 + (2^n - 1) - x
$$
**Why converting this way?**

Because $(2^n-1) $ is "all ones", which makes subtraction very easy (no need to borrow anything!). ---> JUST FLIP THE BITS

Then, add one. ---> easy.

## Negation steps in one word:

1. Flip all the bits;
2. Add one.




