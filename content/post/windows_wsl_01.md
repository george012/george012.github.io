---
title: Ubuntu Server 18.0.4.4 KVM 虚拟化搭建
date: 2022-04-02
tags: [Windows,WSL]
categories: [Windows,WSL]
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 开启`systemctl`服务](#1-开启systemctl服务)
- [2. PS:](#2-ps)

<!-- /TOC -->

# 1. 开启`systemctl`服务
* 在升级为wsl2最新版后执行
    ```
    echo -e "[boot]\nsystemd=true" | sudo tee -a /etc/wsl.conf
    ```
* 安装完后再`PowerShell`中重启WSL2
    ```
    # 重启
    wsl --shutdown
    ```

* 在`WSL Linux系统`中执行下面命令，查看`systemctl`是否启动
```
ps --no-headers -o comm 1
```


# 2. PS:
* 此操作基于（root）权限操作，如用普通用户可在命令行前加“sudo”
* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!
------

[1]:http://www.wmyeah.com




