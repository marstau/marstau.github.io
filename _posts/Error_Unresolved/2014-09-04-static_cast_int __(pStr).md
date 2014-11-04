---
layout: post
title: static_cast<int *>(pStr)
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

 

  char str[] = "glad to test something";   

  char \*pStr = str;

  int \*p = **static\_cast**\<int \*\>(pStr);

// Error:

error C2440: “static\_cast”: 无法从“int \*”转换为“char \*”

1\>          与指向的类型无关；转换要求 reinterpret\_cast、C 样式转换或函数样式转换

 

 // Correct:

int \*p = **reinterpret\_cast**\<int \*\>(pStr);








