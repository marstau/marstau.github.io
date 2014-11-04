---
layout: post
title: static_cast注意点
category: 游戏技术
tags: Ｃ／Ｃ＋＋
keywords: 
description: 
---

<div style="display:inline-block;">

<div>

<div>

<div
style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;font-size:13px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;background-color:#eeeeee;">

<div
style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;">

\#include "stdafx.h"\
 <span style="color:#0000ff;">class</span> C{\
 <span style="color:#0000ff;">public</span>:\
     \~C(){ cout \<\< "\~C" \<\< endl; }\
 };\
\
\
 <span style="color:#0000ff;">class</span> B:<span
style="color:#0000ff;">public</span> C{\
 <span style="color:#0000ff;">public</span>:\
\
     \~B(){ cout \<\< "\~B" \<\< endl; }\
 };\
 <span style="color:#0000ff;">int</span> main(){\
     B b;\
     static\_cast\<C\>(b);\
     (C)b;\
 }\
 <span style="color:#008000;">/\*</span><span style="color:#008000;">\
 \~C\
 \~C\
 \~B\
 \~C\
 请按任意键继续. . .</span><span style="color:#008000;">\*/</span>

</div>

<div
style="border-right:#cccccc 1px solid;padding-right:5px;border-top:#cccccc 1px solid;padding-left:4px;padding-bottom:4px;border-left:#cccccc 1px solid;width:98%;word-break:break-all;padding-top:4px;border-bottom:#cccccc 1px solid;">

<span style="color:#0000ff;">\#include "stdafx.h"</span>

<span style="color:#0000ff;">class</span> C{\
 <span style="color:#0000ff;">public</span>:\
     \~C(){ cout \<\< "\~C" \<\< endl; }\
 };\
\
\
 <span style="color:#0000ff;">class</span> B:<span
style="color:#0000ff;">public</span> C{\
 <span style="color:#0000ff;">public</span>:\
\
     \~B(){ cout \<\< "\~B" \<\< endl; }\
 };\
 <span style="color:#0000ff;">int</span> main(){\
     B b;\
     C\* pc;\
     pc = static\_cast\<C\*\>(&b);\
     pc = (C\*)&b;\
 } 

/\*

\~B

\~C

\*/

// 没有分配内存,所以不会有其他构造和析构函数

</div>

</div>

</div>

</div>

</div>






