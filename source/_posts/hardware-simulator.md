---
title: Hardware simulator
toc: true
date: 2021-01-23 22:15:40
tags: ["Notes", "Coursera", "Nand2Tetris"]
categories: ["Coursera", "Nand2Tetris"]
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





