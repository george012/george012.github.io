---
title: ubuntu lvm 扩容
date: 2016-10-26
type: post
tags: Linux
---

<!-- TOC -->

- [1. ubuntu  lvm 扩容](#1-ubuntu--lvm-扩容)
- [2. 内存虚拟盘](#2-内存虚拟盘)
  - [2.1. 临时挂载](#21-临时挂载)
  - [2.2. 永久挂载](#22-永久挂载)

<!-- /TOC -->

----

# 1. ubuntu  lvm 扩容
```
lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv

resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
```

# 2. 内存虚拟盘

## 2.1. 临时挂载
```
mount -t tmpfs -o size=512G tmpfs /datas/plots_tmp
```

## 2.2. 永久挂载
```
vim /etc/fstab

tmpfs	/datas/plots_tmp	tmpfs	defaults,size=512G	0 0
```