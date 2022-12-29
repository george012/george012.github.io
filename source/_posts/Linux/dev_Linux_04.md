---
title: Ubuntu 14.0.4 配置静态IP
date: 2015-04-18
type: post
tags: Linux
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 参数说明](#1-参数说明)
- [2. 编辑"/etc/network/interfaces"文件](#2-编辑etcnetworkinterfaces文件)
- [3. 编辑"/etc/resolvconf/resolv.conf.d/base"文件](#3-编辑etcresolvconfresolvconfdbase文件)
- [4. 重启networking服务使其生效：](#4-重启networking服务使其生效)
- [5. PS:](#5-ps)

<!-- /TOC -->
----

# 1. 参数说明

* 本例以192.168.1.0(255.255.255.0)网段为例

----

# 2. 编辑"/etc/network/interfaces"文件
*	```
	sudo vi /etc/network/interfaces
	```

*	新增如下内容
	```
	auto eth0
	iface eth0 inet static
	address 192.168.1.88
	netmask 255.255.255.0
	gateway 192.168.1.1
	```

# 3. 编辑"/etc/resolvconf/resolv.conf.d/base"文件
*	```
  	sudo vi /etc/resolvconf/resolv.conf.d/base
	```
*	输入如下内容

	```
	nameserver 192.168.1.1
	nameserver 8.8.8.8
	```

# 4. 重启networking服务使其生效：

```
/etc/init.d/networking restart
```

------

# 5. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

* 参考资料:

	* 1、[ubuntu 14.10系统怎么设置静态ip？][2]
	* 2、[Ubuntu Server 12.04(14.04) 静态IP简洁配置][3]

------


[1]:http://www.wmyeah.com
[2]:http://jingyan.baidu.com/article/1612d500a0348ee20e1eee0d.html
[3]:http://blog.csdn.net/ichsonx/article/details/40040935
