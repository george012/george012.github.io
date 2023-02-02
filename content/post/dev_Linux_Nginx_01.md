---
title: CentOS7.3Yum方式安装Nginx
date: 2017-08-15
tags: [Linux]
categories: [Linux]
---

<font size=20>目录：</font>

<!-- TOC -->

- [1. 更新Yum源](#1-更新yum源)
- [2. 获取最新的Nginx RPM包](#2-获取最新的nginx-rpm包)
- [3. 安装Nginx](#3-安装nginx)
- [4. 设置开机自启](#4-设置开机自启)
- [5. PS:](#5-ps)

<!-- /TOC -->

----


# 1. 更新Yum源
````
yum update
````

# 2. 获取最新的Nginx RPM包
```
rpm -Uvh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
```

# 3. 安装Nginx
```
yum install nginx
```

# 4. 设置开机自启
```
systemctl enable nginx
```

# 5. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!
* 参考资料:
	* 1、[nginx: Linux packages][2]

------

[1]:http://www.wmyeah.com
[2]:http://nginx.org/en/linux_packages.html
