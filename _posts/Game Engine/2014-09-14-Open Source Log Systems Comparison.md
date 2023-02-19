---
layout: post
title: Open Source Log Systems Comparison
category: 编程开发
tags: GameEngine
keywords: 
description: 
---
## log4cxx

Apache logging framework for C++ patterned after Apache log4j (for Java).
比较复杂


## log4cplus[More](http://log4cplus.sourceforge.net/)


Another port of log4j from Java.

* 使用
  
  打开文件目录路E:\\Source Code\\log4cplus-1.1.1-rc4\\msvc10,运行log4cplus.sln即可。

## log4cpp

好久未更新
Log for C++ (also similar to Log4j in Java). Not very well documented, but there is an introductory article.

## glog


Google Logging Library

## Pantheios[More](http://stackoverflow.com/questions/439791/what-is-the-most-efficient-thread-safe-c-logger)

Pantheios is thought to be the best performing C++ logging library, as well as claiming to be the only one that is 100% type-safe (see this article about a related library explaining why printf()/iostream-based libraries are not type-safe)


![](/Resources/第三方库之开源日志库_1.png)


## g2log[More](http://www.codeproject.com/Articles/288827/g-log-An-efficient-asynchronous-logger-using-Cplus#TOC_part_2)


more efficient than glog, using C++11


## Reference
* <http://binglongx.wordpress.com/2010/07/23/logging-libraries-in-c/>
* <http://www.pantheios.org/performance.html#sweet-spot>