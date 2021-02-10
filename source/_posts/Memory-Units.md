---
title: Memory Units
toc: true
date: 2021-02-10 13:08:42
tags: ["Notes", "Coursera", "Nand2Tetris"]
categories: ["Nand2Tetris"]
thumbnail:
---

Given the 1-bit register we learned in the last post, we can build more things!



## The basic memory element: Register (Unit 3.3)

![16-bit Register](/images/Nand2Tetris/16BitRegister.png)

* We use 16-bit **word width** to keep generality
* “Word width” is a parameter `w`, which can be 32-bit, 64-bit, too.

**Register's State:** the value which is currently stored in the register.

---

### Read Logic

This is easy, just probe the `out` and see the outputs.

### Write Logic

Say, we want the register to remember the number `123`. We can:

1. set `in = 123`
2. set `load = 1`
3. The `out` will emit `123` from the next time unit.

---

### How in the Hardware Simulator?

1. Load in the HDL file `nand2tetris\tools\builtInChips\DRegister.hdl`.
2. See the key word `BUILTIN` and `CLOCKED`. This chip is actually implemented by a Java class. When the key word `CLOCKED` is detected, the clock-shaped button will be activated.
3. The "Time: __" will tick to "0+" and then tock to "1". The GUI "D: " on the right displays the value of DFF (defaulted "0"). However, the output pin takes a complete cycle to emit the newly loaded value.

---

## RAM Unit

![RAM Unit](/images/Nand2Tetris/RAMunit.png)

* Abstractly, we view RAM unit as a sequence of $n$ addressable registers, with address `0` to `n - 1`.
* At any point of time, only one register can be selected no matter how many registers exist.
* To represent the address input, it should be $k$ long, where $k = \log_2^n$.
* $n$ has nothing to do with the word width $w$.
* **In a word,** RAM is a sequential chip, and it depends on a clock input.

### Read & Write

The same as a single register, except switching the address code.

---

## A family of 16-bit RAM chips

The family has the same generic architecture as showed above.

As the number of registers, $n$, goes up, the chips are RAM8, RAM64, RAM32, RAM4K, RAM16K... Accordingly, $k$ is respectively 3, 6, 9, 12, 14...

**Why these 5 particular RAM chips?**

Stay tuned... we need them for the next Hack Computer.

---

## Why "Random Access"?

RAM stands for "Random Access Memory", because a magic thing is, once the address code is provide, no matter how many registers, 8 or 8 million, the data is accessible after the same moment.


