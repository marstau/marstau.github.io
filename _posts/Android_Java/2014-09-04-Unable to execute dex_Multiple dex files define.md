---
layout: post
title: Unable to execute dex/Multiple dex files define
category: 游戏技术
tags: android／java
keywords: 
description: 
---

 

[2013-02-17 12:14:12 - Dex Loader] Unable to execute dex: Multiple dex files define Lcom/nd/commplatform/NdAppPromotionFlipperWindowController\$1;

[2013-02-17 12:14:12 - SYJT-91] Conversion to Dalvik format failed: Unable to execute dex: 

 

Multiple dex files define Lcom/nd/commplatform/NdAppPromotionFlipperWindowController\$1;

  

一种原因是jar包重复了,删除libs下的.jar包NdComPlatform.jar.(在网上看到好多这种情况,各种原因)

有时候某个类重复定义了，也会出现这种情况。








