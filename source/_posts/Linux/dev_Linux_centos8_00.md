---
title: CentOS8.X 安装后调优
date: 2020-04-04
type: post
tags: Linux
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 部分常用开发工具安装](#1-部分常用开发工具安装)
- [2. 安装epel源](#2-安装epel源)
- [3. 更换yum源为阿里云yum源（国内提速）](#3-更换yum源为阿里云yum源国内提速)
- [4. 关闭防火墙](#4-关闭防火墙)
- [5. 关闭selinux](#5-关闭selinux)
- [6. 重启系统 使其生效](#6-重启系统-使其生效)
- [7. PS:](#7-ps)

<!-- /TOC -->

----
# 1. 部分常用开发工具安装
```
yum -y install nano vim wget curl net-tools lsof unzip unzip
```

# 2. 安装epel源
```
yum install epel-release
```

# 3. 更换yum源为阿里云yum源（国内提速）
* 备份yum源
  ```
  mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak
  ```
  
* 下载阿里云yum 源
  ```
  wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-8.repo
  ```

* 确保/etc/yum.repos.d/CentOS-Media.repo 文件中 <font color=red>enabled=0</font>
  ```
  vim /etc/yum.repos.d/CentOS-Media.repo
  ```

* 一步到位更新
  ```
  yum clean all && yum makecache && yum update
  ```

# 4. 关闭防火墙
* 查看
  ```
  systemctl status firewalld
  ```

* 关闭
  ```
  systemctl stop firewalld
  ```

* 关闭开机自启
  ```
  systemctl disable firewalld
  ```

# 5. 关闭selinux
* 查看
  ```
  getenforce
  ```

* 永久关闭
  ```
  vim /etc/selinux/config

  将
  SELINUX=enforcing
  改成
  SELINUX=disabled
  ```

# 6. 重启系统 使其生效
```
reboot
```

# 7. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!
* 参考资料[Centos8（最小化安装）全新安装Python3.8+pip的方法教程][2]
------

[1]:http://www.wmyeah.com
[2]:https://www.jb51.net/article/179464.htm