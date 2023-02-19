---
layout: post
title: libpng error  CgBI unhandled critical chunk
category: errors
tags: error-unresolved
keywords: cocos2dx,ios,xcode,symbol
description: 
---
# Error

libpng error: CgBI: unhandled critical chunk

cocos2dx无法载入png文件.

# Solution
在当前target->Build Settings,找到Packaging下的compress PNG Files,设置为No,即可。

## Reference
* <http://idevelopersmalltalk.blogspot.com/2012/05/iphone-libpng-error-cgbi-unknown.html>