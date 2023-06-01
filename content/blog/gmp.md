---
title: GMP
date: 2022-12-22
tags: [Linux]
categories: [Linux]
---
* 使用 MSYS2 UCRT64 进行操作
```
// 安装 make
pacman -S make
安装依赖 m4
pacman -S m4

```


* $GMP_PATH GMP 解压后的目录 例如 [D:\Download\gmp-6.2.1]
// 如果 mingw64 的目录是 [C:\Program Files\mingw64]
```
cd /d/Download/gmp-6.2.1
./configure --prefix=/c/mingw64 --enable-cxx --host=x86_64-w64-mingw32 --target=x86_64-w64-mingw32 --enable-shared --disable-static
```