---
title: CentOS8.X 安装Python3.8.x
date: 2020-04-02
type: post
tags: Linux
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 安装依赖](#1-安装依赖)
- [2. 安装Python3.8.2](#2-安装python382)
  - [2.1. 安装并配置python](#21-安装并配置python)
  - [2.2. 更换pip源加速pip下载速度（此处使用阿里云）](#22-更换pip源加速pip下载速度此处使用阿里云)
  - [2.3. 更新pip](#23-更新pip)
- [3. 番外 virtualenv 和 virtualenvwrapper 的安装](#3-番外-virtualenv-和-virtualenvwrapper-的安装)
  - [3.1. virtualenv](#31-virtualenv)
  - [3.2. virtualenvwrapper](#32-virtualenvwrapper)
- [4. PS:](#4-ps)

<!-- /TOC -->

----
# 1. 安装依赖
* 注意一定要先安装依赖包，依赖包顺序如下（亲测、、、顺序搞错导 会导致 pip某些包无法安装）
  ```
  yum install wget
  yum install setup 
  yum install perl
  yum install openssl-devel
  yum install zlib-devel
  yum groupinstall "Development tools"
  yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel
  yum install gdbm-devel db4-devel libpcap-devel xz-devel
  yum install zlib1g-dev
  yum install zlib*
  yum install libffi-devel

  yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel

  ```

# 2. 安装Python3.8.2
## 2.1. 安装并配置python
  ```
  wget https://www.python.org/ftp/python/3.8.2/Python-3.8.2.tar.xz
  tar -xvJf Python-3.8.2.tar.xz
  mkdir /usr/local/python3 
  cd Python-3.8.2
  ./configure --prefix=/usr/local/python3 --enable-optimizations --with-ssl 
  make && make install
  ln -s /usr/local/python3/bin/python3 /usr/bin/python3
  ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
  ln -s /usr/bin/python3 /usr/bin/python
  ln -s /usr/bin/pip3 /usr/bin/pip
  ```

## 2.2. 更换pip源加速pip下载速度（此处使用阿里云）
* 编辑命令
  ```
  mkdir -p ~/.pip
  
  vim  ~/.pip/pip.conf
  ```

* 文件内容
  ```
  [global]
  index-url = http://mirrors.aliyun.com/pypi/simple 

  [install]
  trusted-host=mirrors.aliyun.com
  ```

## 2.3. 更新pip
```
pip3 install --upgrade pip
```

# 3. 番外 virtualenv 和 virtualenvwrapper 的安装
## 3.1. virtualenv
```
pip install virtualenv
```

## 3.2. virtualenvwrapper
```
pip install virtualenvwrapper
```

------

# 4. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!
* 参考资料[Centos8（最小化安装）全新安装Python3.8+pip的方法教程][2]
------

[1]:http://www.wmyeah.com
[2]:https://www.jb51.net/article/179464.htm