---
title: R730xd Ubuntu server 20.04 安装并调优
date: 2020-04-02
tags: [Linux]
categories: [Linux]
---

<font size=20>目录：</font>

<!-- TOC -->

- [1. 修改apt源为阿里云](#1-修改apt源为阿里云)
  - [1.1. 备份系统自带源](#11-备份系统自带源)
  - [1.2. 修改源为阿里云](#12-修改源为阿里云)
  - [1.3. 更新apt](#13-更新apt)
  - [1.4. 关闭SNAP自动更新](#14-关闭snap自动更新)
- [2. PS:](#2-ps)

<!-- /TOC -->

# 1. 修改apt源为阿里云
## 1.1. 备份系统自带源
```
mv /etc/apt/sources.list /etc/apt/sources.list.bak
```

## 1.2. 修改源为阿里云
* 编辑apt源文件
  ```
  vim /etc/apt/sources.list
  ```

* apt源文件 /etc/apt/sources.list 内容
```
deb http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
```

## 1.3. 更新apt
```
apt update

apt upgrade
```

## 1.4. 关闭SNAP自动更新
```
systemctl disable {snapd,snapd.socket,snapd.refresh.timer}
systemctl stop {snapd,snapd.socket,snapd.refresh.timer}

vim /etc/apt/apt.conf.d/20auto-upgrades
# 将1 改为0 
```

------

# 2. PS:
* 此操作基于（root）权限操作，如用普通用户可在命令行前加“sudo”
* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!
------

[1]:http://www.wmyeah.com
