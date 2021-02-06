---
title: "Project 1: Boolean Logic"
toc: true
date: 2021-01-25 22:08:14
tags: ["Notes", "Coursera", "Nand2Tetris"]
categories: ["Coursera", "Nand2Tetris"]
thumbnail: /images/Nand2Tetris/the-course-is-about.png
---

## Project 1 Goal (Unit 1.8)

Given a NAND, build all the gates.

![上帝：“去造个计算机。”](/images/Nand2Tetris/the-course-is-about.png)

课上给了Project 1的其中几个chips的讲解。讲了Mux, DMux, And16 和 Mux4Way16。

---

## Project 1 Overview

### Multiplexor (多路器) or Mux

```vhdl
IN a, b, sel  // "sel" means "selection bit".
OUT out

if (sel == 0)
	out = a
else
	out = b
```

**Tip:** You can build with AND, OR, NOT gates.

#### Example: AndMuxOr

```vhdl
IN a, b, sel
OUT out

if (sel == 0)
	out = a AND b
else
	out = a OR b
```

**Tip:** 这个可以很容易用`Mux`做出来。

---

### Demultiplexor(分路器) or DeMux

It is like the "inverse" of Mux.

```vhdl
IN in, sel
OUT a, b

if (sel == 0)
	(a, b) = (in, 0)
else
	(a, b) = (0, in)
```

**Note:** 以上两个都在communication networks中经常使用。比如Mux和DMux之间就可能是一个海底光缆的单线信息流，两头分别进行汇总和分流。如下图：

![Communication Networks](/images/Nand2Tetris/muxANDdmux.png)

这里的`sel`就是oscillator（振荡器）。

这样做可以减少昂贵的物理传输费用，还可以做到encoding和decoding异步进行。

---

### And16

**Tip:** 16个bit是无顺序可言的，就像同时放出来的一样。

---

### Mux4Way16

```vhdl
IN a[16], b[16], c[16], d[16], sel[2];
OUT out[16];
// 'sel' has 2 bits to represent 4 ways.
```

---

---

### Some tips for this assignment

* 尽量按顺序完成，这样后面的就可以用到前面写好的helper chips。
* 不按顺序也可以，但是当用到一个没写好的chip比如`chip AND {}`，可以把文件名临时改成`And.hdl233`。这样系统会自动调用内建的chip。
* chip不能调用自己。
* 记得看HDL Survival Guide 和各种资源！

* VSCode 居然有Nand2Tetris的专门编辑.hdl文件的插件。
![](/images/Nand2Tetris/vscode.png)


### Some tips when doing it

* 变量名不要用下划线！（别问我怎么知道的……）



## 参考资料
> - [Hardware Simulator Tutorial](https://b1391bd6-da3d-477d-8c01-38cdf774495a.filesusr.com/ugd/44046b_bfd91435260748439493a60a8044ade6.pdf)
> - [HDL Survival Guide](https://www.nand2tetris.org/hdl-survival-guide)
> - [其他资源在这里，大都是google doc的](https://www.nand2tetris.org/project01)
