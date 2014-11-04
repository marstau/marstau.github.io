---
layout: post
title: multimap容器不能用greater_equal
category: 游戏技术
tags: Ｃ／Ｃ＋＋
keywords: 
description: 
---

<div
style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

<span style="color:#000000;">template</span><span
style="color:#000000;">\<</span><span
style="color:#0000ff;">class</span><span
style="color:#000000;"> \_Pr, </span><span
style="color:#0000ff;">class</span><span
style="color:#000000;"> \_Ty1, </span><span
style="color:#0000ff;">class</span><span
style="color:#000000;"> \_Ty2</span><span
style="color:#000000;">\></span><span style="color:#000000;"> inline\
     </span><span style="color:#0000ff;">bool</span><span
style="color:#000000;"> \_\_CLRCALL\_OR\_CDECL \_Debug\_lt\_pred(\_Pr \_Pred, </span><span
style="color:#0000ff;">const</span><span
style="color:#000000;"> \_Ty1</span><span
style="color:#000000;">&</span><span
style="color:#000000;"> \_Left, </span><span
style="color:#0000ff;">const</span><span
style="color:#000000;"> \_Ty2</span><span
style="color:#000000;">&</span><span style="color:#000000;"> \_Right,\
     </span><span style="color:#0000ff;">const</span><span
style="color:#000000;"> wchar\_t </span><span
style="color:#000000;">\*</span><span
style="color:#000000;">\_Where, unsigned </span><span
style="color:#0000ff;">int</span><span style="color:#000000;"> \_Line)\
 ![](/Images/OutliningIndicators/ContractedBlock.gif)</span><span
id="Codehighlighter1_185_400_Closed_Text"
style="border-bottom:#808080 1px solid;border-left:#808080 1px solid;background-color:#ffffff;display:none;border-top:#808080 1px solid;border-right:#808080 1px solid;">![](http://www.cppblog.com/Images/dot.gif)</span><span
id="Codehighlighter1_185_400_Open_Text"><span
style="color:#000000;">{ </span><span
style="color:#008000;">//</span><span
style="color:#008000;"> test if \_Pred(\_Left, \_Right) and \_Pred is strict weak ordering</span><span
style="color:#008000;">\
 </span><span style="color:#000000;">    </span><span
style="color:#0000ff;">if</span><span
style="color:#000000;"> (</span><span
style="color:#000000;">!</span><span
style="color:#000000;">\_Pred(\_Left, \_Right))\
         </span><span style="color:#0000ff;">return</span><span
style="color:#000000;"> (</span><span
style="color:#0000ff;">false</span><span style="color:#000000;">);\
     </span><span style="color:#0000ff;">else</span><span
style="color:#000000;"> </span><span
style="color:#0000ff;">if</span><span
style="color:#000000;"> (\_Pred(\_Right, \_Left))\
         \_DEBUG\_ERROR2(</span><span
style="color:#000000;">"</span><span
style="color:#000000;">invalid operator\<</span><span
style="color:#000000;">"</span><span
style="color:#000000;">, \_Where, \_Line);\
     </span><span style="color:red;">return</span><span
style="color:red;"> (</span><span style="color:red;">true</span><span
style="color:red;">);</span><span style="color:red;">}</span><span
style="color:#000000;">\
 </span></span><span style="color:#000000;">\
 </span>

</div>

\
 因此,相等的时候就不行






