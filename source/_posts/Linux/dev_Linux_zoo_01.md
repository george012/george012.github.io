---
title: CentOS7.4 zookeeper单机模式安装，并设置开机自启
date: 2018-08-13
type: post
tags: Linux
---


<font size=20>目录：</font>

<!-- TOC -->

- [1. 更新Yum源](#1-更新yum源)
- [2. 获取最新的zookeeper Tar包](#2-获取最新的zookeeper-tar包)
- [3. 安装JDK（官网下载 此处选择的是 rpm包安装）](#3-安装jdk官网下载-此处选择的是-rpm包安装)
- [4. 设置开机自启](#4-设置开机自启)
- [5. PS:](#5-ps)

<!-- /TOC -->

----


# 1. 更新Yum源
````
yum update
````

# 2. 获取最新的zookeeper Tar包
```
wget http://mirrors.hust.edu.cn/apache/zookeeper/zookeeper-3.4.13/zookeeper-3.4.13.tar.gz

# 解压
tar -zxvf zookeeper-3.4.13.tar.gz 

```

# 3. 安装JDK（官网下载 此处选择的是 rpm包安装）
* rpm包主要是为了自动配置环境变量
```
rpm -ivh jdk-8u181-linux-x64.rpm 
```

# 4. 设置开机自启
* 遵循系统的权限管理模式 所以 参照 系统ngix.server 服务编写
```
vim /usr/lib/systemd/system/zookeeper.service
```

* 内容
```
[Unit]
Description=zookeeper
After=syslog.target network.target

[Service]
Type=forking
Environment=ZOO_LOG_DIR=/home/zookeeper/log      //这里必须填写绝对路径
ExecStart=/zookeeper安装目录/bin/zkServer.sh start
ExecStop=/zookeeper安装目录/zoo/bin/zkServer.sh stop
Restart=always

[Install]
WantedBy=multi-user.target
```

* 软连接
```
ln -s /usr/lib/systemd/system/zookeeper.service /etc/systemd/system/zookeeper.service

```

# 5. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!
* 参考资料:
	* 1、[Centos7以普通用户启动zookeeper并加入开机自启动服务][2]

------

[1]:http://www.wmyeah.com
[2]:http://blog.51cto.com/kusorz/1920778
