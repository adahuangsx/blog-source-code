---
title: 5-Computer Architecture
toc: true
date: 2021-04-15 21:08:31
tags: ["Notes", "Coursera", "Nand2Tetris"]
categories: ["Nand2Tetris"]
thumbnail: /images/Nand2Tetris/VonNeumannBuses.png
---

## Buses in Von Neumann Architecture (Unit 5.1)

3 Information flows (bus):

![Information Flows](/images/Nand2Tetris/VonNeumannBuses.png)



## The Fetch-Execute Cycle (Unit 5.2)

**The basic CPU loop:**

* **Fetch an Instruction** from the **Program Memory**
* **Execute** it.
* Repeat this.

### Fetching

* Put the location of the next instruction in the Memory address input (Program Counter)
* Get the instruction code by reading the contents at that Memory location

### Program Counter

![Program Counter](/images/Nand2Tetris/Program%20Counter.png)



### The Fetch-Execute Clash

The instructions and data pieces are stored in a single memory, so there is a clash.

**Solution:**

![](/images/Nand2Tetris/Clash%20Multiplexer.png)



**Simpler Solution (Harvard Architecture):**

To separate the data memory and program memory into 2 modules.
No need to switch between fetching and executing.