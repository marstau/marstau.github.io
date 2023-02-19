---
layout: post
title: file is universal 3 slices but does not contain an armv7s slice
category: errors
tags: error-unresolved
keywords: 
description: 
---
# Error
ld: file is universal (3 slices) but does not contain a(n) armv7s slice: /Users/mars/Downloads/ydsg/1.0/ydsg/libs/cocos2dx/platform/libraries/libcurl.a file '/Users/mars/Downloads/ydsg/1.0/ydsg/libs/cocos2dx/platform/libraries/libcurl.a' for architecture armv7s
clang: error: linker command failed with exit code 1 (use -v to see invocation)
# Solution
修改TARGETS->Build Settings Architectures->Build Active Architecture Only为Yes。
*caution*:若无效,设置为No,然后再重新设置为Yes.
设置为下图所示:

![](/Resources/file is universal 3 slices_1.jpg)
