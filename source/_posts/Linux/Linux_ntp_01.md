---
title: Linux 基操
date: 2015-03-12 10:06:35
tags: Linux
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 、国内常用NTP服务器](#1-国内常用ntp服务器)
- [2. 、使用Let's Encrypt 申请 泛域名ssl证书](#2-使用lets-encrypt-申请-泛域名ssl证书)
- [3. PS:](#3-ps)

<!-- /TOC -->

------
# 1. 、国内常用NTP服务器
*   国家授时中心新的NTP服务器地址：
    ```
    ntp.ntsc.ac.cn
    ```
*   阿里云
    ```
    ntp.aliyun.com
    ```
*   国内大学
    ```
    s1c.time.edu.cn       北京大学 
    s2m.time.edu.cn       北京大学
    s1b.time.edu.cn       清华大学
    s1e.time.edu.cn       清华大学
    s2a.time.edu.cn       清华大学
    s2b.time.edu.cn       清华大学
    ```
*   国外授时服务器
    ```
    #苹果提供的授时服务器   
    time1.apple.com
    time2.apple.com
    time3.apple.com
    time4.apple.com
    time5.apple.com
    time6.apple.com
    time7.apple.com

    #Google提供的授时服务器   
    time1.google.com
    time2.google.com
    time3.google.com
    time4.google.com
    ```
# 2. 、使用Let's Encrypt 申请 泛域名ssl证书
*   命令（Ubuntu serve 18.04.4）
    ```
    certbot certonly --preferred-challenges dns --manual  -d *.example.com --server https://acme-v02.api.letsencrypt.org/directory
    ```
*   需要dns验证 自己操作增加txt 验证即可
*   默认在 /etc/letsencrypt/live/ 目录下
*   为了和阿里云配置保持同步做了两个注记命令 阿里云为 pem 和 key 结尾  这里都是pem
    ```
    cp /etc/letsencrypt/live/$mydomain.com/fullchain.pem ~/$mydomain.com_fullchain.pem
    
    cp /etc/letsencrypt/live/$mydomain.com/privkey.pem ~/$mydomain.com_fullchain_privkey.pem

    ```


------

# 3. PS:
* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!
------

[1]:http://www.wmyeah.com




