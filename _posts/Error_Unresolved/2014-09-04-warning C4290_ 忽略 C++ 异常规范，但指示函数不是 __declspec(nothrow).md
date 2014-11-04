---
layout: post
title: warning C4290： 忽略 C++ 异常规范，但指示函数不是 __declspec(nothrow)
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

<span style="color:black;"><span
style="font-family:宋体;">**警告消息**:</span></span>

<span>忽略</span><span style="color:black;font-size:12pt;"><span
style="font-family:Times New Roman;">C++</span></span><span>异常规范，但指示函数不是</span><span
style="color:black;font-size:12pt;"><span
style="font-family:Times New Roman;">\_\_declspec(nothrow)</span></span>

<span>使用异常规范声明函数，</span><span
style="color:black;font-size:12pt;"><span
style="font-family:Times New Roman;">Visual
C++</span></span><span>接受但并不实现此规范。包含在编译期间被忽略的异常规范的代码可能需要重新编译和链接，以便在支持异常规范的未来版本中重用。</span>

<span>有关更多信息，请参见</span><span
style="color:black;font-size:12pt;"><span
style="font-family:Times New Roman;">Exception
Specifications</span></span><span>。</span><span
style="font-size:12pt;"><span
style="font-family:Times New Roman;"> </span></span>

<span style="font-size:12pt;"><span
style="font-family:Times New Roman;"></span></span>

**<span style="font-size:16px;">解决方案：</span>**

<span style="font-size:11pt;">在函数声明前加：</span><span
style="color:blue;font-size:11pt;">\#pragma </span><span
style="font-size:11pt;"><span style="color:blue;">warning</span> (<span
style="color:blue;">disable</span>:4290)</span>

 

 

<span>此方案只是保证编译器不再弹出警告，但是不能保证编译器接受异常规范</span>








