---
title: iOS .Framework SDK开发注意事项
date: 2016-10-18
type: post
tags: iOS
---

<font size=20>目录：</font>
<!-- TOC -->

- [1. 搜索 Library 设置工程模式为  Static Library](#1-搜索-library-设置工程模式为--static-library)
- [2. 注意事项:](#2-注意事项)
- [3. Run Sripte 内容如下](#3-run-sripte-内容如下)
- [4. 脚本设置成功后 直接选择Target “Comand + B” 编译就OK](#4-脚本设置成功后-直接选择target-comand--b-编译就ok)
- [5. PS:](#5-ps)

<!-- /TOC -->
----

# 1. 搜索 Library 设置工程模式为  Static Library

![](img/wm_article_iOS_01.png)

----

# 2. 注意事项:

* -Option 目前支持选项
* Source.boundle 即同名资源Bundle文件

----

# 3. Run Sripte 内容如下
```
# 如果工程名称和Framework的Target名称不一样的话，要自定义FMKNAME 例如: FMK_NAME = "MyFramework"
FMK_NAME=${PROJECT_NAME}

# ---Option 打包资源Bundle
FMK_Source_NAME=${PROJECT_NAME}"Source"

# 设置打包导出目录
INSTALL_DIR_SRC=${SRCROOT}/Libs/${FMK_NAME}
INSTALL_DIR=${INSTALL_DIR_SRC}/${FMK_NAME}.framework

# 设置打包源文件空间
WRK_DIR=build
DEVICE_DIR=${WRK_DIR}/Release-iphoneos/${FMK_NAME}.framework
SIMULATOR_DIR=${WRK_DIR}/Release-iphonesimulator/${FMK_NAME}.framework

# Bundle文件目录
FMK_Source_DIR=${WRK_DIR}/Release-iphoneos/${FMK_Source_NAME}.bundle

# xcodebuild 命令相关设置
# Clean and Building both architectures.
xcodebuild -configuration "Release" -target "${FMK_NAME}" -sdk iphoneos clean build
xcodebuild -configuration "Release" -target "${FMK_NAME}" -sdk iphonesimulator clean build

# 使用xcodebuild 打包Bundle
xcodebuild -configuration "Release" -target "${FMK_Source_NAME}" -sdk iphoneos clean build

# 清除并新建INSTALL_DIR目录
if [ -d "${INSTALL_DIR}" ]
then
rm -rf "${INSTALL_DIR}"
fi
mkdir -p "${INSTALL_DIR}"

# 拷贝 .Framework 文件到 INSTALL_DIR目录
cp -R "${DEVICE_DIR}/" "${INSTALL_DIR}/"

# ---Option Bundle拷贝资源文件
cp -R "${FMK_Source_DIR}" "${INSTALL_DIR}/"

# Uses the Lipo Tool to merge both binary files (i386 + armv6/armv7) into one Universal final product.
lipo -create "${DEVICE_DIR}/${FMK_NAME}" "${SIMULATOR_DIR}/${FMK_NAME}" -output "${INSTALL_DIR}/${FMK_NAME}"

ln -s ${INSTALL_DIR}/${FMK_Source_NAME}.bundle ${INSTALL_DIR_SRC}/${FMK_Source_NAME}.bundle

# 清理工程
rm -r "${WRK_DIR}"
rm -r "${INSTALL_DIR}/_CodeSignature"
rm -r "${INSTALL_DIR}/Info.plist"
rm -r "${INSTALL_DIR}/Modules"
# ---Option
rm -r "${INSTALL_DIR}/${FMK_Source_NAME}.bundle/Info.plist"

# 打开打包好的工程目录
open "${INSTALL_DIR_SRC}"
```

------

# 4. 脚本设置成功后 直接选择Target “Comand + B” 编译就OK
![](img/wm_article_iOS_02.png)

------

# 5. PS:

* 根据网上资料亲测整理，最终解释权归[WMYeah][1]所有!

* 参考资料:

    * 1、[Xcode 6制作动态及静态Framework][2]

------

[1]:http://www.wmyeah.com
[2]:http://www.cocoachina.com/ios/20141126/10322.html
