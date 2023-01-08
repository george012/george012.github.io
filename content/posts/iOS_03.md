---
title: CocoaPods使用问题汇总
date: 2018-04-08
tags: [iOS]
categories: [iOS]
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 说明:](#1-说明)
- [2. 将变化提交到暂存区](#2-将变化提交到暂存区)
- [3. PS:](#3-ps)

<!-- /TOC -->

----

# 1. 说明:

* <font color=red>CocoaPods 使用过程中得问题记录</font>

----

# 2. 将变化提交到暂存区

*   Q:
    *   gem install cocoapods ERROR: While executing gem ... (Gem::FilePermissionError)
    A:
    *   改用如下命令
        ```
        sudo gem install -n /usr/local/bin cocoapods
        ```

------

# 3. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

------

[1]:http://www.wmyeah.com
