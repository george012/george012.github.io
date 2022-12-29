---
title: 利用Crontab 定时任务自动git pull更新代码
date: 2019-12-25
type: post
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. Crontab操作](#1-crontab操作)
- [2. 在需要更新的git项目文件夹内编辑git\_pull.sh](#2-在需要更新的git项目文件夹内编辑git_pullsh)
- [3. PS:](#3-ps)

<!-- /TOC -->

----
# 1. Crontab操作
* 1-1、编辑crontab
  ```
  crontab -e
  ```

* 1-2、将以下代码放入脚本
  ```
  # 脚本目录、日志目录 根据自己实际情况设定
  */2  *  *  *  *  /home/git_test/git_pull.sh >> /home/logs/git_pull.log 2>&1 &
  ```

# 2. 在需要更新的git项目文件夹内编辑git_pull.sh
* 2-1、编辑
  ```
  vim git_pull.sh
  ```

* 2-2、内容
  ```
  #!/bin/bash
  cu_sp_path=/home/git_test
  cd ${cu_sp_path} && git pull

  echo "["${cu_sp_path}"]  update with  ["`date`"]"
  ```

* 2-3、赋予权限
  ```
  chmod -R 777 git_pull.sh
  ```


------

# 3. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

------

[1]:http://www.wmyeah.com
