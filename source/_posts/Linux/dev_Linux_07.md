---
title: Ubuntu 14.0.4 安装并配置Gitolite服务器
date: 2015-06-09
type: post
tags: Linux
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 说明](#1-说明)
- [2. 添加用户并配置git用户HOME目录](#2-添加用户并配置git用户home目录)
- [3. 将用户添加到SSH服务组](#3-将用户添加到ssh服务组)
- [4. 设置Git密码](#4-设置git密码)
- [5. 配置GitGlobal](#5-配置gitglobal)
- [6. 生成SSHKey](#6-生成sshkey)
- [7. 拷贝并重命名 .Pub 公钥](#7-拷贝并重命名-pub-公钥)
- [8. clone Git源码库](#8-clone-git源码库)
- [9. 新建"$HOME/bin"文件夹](#9-新建homebin文件夹)
- [10. 将git安装到"$HOME/bin"目录](#10-将git安装到homebin目录)
- [11. 初始化gitolite程序](#11-初始化gitolite程序)
- [12. clone gitolite管理库"gitolite-admin.git"](#12-clone-gitolite管理库gitolite-admingit)
- [13. PS:](#13-ps)

<!-- /TOC -->

----

# 1. 说明

* parmars -gitHomeDir-   git用户HOME目录
	* 例如：/home/git/

* parmars -USERNAME-   			//用户名  	

* parmars -git_User_Name-      	//用户名

* parmars -git_User_Email-     	//Email


* <font color=red>WARNING 注意代码中的引用到的参数</font>

----

# 2. 添加用户并配置git用户HOME目录
```
sudo adduser --system --shell /bin/bash --home -gitHomeDir- --group git
sudo adduser --system --shell /bin/bash --home /datas/git- --group git
```

# 3. 将用户添加到SSH服务组</h3>
```
sudo adduser git ssh
```

# 4. 设置Git密码
```
sudo passwd git
```

# 5. 配置GitGlobal
```
git config --global user.name "-git_User_Name-"
git config --global user.email "Email"
```

# 6. 生成SSHKey
```
ssh-keygen -t rsa -C "-git_User_Email-"
```

*	连按3此回车结束(-Option 也可以根据需求设置详细密码)

# 7. 拷贝并重命名 .Pub 公钥
```
cp .ssh/id_rsa.pub ./-USERNAME-.pub
```

# 8. clone Git源码库
```
git clone git://github.com/sitaramc/gitolite
```

# 9. 新建"$HOME/bin"文件夹
```
mkdir -p $HOME/bin
```

# 10. 将git安装到"$HOME/bin"目录
```
gitolite/install -to $HOME/bin
```

# 11. 初始化gitolite程序
```
$HOME/bin/gitolite setup -pk YourName.pub
```

# 12. clone gitolite管理库"gitolite-admin.git"
```
git clone git@127.0.0.1:gitolite-admin.git
```

------

# 13. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

* 参考资料:

	* 1、[gitolite README.markdown][2]
	* 2、[gitolite wiki][3]
	* 2、[Ubuntu下安装Git和Gitolite][4]

------

[1]:http://www.wmyeah.com
[2]:https://github.com/sitaramc/gitolite
[3]:https://github.com/sitaramc/gitolite/wiki
[4]:http://www.2cto.com/os/201205/132121.html
