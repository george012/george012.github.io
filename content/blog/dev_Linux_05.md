---
title: Ubuntu 14.0.4 mysql 存储目录迁移
date: 2016-01-06
tags: [Linux]
categories: [Linux]
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 说明:](#1-说明)
- [2. 停止mysql](#2-停止mysql)
- [3. 建立迁移目的地文件夹](#3-建立迁移目的地文件夹)
- [4. 修改所属用户及所属用户组为mysql](#4-修改所属用户及所属用户组为mysql)
- [5. 修改权限](#5-修改权限)
- [6. 拷贝"/var/lib/mysql/\*"所有文件](#6-拷贝varlibmysql所有文件)
- [7. 修改mysql的配置文件](#7-修改mysql的配置文件)
- [8. 修改shell文件](#8-修改shell文件)
- [9. 重新启动apparmor和mysql](#9-重新启动apparmor和mysql)
- [10. 删除原有文件 (-Option)](#10-删除原有文件--option)
- [11. PS:](#11-ps)

<!-- /TOC -->
----

----

# 1. 说明:
* parmars -mysqlDir- 新的mysql存储目录
	* 例如：/home/mysqlData/

* <font color=red>WARNING 注意代码中的引用到的参数</font>

----

# 2. 停止mysql
```
sudo service mysql stop
```

# 3. 建立迁移目的地文件夹
```
sudo mkdir -p -mysqlDir-
```

# 4. 修改所属用户及所属用户组为mysql
```
sudo chown -vR  mysql:mysql -mysqlDir-
```

# 5. 修改权限
```
sudo chmod -vR 700 -mysqlDir-
```

# 6. 拷贝"/var/lib/mysql/*"所有文件
```
sudo cp -av /var/lib/mysql/* -mysqlDir-
```

# 7. 修改mysql的配置文件
*	```
	sudo vi /etc/mysql/my.cnf
	```

*	将
	```
	datadir=/var/lib/mysql/
	```

*	修改为
	```
	datadir=-mysqlDir-
	```

# 8. 修改shell文件</h3>

*	```
	sudo vi /etc/apparmor.d/usr.sbin.mysqld
	```

*	将

	```
	/var/lib/mysql/ r,
    /var/lib/mysql/** rwk,
	```

*	修改为
	```
	-mysqlDir- r,
    -mysqlDir-** rwk,
	```

# 9. 重新启动apparmor和mysql
```
sudo service apparmor reload
sudo service mysql start
```


# 10. 删除原有文件 (-Option)
```
sudo rm -rvf /var/lib/mysql/
```

------

# 11. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

* 参考资料:

	* 1、[ubuntu14.04 下 mysql 存储目录迁移][2]
	* 2、[mysql数据库的使用与理解（基于ubuntu14.0.4LTS64位）][3]
	* 2、[ubuntu14.04下mysql数据库的默认存放路径并修改][4]

------


[1]:http://www.wmyeah.com
[2]:http://blog.csdn.net/wang794686714/article/details/39273385
[3]:http://www.2cto.com/database/201604/496988.html
[4]:http://blog.csdn.net/lyhvoyage/article/details/50521440
