---
layout: post
title: crosses initialization
category: 游戏技术
tags: error／unresolved
keywords: 
description: 
---

 
<div
style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

<span style="color:#0000ff;">int</span> main()\
 {\
     <span style="color:#0000ff;">int</span> temp = 1 ;\
     <span style="color:#0000ff;">switch</span>(temp)\
     {\
         <span style="color:#0000ff;">case</span> 1:\
             <span style="color:#e53333;">**{**</span>\
                 <span style="color:#0000ff;">int</span> i = 1;\
                 cout \<\< i \<\< endl;\
                 <span style="color:#0000ff;">break</span>;\
            **<span style="color:#e53333;"> }</span>**\
         <span style="color:#0000ff;">case</span> 2:\
             **<span style="color:#e53333;">{</span>**\
                 <span style="color:#0000ff;">int</span> i = 2;\
                 cout \<\< i \<\< endl;\
                 <span style="color:#0000ff;">break</span>;\
             **<span style="color:#e53333;">}</span>**\
     }\
     <span style="color:#0000ff;">return</span> 0;\
 }\

如果没有红色的大括号，则会出现crosses initialization错误，因为编译器会认为局部变量i可能会被绕过申明而被直接进入其作用域。

</div>







