---
title: 在Ubuntu 14.0.4 LTS Apache virtualhost 虚拟主机相关设置(包含https)
date: 2015-04-18
tags: [Linux]
categories: [Linux]
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 说明：](#1-说明)
- [2. 创建存放所有Web项目的相关目录](#2-创建存放所有web项目的相关目录)
	- [2.1. web 根目录](#21-web-根目录)
	- [2.2. 项目A 根目录](#22-项目a-根目录)
	- [2.3. 项目B 根目录](#23-项目b-根目录)
	- [2.4. 赋予相关目录权限](#24-赋予相关目录权限)
- [3. apache2.conf 相关设置](#3-apache2conf-相关设置)
	- [3.1. 备份原有配置文件](#31-备份原有配置文件)
	- [3.2. 编辑 apache2.conf](#32-编辑-apache2conf)
- [4. 设置 apache 虚拟主机](#4-设置-apache-虚拟主机)
	- [4.1. 编辑 -Domain\_A-.conf 文件](#41-编辑--domain_a-conf-文件)
		- [4.1.1. 拷贝样例](#411-拷贝样例)
		- [4.1.2. 编辑](#412-编辑)
			- [4.1.2.1. 根据需求设置](#4121-根据需求设置)
			- [4.1.2.2. 设置https支持 (-Option)](#4122-设置https支持--option)
	- [4.2. 编辑-Domain\_B-.conf文件](#42-编辑-domain_b-conf文件)
- [5. 启用配置](#5-启用配置)
	- [5.1. 进入 “/etc/apache2/sites-available” 目录](#51-进入-etcapache2sites-available-目录)
	- [5.2. 禁用系统默认解析文件 “000-default.conf”](#52-禁用系统默认解析文件-000-defaultconf)
	- [5.3. 启用配置好的文件 “-Domain\_A-.conf”](#53-启用配置好的文件--domain_a-conf)
- [6. 开启apache ssl支持 (-Option)](#6-开启apache-ssl支持--option)
- [7. 重启Apache2服务](#7-重启apache2服务)
- [8. 访问站点:](#8-访问站点)
- [9. PS:](#9-ps)

<!-- /TOC -->

----

# 1. 说明：
* parmars -webDir- 存放所有Web项目的Linux文件系统绝对目录 
	* 例如：/home/webSite
* parmars -webSubDir_A- web项目A根目录	
	* 例如：/home/webSite/webA

* parmars -webSubDir_B- web项目A根目录	
	* 例如：/home/webSite/webB

* parmars [-Domain_A-] webA域名	
	* 例如：a.wmyeah.com

* parmars [-Domain_B-] webB域名	
	* 例如：b.wmyeah.com

* parmars -SSL_File_Path- SSL文件存放位置 (-Option)
	* 例如：/home/SSLFiles

----

# 2. 创建存放所有Web项目的相关目录
## 2.1. web 根目录
```
sudo mkdir -p  -webDir-
```
## 2.2. 项目A 根目录
```
sudo mkdir -p  -webSubDir_A-
```
## 2.3. 项目B 根目录
```
sudo mkdir -p  -webSubDir_B-
```
## 2.4. 赋予相关目录权限
```
sudo chown -R $USER:$USER -webDir-
sudo chown -R $USER:$USER -webDir_A-
sudo chown -R $USER:$USER -webDir_B-
```
-----

# 3. apache2.conf 相关设置

## 3.1. 备份原有配置文件
	```cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf.bak```

## 3.2. 编辑 apache2.conf
	```sudo vi /etc/apache2/apache2.conf```
	* 将
	```
	<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
	</Directory>
	```
	* 改为
	```
	<Directory /zx_dev/webSite/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
	</Directory>
	```
* 保存退出
----

# 4. 设置 apache 虚拟主机

## 4.1. 编辑 -Domain_A-.conf 文件
### 4.1.1. 拷贝样例
```
sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/-Domain_A-.conf
```

### 4.1.2. 编辑
```
sudo vi /etc/apache2/sites-available/-Domain_A-.conf
```

#### 4.1.2.1. 根据需求设置
```
<VirtualHost *:80> 		 			// 端口
ServerName -Domain_A-				// 域名
ServerAdmin webmaster@-Domain_A-    // 管理员邮箱
DocumentRoot -webDir_A-				// 项目根目录
```

#### 4.1.2.2. 设置https支持 (-Option)
* 在“ <VirtualHost *:80 ”上方添加 “Listen 443”
	```
	Listen 443
	<VirtualHost *:80>
	```
* 开启SSL并添加Key文件
	```
	SSLEngine on
	SSLCertificateFile      -SSL_File_Path-/-Domain_A-.crt
	SSLCertificateKeyFile   -SSL_File_Path-/-Domain_A-.key
	SSLCACertificateFile    -SSL_File_Path-/-Domain_A-_Bundle.crt
	```

## 4.2. 编辑-Domain_B-.conf文件
* [请参照4.1](#41-编辑--domain_a-conf-文件)

# 5. 启用配置
## 5.1. 进入 “/etc/apache2/sites-available” 目录
*	```
	cd /etc/apache2/sites-available/
	```

## 5.2. 禁用系统默认解析文件 “000-default.conf”
*	```
	sudo a2dissite 000-default.conf
	```

## 5.3. 启用配置好的文件 “-Domain_A-.conf”
*	```
	sudo a2ensite -Domain_A-.conf
	```

# 6. 开启apache ssl支持 (-Option)
*	```
	sudo a2enmod ssl
	```

# 7. 重启Apache2服务
*	```
	sudo service apache2 restart
	```

# 8. 访问站点:
* 在浏览器中输入“https://domain”访问 (ps:domain 为 服务器IP地址或者已指向服务器的域名)

------

# 9. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

* 参考资料:

	* 1、[LAMP（Apache）环境部署安装SSL安全证书且可HTTPS加密网站][2]
	* 2、[linux下的apache部署ssl证书][3]
	* 2、[如何在Ubuntu 14.04 上为Apache 2.4 安装SSL支持][4]

------


[1]:http://www.wmyeah.com
[2]:https://bbs.wosign.com/forum.php?mod=viewthread&tid=2930&highlight=apache
[3]:https://bbs.wosign.com/forum.php?mod=viewthread&tid=1018&highlight=apache
[4]:http://www.linuxidc.com/Linux/2015-02/113588.htm
