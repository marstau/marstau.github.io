---
layout: post
title: lwebsockets is not an object file
category: 编程开发
tags: error／unresolved
keywords: git,xcode
description: 
---
# Error
file: -lwebsockets is not an object file (not allowed in a library)

# Solution
确保Library Search Path中只引用一个libwebsockets.a文件

## Reference
* <http://www.cocoachina.com/bbs/simple/?t216349.html>