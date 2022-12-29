---
title: Windows 一键查看已连接过的WIFI密码
date: 2016-10-26
type: post
tags: Linux
---

<font size=20>目录：</font>

<!-- TOC -->

- [1. 说明:](#1-说明)
- [2. CMD命令](#2-cmd命令)
- [3. PS:](#3-ps)

<!-- /TOC -->
----

# 1. 说明:
* <font color=red>WARNING 请谨慎使用此命令，一切造成的后果请各位自行承担</font>

----

# 2. CMD命令
```
for /f "skip=9 tokens=1,2 delims=:" %i in ('netsh wlan show profiles') do  @echo %j | findstr -i -v echo | netsh wlan show profiles %j key=clear
```	

------

# 3. PS: 

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

------

[1]:http://www.wmyeah.com
