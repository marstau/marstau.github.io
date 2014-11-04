---
layout: post
title: 在if里面请写入语句 使得打印出 hello world。
category: 游戏技术
tags: Ｃ／Ｃ＋＋
keywords: 
description: 
---

<div
style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

<span style="color:#0000ff;">**int**</span>** main()**\
 **{**\
 **    **<span style="color:#0000ff;">**if**</span>**()**\
 **        printf("Hello ");**\
 **    **<span style="color:#0000ff;">**else**</span>\
 **        printf("World !!!");**\
 **    **<span style="color:#0000ff;">**return**</span>** 0;**\
 **}**\
 <span style="color:#008000;">**//**</span><span
style="color:#008000;">** <span
style="color:#e53333;">在if里面请写入语句 使得打印出 hello world。</span>**</span><span
style="color:#008000;">\
 </span>\
\
 **answer**:\
 <span style="color:#0000ff;">int</span> main()\
 {\
     <span
style="color:#0000ff;">if</span>(puts("hello world"), exit(0), 1)\
         printf("Hello ");\
     <span style="color:#0000ff;">else</span>\
         printf("World !!!");\
 }

</div>






