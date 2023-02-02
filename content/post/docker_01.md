---
title: Centos7.x安装最新版Docker
date: 2022-11-25
tags: [Docker]
categories: [Docker]
---

<!-- TOC -->

- [卸载旧版 `Docker`](#卸载旧版-docker)
- [安装相关工具包](#安装相关工具包)
- [安装`Docker`源](#安装docker源)
- [阿里云](#阿里云)
- [更新 `yum` 缓存并且安装](#更新-yum-缓存并且安装)
- [启动 `Docker` 并且设置开机自启](#启动-docker-并且设置开机自启)
- [查看 `Docker` 版本](#查看-docker-版本)
- [PS:](#ps)

<!-- /TOC -->


# 卸载旧版 `Docker`
```
yum remove docker docker-common container-selinux docker-selinux docker-engine
```

# 安装相关工具包
```
yum install -y yum-utils
```

# 安装`Docker`源
```
# 官方
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

# 阿里云
```
yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```

# 更新 `yum` 缓存并且安装
```
yum makecache fast && yum install docker-ce -y
```

# 启动 `Docker` 并且设置开机自启
```
systemctl start docker && systemctl enable docker
```

# 查看 `Docker` 版本
```
docker -v
```

# PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

* 参考资料:


[1]]:http://www.wmyeah.com
