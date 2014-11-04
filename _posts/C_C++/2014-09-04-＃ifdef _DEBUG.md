---
layout: post
title: ＃ifdef _DEBUG
category: 游戏技术
tags: Ｃ／Ｃ＋＋
keywords: 
description: 
---

<span class="Apple-style-span"
style="widows:2;text-transform:none;text-indent:0px;display:inline !important;font:14px/21px verdana, 'courier new';white-space:normal;orphans:2;float:none;letter-spacing:normal;color:#000000;word-spacing:0px;-webkit-text-size-adjust:auto;-webkit-text-stroke-width:0px;">在调试程序时，常常希望输出一些所需的信息，而在调试完成后不再输出这些信息。可以在源程序中插入以下的条件编译段：</span>

    \#ifdef<span class="Apple-converted-space"> </span><span
style="color:red;">\_DEBUG</span>

    print ("device\_open(%p)\\n", file);

    \#endif

    

    如果在它的前面有以下命令行：

    \#define \_DEBUG

    

    则在程序运行时输出file指针的值，以便调试分析。调试完成后只需将这个define命令行删除即可。有人可能觉得不用条件编译也可达此目的，即在调试时加一批printf语句，调试后一一将printf语句删除去。的确，这是可以的。但是，当调试时加的printf语句比较多时，修改的工作量是很大的。用条件编译，则不必一一删改printf语句，只需删除前面的一条“\#define
DEBUG”命令即可，这时所有的用DEBUG作标识符的条件编译段都使其中的printf语句不起作用，即起统一控制的作用，如同一个“开关”一样。







