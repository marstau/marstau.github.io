---
layout: post
title: LNK2001 ： unresolved externals
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

\
 server1View.obj : error LNK2001: unresolved external symbol

<__imp__listen@8><span class="Apple-converted-space"> </span>\
 server1View.obj : error LNK2001: unresolved external symbol<span
class="Apple-converted-space"> </span><__imp__bind@12><span
class="Apple-converted-space"> </span>\
 server1View.obj : error LNK2001: unresolved external symbol

<__imp__socket@12><span class="Apple-converted-space"> </span>\
 server1View.obj : error LNK2001: unresolved external symbol<span
class="Apple-converted-space"> </span><__imp__htons@4><span
class="Apple-converted-space"> </span>\
 server1View.obj : error LNK2001: unresolved external symbol<span
class="Apple-converted-space"> </span><__imp__htonl@4><span
class="Apple-converted-space"> </span>\
 Debug/server1.exe : fatal error LNK1120: 5 unresolved externals<span
class="Apple-converted-space"> </span>\
 Error executing link.exe.<span class="Apple-converted-space"> </span>\
 Creating browse info file...

server1.exe - 6 error(s), 0 warning(s)

\
 <span style="color:#ff0000;">有俩种方法可以解决这个问题<span
class="Apple-converted-space"> </span></span>\
 <span
style="color:#ff0000;">1.在project-\>setting中,打开link选项卡,加上ws2\_32.lib<span
class="Apple-converted-space"> </span></span>\
 <span style="color:#ff0000;">2.在文件中加上\#progmma comment(lib,
"ws2\_32.lib")</span>

 








