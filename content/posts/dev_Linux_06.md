---
title: Ubuntu 14.0.4 Linux SVN Server搭建
date: 2015-02-01
tags: [Linux]
categories: [Linux]
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 说明:](#1-说明)
- [2. 安装subversion](#2-安装subversion)
- [3. 创建版本库](#3-创建版本库)
- [4. 配置"svnserve.conf"版本库信息](#4-配置svnserveconf版本库信息)
- [5. 配置"passwd"用户信息](#5-配置passwd用户信息)
- [6. 配置"authz"用户授权](#6-配置authz用户授权)
- [7. 设置开机自启动SVN服务](#7-设置开机自启动svn服务)
- [8. PS:](#8-ps)

<!-- /TOC -->

----

# 1. 说明:

* parmars -svnDir- SVN项目统一存放路径
	* 例如：/home/svnProjects/

* parmars -svnDir_Project01- 暂命名为“Project01”的SVN库地址
	* 例如：/home/svnProjects/svnP1/

* <font color=red>WARNING 注意代码中的引用到的参数</font>

----

# 2. 安装subversion
```
sudo apt-get install subversion
```

# 3. 创建版本库
*	```
	sudo mkdir -p -svnDir_Project01-
	```

*	```
	sudo svnadmin create -svnDir_Project01-
	```

# 4. 配置"svnserve.conf"版本库信息
*	```
	sudo vi -svnDir_Project01-/conf/svnserve.conf
	```

*	将以下参数注释掉
	```
	[general]
	anon-access = none #匿名访问权限，默认read，none为不允许访问
	auth-access = write #认证用户权限
	password-db = passwd #用户信息，默认在版本库/conf下面,如需更改请填写文件绝对路径
	authz-db = authz
	```

# 5. 配置"passwd"用户信息
*	```
	sudo vi -svnDir_Project01-/conf/passwd
	```

*	按如下格式添加用户
	```
	[users]
	zhangsan 	= 123
	lisi 		= 123
	wangwu 		= 123
	```

# 6. 配置"authz"用户授权
*	```
	sudo vi -svnDir_Project01-/conf/authz
	```

*	按如下格式修改或添加用户授权信息
	```
	[groups] 				#定义组的用户
	manager = zhangsan
	core_dev = lisi,wangwu

	#以此版本库根目录为基准下发权限物理位置为"-svnDir_Project01-"
	[/] 					#manager组用户对根目录有读写权限
	@manager = rw

	[/dev] 					#core_dev对dev子目录为读写权限
	@core_dev = rw
	```


# 7. 设置开机自启动SVN服务

*	进入"/etc/init.d/"目录
	```
	cd /etc/init.d/
	```

*	```
	sudo vi runSVN .sh
	```

	*	输入如下内容  此处为存放所有SVN版本库的目录的绝对地址
		```
		#!/bin/bash
		svnserve -d -r -svnDir-
		```

	*	保存退出并修改权限
		```
		sudo chmod 777 runSVN.sh
		```

		```
		sudo update-rc.d runSVN.sh defaults
		```

------

# 8. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

* 参考资料:

	* 1、[High-Speed Tutorial Appendix A. Subversion Quick-Start Guide][2]
	* 2、[ubuntu 14.04 下搭建SVN服务器 svn://][3]
	* 2、[Ubuntu 14.0.4系统下SVN的安装与配置][4]

------

[1]:http://www.wmyeah.com
[2]:http://svnbook.red-bean.com/nightly/en/svn.intro.quickstart.html
[3]:http://www.cnblogs.com/bcsflilong/p/4231252.html
[4]:http://www.codesec.net/view/146860.html
