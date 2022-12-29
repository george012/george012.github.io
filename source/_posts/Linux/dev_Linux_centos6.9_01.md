---
title: CentOS6.9 后台自制shell循环任务+nohup运行SrpingBoot Jar包
date: 2018-04-05
type: post
tags: Linux
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. Shell脚本示例](#1-shell脚本示例)
- [2. 将写好的xxPlugin 放入/etc/init.d目录内](#2-将写好的xxplugin-放入etcinitd目录内)
- [3. PS:](#3-ps)

<!-- /TOC -->

----
# 1. Shell脚本示例
```
#!/bin/bash
#chkconfig: 2345 99 99
#description:xxPlugin


#   *jar 为要执行的jar包所在绝对路径
#   log_file 为转储运行日志绝对路径
#   前三行必写 description:为脚本描述建议20字符以内

nohup java -jar *.jar >log_file &
```

# 2. 将写好的xxPlugin 放入/etc/init.d目录内
* 运行如下命令
    ```
    #   添加自启服务
    chkconfig --add zjbjPlugin 
    #   查看自启服务
    chkconfig --list

    #   如需删除请按如下命令执行  
    chkconfig --del zjbjPlugin 
    ```


------

# 3. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

------

[1]:http://www.wmyeah.com
