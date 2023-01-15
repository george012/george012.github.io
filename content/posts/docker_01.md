---
title: Centos7.x安装最新版Docker
date: 2022-11-25
tags: [Docker]
categories: [Docker]
---

<!-- TOC -->

- [卸载旧版 Docker](#%E5%8D%B8%E8%BD%BD%E6%97%A7%E7%89%88-docker)
- [安装相关工具包](#%E5%AE%89%E8%A3%85%E7%9B%B8%E5%85%B3%E5%B7%A5%E5%85%B7%E5%8C%85)
- [安装Docker源](#%E5%AE%89%E8%A3%85docker%E6%BA%90)
- [阿里云](#%E9%98%BF%E9%87%8C%E4%BA%91)
- [更新 yum 缓存并且安装](#%E6%9B%B4%E6%96%B0-yum-%E7%BC%93%E5%AD%98%E5%B9%B6%E4%B8%94%E5%AE%89%E8%A3%85)
- [启动 Docker 并且设置开机自启](#%E5%90%AF%E5%8A%A8-docker-%E5%B9%B6%E4%B8%94%E8%AE%BE%E7%BD%AE%E5%BC%80%E6%9C%BA%E8%87%AA%E5%90%AF)
- [查看 Docker 版本](#%E6%9F%A5%E7%9C%8B-docker-%E7%89%88%E6%9C%AC)
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
