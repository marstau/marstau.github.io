---
layout: post
title: is not a valid JNI reference
category: 编程开发
tags: error／unresolved
keywords: 
description: 
---

## Error

```
JNI ERROR (app bug): attempt to use stale local reference 0x4200001d (should be 0x4210001d)
    JNI WARNING: 0x4200001d is not a valid JNI reference
                 in LMyClass;.useStashedClass:()V (IsSameObject)
```


## Solutions[More](http://blog.k-res.net/archives/1525.html)

smali文件夹下代码的问题


```
Bug:调用DeleteLocalRef()后继续使用已被删除的引用

解决方法很简单：别对你还要用到的(包括作为返回值的)引用调用DeleteLocalRef()。
```

而对于已经编译好的.so文件要想修改,则需要反编译修改,eg:

```
BL _ZN7_JNIEnv14DeleteLocalRefEP8_jobject
```

此命令四个字节，改为

```
29 1C 29 1C
```

即可删除这个函数。

部分机型不兼容？？

## Reference