---
title: CentOS7.X 新装后个性化处理
date: 2017-08-01
type: post
tags: Linux
---

<font size=20>目录：</font>

<!-- TOC depthFrom:1 depthTo:6 orderedList:true updateOnSave:true withLinks:true -->

- [1. 修改HostName](#1-修改hostname)
- [2. Shell脚本中文乱码问题解决](#2-shell脚本中文乱码问题解决)
- [3. 部分常用开发工具安装](#3-部分常用开发工具安装)
- [4. 关闭防火墙](#4-关闭防火墙)
- [5. 关闭SELinux](#5-关闭selinux)
- [6. 更换yum源及安装EPEL源](#6-更换yum源及安装epel源)
- [7. PS:](#7-ps)

<!-- /TOC -->

----
# 1. 修改HostName

```
#	设置自定义HostName
hostnamectl set-hostname MyHostName
#	查看一下是否生效
hostnamectl status
```

# 2. Shell脚本中文乱码问题解决

```
vim /etc/locale.conf
##	将默认语言改为中文UTF-8
LANG=zh_CN.UTF-8
```

# 3. 部分常用开发工具安装

```
yum -y install nano vim wget curl net-tools lsof unzip unzip
```


# 4. 关闭防火墙

```
systemctl stop firewalld

systemctl disable firewalld
```

# 5. 关闭SELinux
```
sed -i 's#SELINUX=enforcing#SELINUX=disabled#g' /etc/selinux/config
#   查看
grep 'SELINUX=disabled' /etc/selinux/config
```

# 6. 更换yum源及安装EPEL源
```
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup

wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo
或者
curl -o /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo

# 安装EPEL源
yum install -y epel-release
 
# 执行清理
yum clean all
 
# 重建缓存
yum makecache
```

------

# 7. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

------

[1]:http://www.wmyeah.com
