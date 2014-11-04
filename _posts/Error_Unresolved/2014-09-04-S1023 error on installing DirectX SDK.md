---
layout: post
title: S1023 error on installing DirectX SDK
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

Setup failed.

Errors were encountered during installation of redistributable packages.

Please close all open programs and try running setup again.

If problems persist, contact DirectX Developer Support.

Error code: S1023

 

Solution

 

The problem seems to be caused because my Windows has a Visual C++ 2010 Redistributable that is newer than the one that this SDK is trying to install. The solution, explained here, is to uninstall all the Visual C++ 2010 Redistributable packages and try installing this SDK.

 

I found that I had the following two packages:

1 Microsoft Visual C++ 2010  x64 Redistributable - 10.0.40219

2 Microsoft Visual C++ 2010  x86 Redistributable - 10.0.40219

I uninstalled them and the DirectX SDK installed without a problem after that.








