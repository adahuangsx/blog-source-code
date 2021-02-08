---
title: "Project 2: Boolean Arithmetic"
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
   * (Make sure to use them like "Mux" or "And" precisely, because the simulator always looks for the chips in the current directory, and then if finds nothing, it will kick in and use the automatic built-in version at last.)

---

## Some Questions This Week

**Q. We have built nearly 20 chips. Are they standard? or are they typically used in the computer systems?**
A. Yes, the gates this week like Half Adder and Full Adder are standard, as well as the 16 chips built in the last project like "Mux" and "Xor", except ALU, which is extremely simplified from the actually used one. So, this ALU is a bit unique among usual ALUs.


**Q. How does the ALU we built operates multiplication and division?**
A. There is no problem to write HDL code that specifies chips to carry out these operations by working directly on bits. In fact, there are some elegant algorithms to do that. Designers are free to decide how much functionality to put into each layers. In this course, we put multiplication and division into the software that runs on the top of the computer to keep ALU simple.

Also, this is another trade-off since hardware functionality runs much faster but costly. However, the high-level programmers will not feel this difference.


**Q. Is the ALU efficient?**
A. Almost everything we build is efficient, but some optimization is still possible. For example, the adder. Say there is a 32-bit adder, and to compute all the 32 bits, we need to connect all of the 32 Full Adders with the carries along the significance ladder. 

But don't forget that a Full Adder is made of 3-4 other chips. So, the total **delay** would be $32 * 3 $. One optimization is the carry that goes one of the Full Adders at the top. We can, instead, compute this MSB carry in a more efficient way. This is called **"carry look ahead"**.


**Q. Why using the built-in chips, not the ones we built in the Project 1?**
A. You are more than welcomed to use them. However, using built-in chips is good for unit-testing and prevent the bugs from being messed up.	

---

## While doing it （感想及常见错误）

这次的作业感觉就是上次的延伸。只有5个chip，而且是前4个adder层层递进。

最后一个ALU是难点，重要的是要把上一次作业的chips利用起来。比如对于`zx`或`nx`，如何通过一个bit是零还是壹而输出不同的值，则应该想到Mux（多路器）。

还有仍然要小心”sub-bus“的错误，那就是`[xx..xx]`只能出现在`..., out=out)` 中的等号左边而不能pipe到其他chip的`(in=...,)`里，而形如`..., out=out[0..7])`则会报`Sub bus of an internal node may not be used`的错误。例子如下：

```vhdl
SomeGate(..., out=foo);
Or8Way(in=foo[0..7], out=p1);
Or8Way(in=foo[8..15], out=p2); // ERROR
```

这样是不对的，因为`foo`是个中间产生的变量名，它在HDL中不能用sub-bus的方式作为另一个chip的“in=”。

Instead，

```vhdl
SomeGate(..., out[0..7]=foo1);
SomeGate(..., out[8..15]=foo2);
Or8Way(in=foo1, out=p1);
Or8Way(in=foo2, out=p2);
```

应该像上面这样把2个narrower buses分别输出。代码的意思是“foo1接收了out的[0..7]位并被赋值成了8-bit的值”。

也可以像这样把多个narrowing合并起来：

```vhdl
SomeGate(..., out[0..7]=foo1, out[8..15]=foo2);
```

以上可以参照[Survival Guide](https://www.nand2tetris.org/hdl-survival-guide) 中的“sub-busing”部分。

---




## Reference
> - [Project 2 Main page](https://www.nand2tetris.org/project02)
> - [The HDL Guide](https://drive.google.com/file/d/1dPj4XNby9iuAs-47U9k3xtYy9hJ-ET0T/view)
> - [The Hack Chip Set API](https://drive.google.com/file/d/1IsDnH0t7q_Im491LQ7_5_ajV0CokRbwR/view)
