---
title: Redis
date: 2023-04-02
tags: [Redis]
categories: [Redis]
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 在`Ubuntu 20.04 LTS`安装最新版本`Redis`](#1-在ubuntu-2004-lts安装最新版本redis)
- [2. PS:](#2-ps)

<!-- /TOC -->

# 1. 在`Ubuntu 20.04 LTS`安装最新版本`Redis`
* 添加redis源
```
add-apt-repository ppa:redislabs/redis

apt update && apt install redis

systemctl enable redis-server.service

```


# 2. PS:
* 此操作基于（root）权限操作，如用普通用户可在命令行前加“sudo”
* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!
------

[1]:http://www.wmyeah.com




