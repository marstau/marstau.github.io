---
layout: post
title: warning:DIRECTINPUT_VERSION undefined. Defaulting to version 0x0800
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

如果使用DirectX9.0，则其DirectInput版本为8.0。假如直接写“\#include
\<dinput.h\>”，那么编译时会产生这么一个警告：DIRECTINPUT\_VERSION
undefined. Defaulting to version 0x0800

 

 

解决的办法就是这样写：

// xx.h

 

\#define DIRECTINPUT\_VERSION 0x0800

\#include \<dinput.h\>

 

// ...

 

 

 

需要说明的是，这里的版本定义并不是必须的，只是编译器会产生一个没什么影响的警告。在dinput.h里有这么一段代码：

 

\#define DIRECTINPUT\_HEADER\_VERSION 0x0800

 

\#ifndef DIRECTINPUT\_VERSION

 

\#define DIRECTINPUT\_VERSION DIRECTINPUT\_HEADER\_VERSION

 

\#pragma message(\_\_FILE\_\_ ": DIRECTINPUT\_VERSION undefined.
Defaulting to version 0x0800")

 

\#endif

 

 

 

 

所以如果你不声明版本的话，会给出你一个warning警告，不过也没什么关系，因为你确定使用的8.0的版本而不是其他版本，除非你需要使用其他版本，那么你才需要注意这点。








