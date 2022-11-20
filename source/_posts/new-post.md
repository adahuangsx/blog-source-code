---
title: 三、存储与检索
toc: true
date: 2022-05-20 14:34:49
tags: ["DDIA", "Notes"]
categories: ["DDIA"]
---

## 引言

两大类存储引擎：日志结构（log-structured） 的存储引擎，以及 面向页面（page-oriented） 的存储引擎（例如 B 树）。

* 日志
一个 仅追加（append-only） 的数据文件
写入非常快，但是搜索效率很低

* 索引
trade-off：加快了读查询的速度，但是每个索引都会拖慢写入速度

## 索引结构

### hash 索引 -- 内存里的键值数据（key-value Data） 的索引








## 参考资料
> - [DDIA 中文网页版](https://github.com/Vonng/ddia)
> - [ MIT 6.824 Distributed Systems 的视频](https://www.bilibili.com/video/BV1x7411M7Sf?from=search&seid=15149782867482872906&spm_id_from=333.337.0.0)
