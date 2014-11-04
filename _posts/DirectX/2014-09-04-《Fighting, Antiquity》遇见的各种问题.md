---
layout: post
title: 《Fighting, Antiquity》遇见的各种问题
category: 游戏技术
tags: DirectX
keywords: 
description: 
---

-   

-   将shader实现的粒子系统集成到demo中时,粒子系统老是无法显示,经过不断注释代码,最终发现,原来是static
    mesh的时候\
    EffectLightTex-\>Begin( &nPass, 0 ); //
    EffectLightTex为ID3DXEffect.\
    后不记得运行

    EffectLightTex-\>End();\
    了.

-   

-   

    固定管线改为可编程管线的时候出现这个，是因为可编程管线绘制了一次模型,而后固定管线又绘制了一次模型,删除固定管线绘制的即可.\
    ![](http://files.note.sdo.com/XbPJ4~kjcjhR6u0zQ0061f)

-   

-   

     








