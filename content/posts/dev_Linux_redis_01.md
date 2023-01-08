---
title: CentOS7.X yum方式安装最新版本Redis
date: 2018-08-15
tags: [Linux]
categories: [Linux]
---


<font size=20>目录：</font>

<!-- TOC -->

- [1. 更新yum源](#1-更新yum源)
- [2. 安装redis-rpm源](#2-安装redis-rpm源)
- [3. 安装Redis](#3-安装redis)
- [4. 开机自启Redis](#4-开机自启redis)
- [5. 设置redis.conf](#5-设置redisconf)
- [6. PS:](#6-ps)

<!-- /TOC -->


# 1. 更新yum源
```
yum update
```


# 2. 安装redis-rpm源
```
yum install http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
```


# 3. 安装Redis
```
yum --enablerepo=remi install redis
```

# 4. 开机自启Redis
```
systemctl enable redis
```

# 5. 设置redis.conf
* bind 127.0.0.1  改为 bind 0.0.0.0(可选)
	```
	vim /etc/redis.conf
	```




# 6. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!
* 参考资料:

------

[1]:http://www.wmyeah.com
