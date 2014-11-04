---
layout: post
title: __gmsl：512：*** non-numeric second argument to `wordlist' function： ''.
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

<div>

\

</div>

<div>

在编译ndk生成so动态库的时候，可能会碰到错误：

</div>

<div>

android-ndk-r8e/build/gmsl/\_\_gmsl:512: \*\*\* non-numeric second
argument to \`wordlist' function: ''.  Stop.

</div>

<div>

\

</div>

<div>

解决办法：把AndroidManifest.xml先move到别的地方，编译生成so库，在把AndroidManifest.xml移回来即可。

</div>

<div>

From: <http://www.mmihome.net/forum.php?mod=viewthread&tid=3>

</div>







