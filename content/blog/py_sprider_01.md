---
title: Python 爬虫常用命令集锦
date: 2019-08-15
tags: [Linux]
categories: [Linux]
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 说明:](#1-说明)
- [2. python BeautifulSoup怎么获取无标签文本](#2-python-beautifulsoup怎么获取无标签文本)
- [3. 时间函数处理](#3-时间函数处理)
- [4. 关于open()的mode参数：](#4-关于open的mode参数)
- [5. PS:](#5-ps)

<!-- /TOC -->

----

# 1. 说明:
* <font color=red>常用命令集锦</font>

----

# 2. python BeautifulSoup怎么获取无标签文本
```
get_name = soup_data.find_all('div', attrs={'class': 'inf-get_name'})
get_name = BeautifulSoup(str(get_name), 'html.parser').get_text().replace("\n","").replace(" ","").replace("[","").replace("]","")
```


# 3. 时间函数处理
```
# -*- coding:utf-8 -*-
import time
#当前时间
print time.time()
#时间戳形式
print time.localtime(time.time())
#简单可读形式
print time.asctime( time.localtime(time.time()) )
# 格式化成2015-02-11 10:45:39形式
print time.strftime("%Y-%m-%d %H:%M:%S", time.localtime()) 
# 格式化成Sat Mar 28 22:24:24 2016形式
print time.strftime("%a %b %d %H:%M:%S %Y", time.localtime()) 
# 将格式字符串转换为时间戳
a = "Sat Mar 28 22:24:24 2016"
print time.mktime(time.strptime(a,"%a %b %d %H:%M:%S %Y"))
```


# 4. 关于open()的mode参数：</h3>
```
'r'：读

'w'：写

'a'：追加

'r+' == r+w（可读可写，文件若不存在就报错(IOError)）

'w+' == w+r（可读可写，文件若不存在就创建）

'a+' ==a+r（可追加可写，文件若不存在就创建）

对应的，如果是二进制文件，就都加一个b就好啦：

'rb'　　'wb'　　'ab'　　'rb+'　　'wb+'　　'ab+'
```


------

# 5. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

* 参考资料:

	* 1、[gitolite README.markdown][2]
	* 2、[gitolite wiki][3]
	* 2、[Ubuntu下安装Git和Gitolite][4]

------

[1]:http://www.wmyeah.com
[2]:https://github.com/sitaramc/gitolite
[3]:https://github.com/sitaramc/gitolite/wiki
[4]:http://www.2cto.com/os/201205/132121.html
