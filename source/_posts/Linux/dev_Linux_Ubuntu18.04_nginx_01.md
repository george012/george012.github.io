---
title: Ubuntu 18.04 安装最新版本 Nginx
date: 2018-08-15
type: post
tags: Linux
---

<!-- TOC -->

- [1. 编辑源](#1-编辑源)
- [2. 源内容](#2-源内容)
- [3. 添加nginx 公钥](#3-添加nginx-公钥)
- [4. 更新并安装](#4-更新并安装)
- [5. PS:](#5-ps)

<!-- /TOC -->

----




# 1. 编辑源
````
vim  /etc/apt/sources.list.d/nginx.list
````

# 2. 源内容
```
deb [arch=amd64] http://nginx.org/packages/mainline/ubuntu/ bionic nginx
deb-src http://nginx.org/packages/mainline/ubuntu/ bionic nginx
```

# 3. 添加nginx 公钥
*	下载nginx 公钥
```
wget http://nginx.org/keys/nginx_signing.key
```

*	添加
```
apt-key add nginx_signing.key
```

# 4. 更新并安装
```
apt update
apt install nginx
```

----
# 5. PS:
* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

------

[1]:http://www.wmyeah.com