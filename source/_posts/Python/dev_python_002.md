---
title: linux python 常用命令
date: 2019-08-15
type: post
tags: Linux
---

<font size=20>目录：</font>

<!-- TOC -->

- [1. Centos 篇](#1-centos-篇)
  - [1.1. virtualenvwrapper 操作Python 虚拟环境virtualenv](#11-virtualenvwrapper-操作python-虚拟环境virtualenv)
    - [1.1.1. 指定版本创建](#111-指定版本创建)
    - [1.1.2. 删除pyenv](#112-删除pyenv)
    - [1.1.3. 切换 py-env环境](#113-切换-py-env环境)
    - [1.1.4. 离开当前虚拟环境](#114-离开当前虚拟环境)
- [2. PS:](#2-ps)

<!-- /TOC -->

# 1. Centos 篇
## 1.1. virtualenvwrapper 操作Python 虚拟环境virtualenv
### 1.1.1. 指定版本创建
```
virtualenv -p  ${python-path} ${virtualenv-name}

# ${python-path} 欲指定python 版本路径
# ${virtualenv-name} 欲指定 py-env 名称
```

### 1.1.2. 删除pyenv
```
rmvirtualenv  ${virtualenv-name}

# ${virtualenv-name} py-env 名称
```

### 1.1.3. 切换 py-env环境
```
workon  ${virtualenv-name}

# ${virtualenv-name} py-env 名称
```

### 1.1.4. 离开当前虚拟环境
```
deactivate
```



------
# 2. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

------

[1]:http://www.wmyeah.com
[2]:http://blog.51cto.com/kusorz/1920778
