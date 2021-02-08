---
title: Hello, Time!
toc: true
date: 2021-02-08 16:06:54
tags: ["Notes", "Coursera", "Nand2Tetris"]
categories: ["Nand2Tetris"]
thumbnail: https://i.ytimg.com/vi/kcORYKPL53o/maxresdefault.jpg
---



## Sequential Logic

In this unit we introduce the issue of **time** into the system, since we didn't have the <u>notion of change</u> before. To simplify the concept, we divide time into atomic pieces, which is **clock**.

### Clock

Clock can be viewed as an oscillator at a certain fixed rate, of which each cycle is treated as a time unit, like time 0, time 1 and so on.

The signals are viewed as a indivisible thing **as if nothing changes within each time unit**. As a input signal is renewed every cycle, the output signal instantaneously follows (几乎同时). 

**You may wonder if this is real.** Indeed, there may be delay in physical electrical signals. But, we can think it as a way that **the voltage change** (the grey area in the screenshot below) **happens between cycles**, while luckily, the cycles are a little bit wider than this instability. So, it is safe to ignore it and focus on the end of each time unit. 

![](/images/Nand2Tetris/theClock.png)

Also, (my guess) **another reason** can be given by the answer "Why binary?". ---> it may takes time to reach the final and consistent stage but not necessarily precise but it's already enough to tell zero from one.



## 参考资料
> - []()
> - []()
