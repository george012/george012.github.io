---
title: 嵌入式开发之MacOS、iOS串口通讯开发环境准备
date: 2016-10-27
type: post
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 说明](#1-说明)
- [2. 准备串口线及对应串口传唤器驱动](#2-准备串口线及对应串口传唤器驱动)
	- [2.1. 线材准备](#21-线材准备)
	- [2.2. 对应驱动准备](#22-对应驱动准备)
- [3. 下载可视化连接工具"CoolTerm\_Mac"](#3-下载可视化连接工具coolterm_mac)
- [4. 验证是否驱动安装完成](#4-验证是否驱动安装完成)
- [5. PS:](#5-ps)

<!-- /TOC -->

----

# 1. 说明

* <font color=red>WARNING 凡所涉及线材及设备,请自行准备此处仅为当前条件随便购买</font>

----

# 2. 准备串口线及对应串口传唤器驱动
## 2.1. 线材准备
*	[优越者 Y-105 USB转RS232  工口][2]

*	[优越者 Y-105D USB转RS232 母口][3]

## 2.2. 对应驱动准备
* 购买线材时随附光盘中一般会有

* ![](img/wm_article_Mac-iOS_01.png)

* 点这里下载[基于PL-2303芯片驱动][8]

* 点这里下载[CH430G For Mac 驱动下载][9]

* 点这里下载[CH430G For Linux 驱动下载][10]


# 3. 下载可视化连接工具"CoolTerm_Mac"
* [CoolTerm_Mac下载地址][7]


# 4. 验证是否驱动安装完成
*	设置连接选项
	* ![](img/wm_article_Mac-iOS_02.png)

*	在另一台准备好的机器上输入测试字符

	* ![](img/wm_article_Mac-iOS_03.png)

------

# 5. PS:
* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

* 参考资料:

	* 1、[Roger Meier's Freeware][4]
	* 2、[Mac's and serial TTY's][5]
	* 2、[在MAC OS X下安装usb转串口驱动（PL2303主控芯片）][6]

------

[1]:http://www.wmyeah.com
[2]:http://www.unitek-it.com/html/products/usbchuankoubingkou/92.html
[3]:http://item.jd.com/2176746.html
[4]:http://freeware.the-meiers.org/
[5]:http://pbxbook.com/other/mac-tty.html
[6]:http://www.cnblogs.com/humaoxiao/p/3594953.html?utm_source=tuicool&utm_medium=referral

[7]:http://soft.wmyeah.com/CoolTerm_Mac.zip
[8]:http://soft.wmyeah.com/PL2303_Unitek.zip
[9]:http://www.wch.cn/download/CH341SER_MAC_ZIP.html
[10]:http://www.wch.cn/download/CH341SER_LINUX_ZIP.html
