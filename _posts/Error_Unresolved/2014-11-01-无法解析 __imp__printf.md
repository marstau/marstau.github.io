---
layout: post
title: 无法解析 __imp__printf
category: 编程开发
tags: error-unresolved
keywords: 
description: 
---

# Error

```
arsゾ  10:17:52
1>SDL_compat.obj : error LNK2019: 无法解析的外部符号 __imp__printf，该符号在函数 _SDL_openFile 中被引用
1>SDL_compat.obj : error LNK2019: 无法解析的外部符号 __imp__fopen，该符号在函数 _SDL_openFile 中被引用
1>SDL_compat.obj : error LNK2019: 无法解析的外部符号 __imp___snprintf，该符号在函数 _SDL_openFile 中被引用
1>SDL_compat.obj : error LNK2019: 无法解析的外部符号 __imp__strncpy，该符号在函数 _SDL_openFile 中被引用
1>SDL_compat.obj : error LNK2019: 无法解析的外部符号 _memset，该符号在函数 _SDL_openFile 中被引用
1>SDL_compat.obj : error LNK2019: 无法解析的外部符号 __imp__tolower，该符号在函数 _my_strlwr 中被引用
```
# Solution[More](http://bbs.csdn.net/topics/120056819)

在项目属性->链接器->输入->附加依赖项 加入你用到的.lib（或.obj）等静态库。

添加

```
msvcrt.lib
```

## Reference