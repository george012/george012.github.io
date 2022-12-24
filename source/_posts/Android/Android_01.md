---
title: Android JNI编译so动态库技巧(Mac环境)
date: 2016-11-25
tags: Android,JNI,so,SDK
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 工具及环境](#1-工具及环境)
  - [1.1. 系统及硬件平台](#11-系统及硬件平台)
  - [1.2. 软件及相关工具包](#12-软件及相关工具包)
- [2. PS:](#2-ps)

<!-- /TOC -->

----

# 1. 工具及环境

## 1.1. 系统及硬件平台
* MacBook Air(made on 2013)
* MacOS Sierra(10.12.1)

## 1.2. 软件及相关工具包
* Eclipse(Neon)Java EE IDE For Mac(主要为了省事兼顾Java后台CodeReview、根据自身需求选择Eclipse版本)
* ADT(23.0.7) -PS:Goole官方ADT插件
* Android SDK Manager Tools(24.0.1) 
	*	-PS：有了这个就可以选择下载最新的Android SDK 了（2016-3月份后SDK的下载已经不被墙了，国内多地使用过，操作地域：太原，北京、深圳、西安、上海、杭州）
* NDK(version-13b)

----

# 2. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

* 参考资料:

    * 1、[Xcode 6制作动态及静态Framework][2]

------

[1]:http://www.wmyeah.com
[2]:http://www.cocoachina.com/ios/20141126/10322.html