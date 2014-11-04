---
layout: post
title: static DWORD成员变量定义
category: 游戏技术
tags: Ｃ／Ｃ＋＋
keywords: windows, DWORD
description: 
---

    // classes and structures
    struct stVertex{
    
    // ...
    
    static const DWORD FVF_VERTEX = D3DFVF_XYZ | D3DFVF_NORMAL | D3DFVF_TEX1;
};

因为DWORD在编译时刻宏替换成unsigned,而FVF_VERTEX也是编译时刻定义的,因此会出错,无法识别DWORD类型.

#Solution

solution: DWORD 换成 unsigned


