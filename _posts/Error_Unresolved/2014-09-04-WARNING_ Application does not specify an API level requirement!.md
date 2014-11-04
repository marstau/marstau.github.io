---
layout: post
title: Application does not specify an API level requirement!
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

WARNING: Application does not specify an API level requirement!

 

[2009-12-27 16:51:33 - Tank] WARNING: Application does not specify an API level requirement!

[2009-12-27 16:51:33 - Tank] Device API version is 3 (Android 1.5)

 

网上一查是由于没有指定users sdk的缘故,修改AndroidManifest.xml文件.

 

加入:

 

\<uses-sdk android:minSdkVersion="3"\>\</uses-sdk\>

 

加在\<manifest\> \</manifest\> 之间.

// 否则将导致程序直接崩溃！！








