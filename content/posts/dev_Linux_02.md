---
title: Ubuntu 14.0.4搭建LAMP+phpmyadmin Web服务器
date: 2015-04-08
tags: [Linux]
categories: [Linux]
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 安装mysql-server、mysql-client](#1-安装mysql-servermysql-client)
- [2. 安装apache2](#2-安装apache2)
- [3. 安装php5 php5 libapache2-mod-php5(apache php5支持模块)](#3-安装php5-php5-libapache2-mod-php5apache-php5支持模块)
- [4. 安装php5常用模块](#4-安装php5常用模块)
- [5. 安装数据库管理工具 phpMyadmin](#5-安装数据库管理工具-phpmyadmin)
- [6. 重启apache2](#6-重启apache2)
- [7. 访问站点:](#7-访问站点)
- [8. PS:](#8-ps)

<!-- /TOC -->

----

# 1. 安装mysql-server、mysql-client
```
sudo apt-get install mysql-server mysql-client
```

# 2. 安装apache2
```
sudo apt-get install apache2
```

# 3. 安装php5 php5 libapache2-mod-php5(apache php5支持模块)
```
sudo apt-get install php5 libapache2-mod-php5
```

# 4. 安装php5常用模块
```
sudo apt-get  install php5-mysql php5-curl php5-gd php5-intl php-pear php5-imagick  php5-imap php5-mcrypt php5-memcache php5-ming php5-ps php5-pspell  php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl```
```

# 5. 安装数据库管理工具 phpMyadmin
```
sudo apt-get install phpmyadmin
```

# 6. 重启apache2
```
sudo service apache2 restart
```

# 7. 访问站点:

* LocalHost模式:	再浏览器中输入“http://127.0.0.1” 或 “http://localhost” 访问

* 远程模式: 再浏览器中输入“http://domain”访问 (ps:domain 为 服务器IP地址或者已指向服务器的域名)

------

# 8. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有! 

* 参考资料:

	* 1、[Linux Ubuntu 14.04安装LAMP（Apache+MySQL+PHP）网站环境][2]
	* 2、[Ubuntu Server 14.04 安装 LAMP][3]
	* 2、[ubuntu14.04搭建web服务器lamp][4]

------

[1]:http://www.wmyeah.com
[2]:http://www.jianshu.com/p/135697b3ff0d
[3]:http://www.linuxidc.com/Linux/2015-03/115136.htm
[4]:http://jingyan.baidu.com/article/ceb9fb10d572d88cad2ba093.html
