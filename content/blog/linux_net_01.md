---
title: Linux Net相关命令收集
date: 2016-01-06
tags: [Linux,Net]
categories: [Linux,Net]
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 查看`443`的`TCP`连接数](#1-查看443的tcp连接数)
- [2. PS:](#2-ps)

<!-- /TOC -->


# 1. 查看`443`的`TCP`连接数
```
netstat -anp | grep :443 | grep ESTABLISHED | wc -l
```
或者
```
lsof -i:443 | grep ESTABLISHED | grep TCP | wc -l
```

# 2. PS:
* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

[1]]:http://www.wmyeah.com
