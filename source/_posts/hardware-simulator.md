---
title: Hardware simulator
toc: true
date: 2021-01-23 22:15:40
tags: ["Notes", "Coursera", "Nand2Tetris"]
categories: ["Nand2Tetris"]
thumbnail: https://i.ytimg.com/vi/kcORYKPL53o/maxresdefault.jpg
---

这两个单元主要是介绍了软件怎么用，怎么test和生成output。
简介了Hardware Description Language (HDL) (unit 1.4)



## Hardware simulator (unit 1.5)

### Feel free to "kick the tires"!

* The simulator is written in Java.
* The download link is [here](https://www.nand2tetris.org/software).
* The simulator is invoking in `nand2tetris/tools/HardwareSimulator.bat`.
* It can check both output pins and internal pins.

### Script-based simulation

HDL code `.hdl` + test script  `tst` -----> into simulator -----> Output file `.out`

**Note that** this way to debug by checking the output file is rare in real life testing, because a real chip is far more complex than an Xor chip. A more systematic and planned method is going to be introduced next.

### Script-based simulation with compare files

The compare file `.cmp`, whose previous incarnation (前身) is a correct output file.

---

## Hardware Construction Projects

* ### System architects

  * chip API
  * test script
  * compare file

* ### Developers

  * build the chip with HDL

**In this course, we play the role of developers.**


---

## Multi-Bit Buses

*"Bus" means "many" in Latin.*

### Some Syntax Notes

Say, an integer is `aaa[16]`:

* `aaa` is the integer's name
* `aaa[0]` is its first bit. （注意是LSB，就是最低位/最右边的一位。）
* `aaa[7..15]`, with 2 dots in the middle, means its sub-bus.

Other syntaxes:

* `true` and `false` can represent a bus with constant signal of any width.

---

补充一个后面答疑问到的几个关于HDL的问题：

Q. 这门课中的HDL语言是现实中使用的吗？
A. 很相似，比如和VHDL相比，VHDL可能在基本的HDL基础上加了一些类C的语言，比如For这些。（所以code block我也就近用了VHDL的高亮）




