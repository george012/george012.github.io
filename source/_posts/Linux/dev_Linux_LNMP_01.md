---
title: CentOS7.X 搭建LNMP平台(Yum方式)
date: 2017-08-21
type: post
tags: Linux
---

<font size=20>目录：</font>

<!-- TOC -->

- [1. 说明：](#1-说明)
- [2. 安装php、php-fpm](#2-安装phpphp-fpm)
- [3. Nginx](#3-nginx)
- [4. Mysql](#4-mysql)
- [5. PS:](#5-ps)

<!-- /TOC -->
----  

# 1. 说明：
<font color=red>基于 Centos7.3 php5.6 mysql5.6 nginx1.12.1</font>

# 2. 安装php、php-fpm
```
# 更新yum
yum install epel-release
rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm


# 1、安装php

yum install --enablerepo=remi --enablerepo=remi-php56 php php-opcache php-devel php-mbstring php-mcrypt php-mysqlnd php-phpunit-PHPUnit php-pecl-xdebug php-gd php-pecl-xhprof


# Centos8
yum install http://rpms.remirepo.net/enterprise/remi-release-8.rpm

yum install --enablerepo=remi --enablerepo=remi-safe php56 php56-php-opcache php-devel php56-php-mbstring php56-php-mcrypt php56-php-mysqlnd php-phpunit-PHPUnit php56-php-pecl-xdebug php56-php-pecl-xhprof


apt install php5.6 php5.6-mcrypt php5.6-mbstring php5.6-curl php5.6-cli php5.6-mysql php5.6-gd php5.6-xml php5.6-fpm
# 2、安装 php-fpm
yum install --enablerepo=remi --enablerepo=remi-php56 php-fpm
or
【yum install php-fpm】
# 3、启动 php-fpm
systemctl start php-fpm
# 4、开机自启 php-fpm
systemctl enable php-fpm

```

# 3. Nginx
```
# 1、更新Yum源
yum update

# 2、获取最新的Nginx RPM包
rpm -Uvh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm

# 3、安装Nginx
yum install nginx

# 4、设置开机自启
systemctl enable nginx

```

# 4. Mysql

```
# 1、编辑yum源
vim /etc/yum.repos.d/mysql-community.repo
[mysql56-community]
name=MySQL 5.6 Community Server
baseurl=http://repo.mysql.com/yum/mysql-5.6-community/el/7/$basearch/
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql

# 2、安装
yum install mysql-community-server mysql-community-devel mysql-community-client


# 3、开机自启
systemctl enable mysqld

```
------

# 5. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

------

[1]:http://www.wmyeah.com
