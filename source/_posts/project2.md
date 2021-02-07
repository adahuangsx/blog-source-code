---
title: "Project 2: ALU"
toc: true
date: 2021-02-07 09:38:22
tags: ["Notes", "Coursera", "Nand2Tetris"]
categories: ["Coursera", "Nand2Tetris"]
thumbnail: https://i.ytimg.com/vi/kcORYKPL53o/maxresdefault.jpg
---

## Previous Topic

The previous post has elaborated 3 things we need to implement: **Half Adder**, **Full Adder** and **16-bit Number Adder**. The next is a simpler one: **16-bit Incrementor**.

## Other Two Chips


### 16-bit Incrementor

**Tip:** A single bit "0" or "1" can be represented by `true` or `false` in HDL.



### ALU

**Tips:** 

1. This can be built with the chips in Project 1
2. Only less than 20 lines of HDL code are needed.
3. No need to use my own implementation in Project 1, but instead, the best practice is to use their built-in versions. 
   * (Make sure to use them like "Mux" or "And" precisely, because the simulator always looks for the chips in the current directory, and if finds nothing, it will kick in and use the automatic built-in version.)

---



## Some Questions in this week:

**Q. We have built nearly 20 chips. Are they standard? or are they typically used in the computer systems?**
A. Yes, the gates this week like Half Adder and Full Adder, as well as the 16 chips built in the last project like "Mux" and "Xor", except ALU, which is extremely simplified from the actually used one. So, this ALU is a bit unique among usual ALUs.


**Q. How does the ALU we built operates multiplication and division?**
A. There is no problem to write HDL code that specifies chips to carry out these operations by working directly on bits. In fact, there are some elegant algorithms to do that. Designers are free to decide how much functionality to put into each layers. In this course, we put multiplication and division into the software that runs on the top of the computer to keep ALU simple.

Also, this is another trade-off since hardware functionality runs much faster but costly. However, the high-level programmers will not feel this difference.


**Q. Is the ALU efficient?**

A. Almost everything we build is efficient, but some optimization is still possible. For example, the adder. Say there is a 32-bit adder, and to compute all the 32 bits, we need to connect all of the 32 Full Adders with the carries along the significance ladder. 

But don't forget that a Full Adder is made of 3-4 other chips. So, the total delay would be $32 * 3 $. One optimization is the carry that goes one of the Full Adders at the top. We can, instead, compute this MSB carry in a more efficient way. This is called **"carry look ahead"**.


**Q. Why using the built-in chips, not the ones we built in the Project 1?**

A. You are more than welcomed to use them. However, using built-in chips is good for unit-testing and prevent the bugs from being messed up.	






## Reference
> - [Project 2 Main page](https://www.nand2tetris.org/project02)
> - [The HDL Guide](https://drive.google.com/file/d/1dPj4XNby9iuAs-47U9k3xtYy9hJ-ET0T/view)
> - [The Hack Chip Set API](https://drive.google.com/file/d/1IsDnH0t7q_Im491LQ7_5_ajV0CokRbwR/view)
