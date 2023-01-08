---
title: Ubuntu 14.0.4 phpMyAdmin 报错："缺少mcrypt扩展,请检查 PHP 配置"解决方案
date: 2016-01-06
tags: [Linux]
categories: [Linux]
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. mcryp模块安装](#1-mcryp模块安装)
- [2. mcrypt模块加载](#2-mcrypt模块加载)
  - [2.1. 开启mcrypt模块](#21-开启mcrypt模块)
  - [2.2. 查看apache2 配置文件](#22-查看apache2-配置文件)
- [3. 重启apache2](#3-重启apache2)
- [4. PS:](#4-ps)

<!-- /TOC -->

----

# 1. mcryp模块安装
```
sudo apt-get install php5-mcrypt
```

# 2. mcrypt模块加载

## 2.1. 开启mcrypt模块
```
sudo php5enmod mcrypt
```

## 2.2. 查看apache2 配置文件
*	进入目录："/etc/php5/apache2/conf.d/" 和 "/etc/php5/mods-available/" 检查是否有mcrypt.ini文件

# 3. 重启apache2
```
sudo service apache2 restart
```

------

# 4. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

* 参考资料:

	* 1、[缺少 mcrypt 扩展。请检查 PHP 配置。][2]

------


[1]:http://www.wmyeah.com
[2]:http://blog.csdn.net/wang1144/article/details/51505887?locationNum=12
