---
layout: post
title: pragma warning(disable:4996)
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

warning C4996: <span style="color:#e53333;">strcpy was declared
deprecated </span>

在使用VC 2005
的开发者会遇到这样的问题，在使用std命名空间库函数的时候，往往会出现类似于下面的警告：
warning C4996: strcpy was declared deprecated

出现这样的警告，是因为VC2005中认为CRT中的一组函数如果使用不当，可能会产生诸如内存泄露、缓冲区溢出、非法访问等安全问题。这些函数如：strcpy、strcat等。

对于这些问题，VC2005建议使用这些函数的更高级的安全版本，即在这些函数名后面加了一个\_s的函数。这些安全版本函数使用起来更有效，也便于识别，如：strcpy\_s,calloc\_s等。

当然，如果执意使用老版本、非安全版本函数，可以使用\_CRT\_SECURE\_NO\_DEPRECATE标记来忽略这些警告问题。办法是在编译选项
C/C++ | Preprocessor | Preprocessor
Definitions中，增加\_CRT\_SECURE\_NO\_DEPRECATE标记即可。或在程序开头添加<span
style="color:#e53333;"> **\#pragma warning(disable:4996)**</span>
//全部关掉 \#pragma warning(once:4996) //仅显示一个

 

<span style="color:#e53333;"> </span>

**<span
style="color:#e53333;">工程-\>Configration Properties-\>C/C++-\>Advanced-\>Disable Specific Warnings</span>**

**<span style="color:#e53333;">中添加 4996就行了</span>**

 








