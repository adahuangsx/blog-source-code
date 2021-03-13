---
title: Input and Output
toc: true
date: 2021-03-10 17:58:42
tags: ["Notes", "Coursera", "Nand2Tetris"]
categories: ["Nand2Tetris"]
thumbnail:
---

We will learn to use bits to manipulate the peripheral devices.

## Screen Memory Map

There is a display unit (256 * 512, b/w)

The **Screen Memory Map** is a sequence of 16-bit values, each of which is called "a word". Altogether we have 8k (8192), 16-bit words, because there should be this much bits (one for each pixel).

**Note that** the read/write operations are only 16-bit, not individual bits.

### Screen

We are going to implement the memory map with a chip called **Screen**. It's an 8k chip, behaving exactly as a memory unit.

When we build the overall computer, this chip will be part of the data memory (or RAM). In other words, Screen is only one chip among a bunch of other chips.

To access the Screen chip in RAM, the addressing needs to add the base address (say, 16384). 

### How to set a pixel

To set a pixel (`row`, `col`) on or off:

1. `word = Screen[32 * row + col / 16]`
   `word = RAM[16384 + 32 * row + col / 16]`
2. Set the `col % 16` -th bit of `word` to zero or one.
3. Commit `word` to RAM

---

## Keyboard Memory Map

This is the chip which a physical keyboard is associated with. Its memory map needs no more than 16 bits, which is a single register. Every key has an agreed-upon value as a scan code.

When I lift my finger or the keyboard is idle, the memory map returns **zero**.

In Hack computer, it is in `RAM[24576]`.

