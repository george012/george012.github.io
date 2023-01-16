---
title: CocoaPods使用问题汇总
date: 2018-04-08
tags: [iOS]
categories: [iOS]
---

<font size=20>目录：</font>
<!-- TOC -->

- [说明:](#%E8%AF%B4%E6%98%8E)
- [将变化提交到暂存区](#%E5%B0%86%E5%8F%98%E5%8C%96%E6%8F%90%E4%BA%A4%E5%88%B0%E6%9A%82%E5%AD%98%E5%8C%BA)
- [PS:](#ps)

<!-- /TOC -->
# 1. 说明:

* <font color=red>CocoaPods 使用过程中得问题记录</font>


# 2. 将变化提交到暂存区

*   Q:
    *   gem install cocoapods ERROR: While executing gem ... (Gem::FilePermissionError)
    A:
    *   改用如下命令
        ```
        sudo gem install -n /usr/local/bin cocoapods
        ```


# 3. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!


 [1]]:http://www.wmyeah.com
