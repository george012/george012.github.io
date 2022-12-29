---
title: Mac Pyhton3.7+Django2+Xadmin
date: 2018-11-15
type: post
tags: Linux
---

<font size=20>目录：</font>

<!-- TOC -->

- [1. 环境准备](#1-环境准备)
	- [1.1. Python](#11-python)
	- [1.2. Django2](#12-django2)
	- [1.3. Xadmin](#13-xadmin)
	- [1.4. 设置](#14-设置)
	- [1.5. 时区及本地显示](#15-时区及本地显示)
	- [1.6. 依赖文件处理](#16-依赖文件处理)
	- [1.7. 修改本版本Bug](#17-修改本版本bug)
- [2. 部署（CentOS7）](#2-部署centos7)
- [3. PS:](#3-ps)

<!-- /TOC -->

# 1. 环境准备
## 1.1. Python
*	此处使用Python3.7

## 1.2. Django2
*	本文使用Django2.1.3

## 1.3. Xadmin
*	Git远程源码安装（截止本文最新版本为2.0.1）
	```
	pip3 install git+git://github.com/sshwsfc/xadmin.git@django2
	```

*	卸载 xadmin并改用本地安装(主要是为了保留依赖环境)
	```
	pip3 uninstall xadmin
	```

*	将自行下载的Xadmin拖入新建工程根目录
*	新建apps（存放主App）
*	新建extra_apps目录（存放 第三方App）
*	将xamdin 目录从根目录下拖拽到extra_apps目录下（去掉下面的勾选）
*	选中《extra_apps》目录 → 右键 → Mark Directory as → Sources Root
*	注册 App 添加 xadmin、reversion
	```
	INSTALLED_APPS = [
	    'django.contrib.admin',
	    'django.contrib.auth',
	    'django.contrib.contenttypes',
	    'django.contrib.sessions',
	    'django.contrib.messages',
	    'django.contrib.staticfiles',
	    'xadmin',
	    'reversion'
	]
	```

*	说明
	```
	1、以下设置可直接运行Xadmin自身进行测试
	2、主要是尽量不动第三方App的情况下自主开发自有管理系统,所以只需要依赖环境
	3、保留xadmin本地文件主要是为了更正xadmin中的bug，并且可以和其他小伙伴一起享用同一套代码
	4、所以本人将不会 对‘Xadmin’进行注册，而是注册依赖于Xadmin的自建App
	```


## 1.4. 设置
*	使用PyCharm自带Terminal在工程根目录下进行操作
*	更新
	```
	./manage.py makemigrations
	```

*	同步库表结构
	```
	./manage.py migrate
	```

*	创建超级管理员
	```
	./manage.py createsuperuser
	```

## 1.5. 时区及本地显示
*	在settings.py中修改
	```
	LANGUAGE_CODE = 'zh-hans'
	TIME_ZONE = 'Asia/Shanghai'
	USE_I18N = True
	USE_L10N = True
	USE_TZ = False
	```

## 1.6. 依赖文件处理
```
# 依赖文件生成
pip freeze > requirements.txt
# 依赖文件安装
pip install -r requirement.txt
```

## 1.7. 修改本版本Bug
* ./xadmin/views/dashboard.py 第36行进行修改
	```
	* 将如下代码
	def render(self, name, value, attrs=None):
	* 修改为
	def render(self, name, value, attrs=None, renderer=None):
	```

# 2. 部署（CentOS7）
* 安装 virtualenv
	```
	pip3 install virtualenv
	```

* 建立软链接
	```
	ln -s /usr/local/python3/bin/virtualenv /usr/bin/virtualenv
	```

*	创建python_web虚拟环境
	```
	virtualenv --python=/usr/bin/python3 python_web
	```

* 进入{python_web/bin}目录，启动虚拟环境
	```
	source activate
	```

* 在虚拟环境中使用pip3安django和uwsgi
	```
	pip3 install django
	pip3 install uwsgi

	ln -s /usr/local/python3/bin/uwsgi /usr/bin/uwsgi		#建立uwsgi软链接以方便使用
	```

* 启动项目(进入项目目录中)
	```
	python3 manage.py runserver
	```

* 在项目根目录下配置UWSGI
	```
	<uwsgi>
	   <socket>127.0.0.1:8180</socket> <!-- 内部端口，自定义 -->
	   <chdir>/home/mysite/</chdir> <!-- 项目路径 -->
	   <module>mysite.wsgi</module>  <!-- mysite为wsgi.py所在目录名-->
	   <processes>1</processes> <!-- 进程数 -->
	   <daemonize>/home/logs/mysite.uwsgi.log</daemonize> <!-- 日志文件 -->
	</uwsgi>
	```

*	生成requirements.txt文件
	```
	pip freeze > requirements.txt
	```

*	安装requirements.txt依赖
	```
	pip install -r requirements.txt
	```

------
# 3. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

------

[1]:http://www.wmyeah.com
[2]:http://blog.51cto.com/kusorz/1920778
