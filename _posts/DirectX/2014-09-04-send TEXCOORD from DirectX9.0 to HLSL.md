---
layout: post
title: send TEXCOORD from DirectX9.0 to HLSL
category: 游戏技术
tags: DirectX
keywords: 
description: 
---

从DirectX中导入读取纹理坐标，出现这种情况\
  ![](http://files.note.sdo.com/XbPJ4~kbO_Q2wE0zQ00bLy)\
 原来是fx文件中 

    output.tex.x = input.tex.x;

    output.tex.y = input.tex.y + cos(g\_TimeDelta/120);\
 没设置好,

去掉即可。\
\
 ![](http://files.note.sdo.com/XbPJ4~kbO_POwE0zQ00bLv)







