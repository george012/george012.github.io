---
title: git相关配置
date: 2017-07-17
tags: [Git]
categories: [Git]
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 说明:](#1-说明)
- [2. 关于`LF`和`CRLF`的处理](#2-关于lf和crlf的处理)
  - [处理`core.autocrlf`](#处理coreautocrlf)
  - [处理`core.safecrlf`](#处理coresafecrlf)
- [处理案例:](#处理案例)

<!-- /TOC -->
# 1. 说明:

* <font color=red>git相关配置，方便跨平台</font>

# 2. 关于`LF`和`CRLF`的处理

## 处理`core.autocrlf`
* core.autocrlf 的默认值是false
* `core.autocrlf`是git中负责处理`line ending`的变量，可以设置3个值：
    *   `true` 提交时改成LF，检出时改成CRLF
    *   `input` 提交时改成LF，检出时不改
    *   `false` (默认值) 提交时是什么就是什么，不改换行符，检出时也不

## 处理`core.safecrlf`
* 默认值是warn
* `core.safecrlf` 默认值可设置3个：
  * `true`  拒绝提交包含混合换行符的文件		（会提示 Fatal:xxx）
  * `false` 允许提交包含混合换行符的文件 
  * `warn` 提交包含混合换行符的文件时给出警告		(默认值)

# 处理案例:
```
git config --global core.autocrlf input

git config --global core.safecrlf true
```

<h3 id = "ps">PS:</h3>

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

------

 [1]]:http://www.wmyeah.com
