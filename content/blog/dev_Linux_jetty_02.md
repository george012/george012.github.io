---
title: Jetty9.2 阿里云SSL配置
date: 2017-08-10
tags: [Linux]
categories: [Linux]
---

<font size=20>目录：</font>

<!-- TOC -->

- [1. 申请阿里云免费SSL证书](#1-申请阿里云免费ssl证书)
- [2. 转换证书](#2-转换证书)
- [3. 编辑“jetty-ssl.xml”文件](#3-编辑jetty-sslxml文件)
- [4. 配置"jetty-https.xml "](#4-配置jetty-httpsxml-)
- [5. 配置Jetty启动文件](#5-配置jetty启动文件)
- [6. PS:](#6-ps)

<!-- /TOC -->


# 1. 申请阿里云免费SSL证书
*	阿里云	→	控制台	→	安全（云盾）→	证书服务	→	购买证书
*	根据如下路径申请免费证书（购买详细步骤阿里云操作提示中很详细）

# 2. 转换证书
* xxxx.pfx  : 阿里云提供的SSL PFX格式文件
* your-name.jks ：新文件及命名格式（可根据项目需求自行变换）
*	转换命令
	```
	keytool -importkeystore -srckeystore xxxx.pfx -destkeystore your-name.jks -srcstoretype PKCS12 -deststoretype JKS
	```


# 3. 编辑“jetty-ssl.xml”文件
*	以下下操作均在“$JETTY_HOME”目录下操作

*	```
	vim etc/jetty-ssl.xml
	```

*	如下配置
	*	etc/your-name.jks	:	相对于Jetty根目录的jks证书位置
	*	your-jks-password	:	证书密码
	```
	<Set name="KeyStorePath"><Property name="jetty.base" default="." />/<Property name="jetty.keystore" default="etc/your-name.jks"/></Set>
	<Set name="KeyStorePassword"><Property name="jetty.keystore.password" default="your-jks-password"/></Set>
	<Set name="KeyManagerPassword"><Property name="jetty.keymanager.password" default="your-jks-password"/></Set>
	<Set name="TrustStorePath"><Property name="jetty.base" default="." />/<Property name="jetty.truststore" default="etc/your-name.jks"/></Set>
	<Set name="TrustStorePassword"><Property name="jetty.truststore.password" default="your-jks-password"/></Set>
	```

# 4. 配置"jetty-https.xml "
*	进入编辑
	```
	vim etc/jetty-https.xml
	```

*	检查配置
	*	8443	：此处以8443位示例端口
	```
	<Set name="host"><Property name="jetty.host" /></Set>
	<Set name="port"><Property name="https.port" default="8443" /></Set>
	<Set name="idleTimeout"><Property name="https.timeout" default="30000"/></Set>
	<Set name="soLingerTime"><Property name="https.soLingerTime" default="-1"/></Set>
	<Set name="acceptorPriorityDelta"><Property name="ssl.acceptorPriorityDelta" default="0"/></Set>
	<Set name="selectorPriorityDelta"><Property name="ssl.selectorPriorityDelta" default="0"/></Set>
	<Set name="acceptQueueSize"><Property name="https.acceptQueueSize" default="0"/></Set>
	```

# 5. 配置Jetty启动文件
*	编辑“start.ini”
	```
	vim start.ini
	```
*	文件中添加如下代码(<font color = red>尽量在端口配置行上面添加</font>)
	```
	etc/jetty-ssl.xml
	etc/jetty-https.xml
	```

# 6. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!
* 参考资料:
	1、[Jetty:9.2官方文档：Jetty : The Definitive Reference][2]
	2、[Jetty9.2官方SSL配置文档][3]
------

[1]:http://www.wmyeah.com
[2]:https://www.eclipse.org/jetty/documentation/9.2.22.v20170531/
[3]:https://www.eclipse.org/jetty/documentation/9.2.22.v20170531/configuring-ssl.html
