---
title: git修改忽略文件“.gitignore”并立即生效
date: 2017-02-20
tags: [Git]
categories: [Git]
---

<font size=20>目录：</font>

<!-- TOC -->

- [1. 说明:](#1-说明)
- [2. 清除缓存 记得 带“.”](#2-清除缓存-记得-带)
- [3. 将变化提交到暂存区](#3-将变化提交到暂存区)
- [4. 提交并填写相关信息](#4-提交并填写相关信息)
- [5. 可选同步到远程分支](#5-可选同步到远程分支)

<!-- /TOC -->

----

# 1. 说明:

* <font color=red>有时候我们得修改忽略文件并立即生效,这样方便我们精细化管理git仓库</font>

----

# 2. 清除缓存 记得 带“.”

```
git rm -r --cached .
```

# 3. 将变化提交到暂存区
```
git add .
```

# 4. 提交并填写相关信息
```
git commit -m "update .gitignore"   
```

# 5. <font color=red>可选</font>同步到远程分支
```
git push

或者

git push origin master
```

------

<h3 id = "ps">PS:</h3>

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

------

[1]:http://www.wmyeah.com
