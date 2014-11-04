---
layout: post
title: sprite::create("*.png")崩溃
category: 游戏技术
tags: cocos2dx
keywords: 
description: 
---

I just had the same experience - nearly systemwide crash when trying to
compile a sass project with sprites.\
 If you take a look at your file - it is not a corrupted png, but a JPEG
image with a .png extension... This causes the crash.\
 Actually it is rather a memory-leak than a system crash [Don't know
much about this things, maybe i0m wrong].

From : <https://github.com/Compass/compass/issues/860>






