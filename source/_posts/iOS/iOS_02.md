---
title: 制作cocoapods开源库-命令备忘
date: 2016-10-18
type: post
tags: iOS
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 说明:](#1-说明)
- [2. Git操作](#2-git操作)
  - [2.1. 将变化提交到暂存区](#21-将变化提交到暂存区)
  - [2.2. 提交并填写相关信息](#22-提交并填写相关信息)
  - [2.3. 打tag](#23-打tag)
  - [2.4. 同步tag](#24-同步tag)
- [3. pod trunk相关](#3-pod-trunk相关)
  - [3.1. 注册pod trunk](#31-注册pod-trunk)
  - [3.2. 在项目根目录下，创建podspec文件](#32-在项目根目录下创建podspec文件)
  - [3.3. 查看注册信息](#33-查看注册信息)
  - [3.4. 验证Pods库是否正确](#34-验证pods库是否正确)
  - [3.5. 上传至cocoaPods](#35-上传至cocoapods)
- [4. PS:](#4-ps)

<!-- /TOC -->
------

# 1. 说明:

* <font color=red>记录常用命令用以备忘</font>

------
# 2. Git操作
## 2.1. 将变化提交到暂存区
```
git add .
```

## 2.2. 提交并填写相关信息
```
git commit -m "release-Version-xxx"   
```

## 2.3. 打tag
```
git tag x.x.x
```

## 2.4. 同步tag
```
git push --tags
```

# 3. pod trunk相关
## 3.1. 注册pod trunk
```
# Description 为描述
# xxx@xxx.com 为邮箱
# --tag       为标识
#--description  自我描述

pod trunk register xxx@xxx.com '--Tag' --description='Description'
```

## 3.2. 在项目根目录下，创建podspec文件
```
# PodName 为定义开源库名
pod spec create PodName
```

## 3.3. 查看注册信息
```
pod trunk me
```

## 3.4. 验证Pods库是否正确
```
# 验证线上
pod spec lint XXX.podspec
# 验证本地
pod lib lint --allow-warnings

--allow-warnings 指忽略警告
```

## 3.5. 上传至cocoaPods
```
pod trunk push --allow-warnings
```


------

# 4. PS:
* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

------

[1]:http://www.wmyeah.com
