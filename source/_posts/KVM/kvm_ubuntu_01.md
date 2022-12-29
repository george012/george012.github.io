---
title: Ubuntu Server 18.0.4.4 KVM 虚拟化搭建
date: 2020-04-02
type: post
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. KVM安装](#1-kvm安装)
  - [1.1. 检查是否支持](#11-检查是否支持)
  - [1.2. 安装 cpu-checker 检查工具并检查机器是否支持 kvm](#12-安装-cpu-checker-检查工具并检查机器是否支持-kvm)
  - [1.3. 开始安装](#13-开始安装)
- [2. PS:](#2-ps)

<!-- /TOC -->

------
# 1. KVM安装
## 1.1. 检查是否支持
```
egrep -c '(vmx|svm)' /proc/cpuinfo
```

## 1.2. 安装 cpu-checker 检查工具并检查机器是否支持 kvm
*   安装cpu-checker
    ```
    apt install cpu-checker
    ```
*   检查
    ```
    kvm-ok
    ```
## 1.3. 开始安装
*   更新apt源并且安装kvm及相关组件
    ```
    apt update && apt install qemu qemu-kvm libvirt-bin  bridge-utils  virt-manager

    ```
*   设置网络桥接 共4网卡，2网卡给虚拟机，2网卡留给物理机
    ```
    network:
        ethernets:
            eno1:
                addresses:
                - 192.168.0.6/24
                gateway4: 192.168.0.1
                nameservers:
                    addresses:
                    - 192.168.0.1
            eno2:
                addresses:
                - 192.168.0.5/24
                gateway4: 192.168.0.1
                nameservers:
                    addresses:
                    - 192.168.0.1
            eno3:
                dhcp4: no
                dhcp6: no
            eno4:
                dhcp4: no
                dhcp6: no
        bridges:
            br0:
                interfaces: [eno3]
                dhcp4: no
                addresses: [192.168.0.4/24]
                gateway4: 192.168.0.1
                nameservers:
                    addresses: [192.168.0.1]
            br1:
                interfaces: [eno4]
                dhcp4: no
                addresses: [192.168.0.3/24]
                gateway4: 192.168.0.1
                nameservers:
                    addresses: [192.168.0.1]
        version: 2
    ```

*   更新配置 及 查看
    ```
    #   更新
    netplan apply
    #   查看
    networkctl status -a
    ```

------

# 2. PS:
* 此操作基于（root）权限操作，如用普通用户可在命令行前加“sudo”
* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!
------

[1]:http://www.wmyeah.com




