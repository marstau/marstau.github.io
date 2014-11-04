---
layout: post
title: android ndk 开发之Application.mk
category: 游戏技术
tags: android／java
keywords: 
description: 
---

From: <http://blog.csdn.net/weidawei0609/article/details/6561280>

 

Application.mk的作用：

Application.mk描述了应用程序需要哪些动态库和静态库。

 

 

存放位置：

文件通常放在项目目录的jni文件夹下。

 

 

变量定义：

由于Application.mk说到底只是作为GNU makefile的一个片段，其中也需要定义一些变量。

 

 

-APP\_PROJECT\_PATH

此变量应该被赋予项目的根目录地址，此项为可选项。

 

 

 

-APP\_MODULES

此项为可选项，当没有此选项时，NDK会自动编译android.mk文件中定义的所有模块及其包含的子模块。

 

当有此选项时，必须是一个模块的列表，各个模块之间以空格为分隔符分开或者是向android.mk中罗列开来。

 

 

-APP\_OPTIM

此选项可以被定义为 release 或 debug。这个选项用于变更编译程序模块时的优化级别。

默认的选项是release，此选项下会得到较高级别的优化。debug下为了便于调试不会进行过多优化。

 

 

 

可以在manifest文件中\<application\>tag内设置android:debuggable为ture来改变默认值为debug

 

其实无论debug还是release都是允许用户进行调试的，只是debug模式下会提供更多的信息。

 

 

-APP\_BUILD\_SCRIPT

默认条件下，NDK编译系统会到工程目录的jni文件夹下查找android.mk文件。如果你想覆盖这个行为的话

就可以定义此变量。如果你给定的是一个非绝对路径的话，那么这个路径总是被认为是相对于NDK顶层目录的路径。

-APP\_ABI

默认条件是armeabi，用户可以通过此选项进行修改，例如：为了在ARMv7上支持硬件FPU指令可以修改如下：

APP\_ABI := armeabi-v7a

或者支持ARMv5TE 又支持ARMv7的设备

APP\_ABI := armeabi armeabi-v7a

-APP\_STL

默认条件下，NDK编译系统会使用android系统提供的轻量级C++运行时库

/system/lib/libstdc++.so

NDK本身为用户提供了可选择的C++库，用户可以使用或是链接到自己的应用。

例如：

APP\_STL := stlport\_static    --\> static STLport library

       APP\_STL := stlport\_shared    --\> shared STLport library

       APP\_STL := system            --\> default C++ runtime library








