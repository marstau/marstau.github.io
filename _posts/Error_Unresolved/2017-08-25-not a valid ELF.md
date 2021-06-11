---
layout: post
title: not a valid ELF
category: 编程开发
tags: error／unresolved
keywords: cocos2dx
description: 
---	


## Error

build_native.py编译cocos2dx的so文件

```
dlopen("/data/app-lib/com.izanami.infinitewar-1/libinfinitewar.so") failed: Cannot load library: load_library(linker.cpp:761): not a valid ELF executable: /data/app-lib/com.izanami.infinitewar-1/libinfinitewar.so
```


## Solution

更换android sdk的版本（不是ndk的版本）。

## Reference