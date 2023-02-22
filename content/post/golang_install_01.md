---
title: Golang--安装篇
date: 2023-02-01
tags: [Golang]
categories: [Golang]
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 在`Windows`安装](#1-在windows安装)
  - [1.1. 在`Windows`下`WSL2 Ubuntu20.0.4`](#11-在windows下wsl2-ubuntu2004)
- [2. 在`Linux`安装](#2-在linux安装)
  - [2.1. 在`Ubuntu`中](#21-在ubuntu中)
- [3. PS:](#3-ps)

<!-- /TOC -->

# 1. 在`Windows`安装
```
```

## 1.1. 在`Windows`下`WSL2 Ubuntu20.0.4`
* 同`Linux Ubuntu`安装方式----

# 2. 在`Linux`安装

## 2.1. 在`Ubuntu`中
    ```
sudo add-apt-repository ppa:longsleep/golang-backports 
sudo apt-get install golang-go
```

*   如果要安装指定版本
    ```
    sudo apt-get install golang-1.17-go
    ```

*   如果add-apt-repository不存在，通过以下命令安装进行按照：
    ```
    sudo apt-get install software-properties-common
    sudo apt-get update
    ```

# 3. PS:
* 此操作基于（root）权限操作，如用普通用户可在命令行前加“sudo”
* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!
------

[1]:http://www.wmyeah.com




