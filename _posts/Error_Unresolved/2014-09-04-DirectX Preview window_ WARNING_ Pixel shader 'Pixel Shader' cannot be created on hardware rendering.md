---
layout: post
title: DirectX Preview window： WARNING： Pixel shader 'Pixel Shader' cannot be created on hardware rendering
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

DirectX Preview window: WARNING: Pixel shader 'Pixel Shader' cannot be created on hardware rendering。

![](http://files.note.sdo.com/XbPJ4~kbbG0iwE0rM00cl7)

**<span style="color:#e53333;">解决：</span>**

**因为pixel
shader中的target用的是高版本(ps\_3\_sw)的,硬件不支持,改成低版本即可。**








