---
layout: post
title: dyld Library not loaded rpathlibfmodL
category: 编程开发
tags: error／unresolved
keywords: mac,ios
description: 
---	


## Error

```
dyld: Library not loaded: @rpath/libfmodL.dylib
```

## Solution

模拟器和真机的库用的不一样

模拟器：libfmodL_iphonesimulator.a, libfmod_iphonesimulator.a

真机：libfmodL_iphoneos.a,libfmod_iphoneos.a

## Reference