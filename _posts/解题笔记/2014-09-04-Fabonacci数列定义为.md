---
layout: post
title: Fabonacci数列定义为
category: 数据结构与算法
tags: data　structure／algorithm
keywords: 
description: 
---

<span style="color:#e53333;font-size:10.5pt;">**Fabonacci**</span><span
style="color:#e53333;font-size:10.5pt;">**数列定义为（**</span><span
style="color:#e53333;font-size:10.5pt;">**1,1,2,3,5,8,.....**</span><span
style="color:#e53333;font-size:10.5pt;">**），即每个元素是前两个元素的和。如果一个**</span><span
style="color:#e53333;font-size:10.5pt;">**Fabonacci**</span><span
style="color:#e53333;font-size:10.5pt;">**数与所有小于它的**</span><span
style="color:#e53333;font-size:10.5pt;">**Fabonacci**</span><span
style="color:#e53333;font-size:10.5pt;">**数互质，那么称之为**</span><span
style="color:#e53333;font-size:10.5pt;">**Fabonacci**</span><span
style="color:#e53333;font-size:10.5pt;">**质数。现在求第**</span><span
style="color:#e53333;font-size:10.5pt;">**k**</span><span
style="color:#e53333;font-size:10.5pt;">**个**</span><span
style="color:#e53333;font-size:10.5pt;">**Fabonacci**</span><span
style="color:#e53333;font-size:10.5pt;">**质数是第几个**</span><span
style="color:#e53333;font-size:10.5pt;">**Fabonacci**</span><span
style="color:#e53333;font-size:10.5pt;">**数。**</span>
<div
style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;padding-bottom:4px;background-color:#eeeeee;padding-left:4px;width:98%;padding-right:5px;font-size:13px;word-break:break-all;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding-top:4px;">

\#include "stdafx.h"\
 <span style="color:#0000ff;">bool</span> IsPrime( <span
style="color:#0000ff;">const</span> vector\<<span
style="color:#0000ff;">long</span>\> &fibonacciSeq, <span
style="color:#0000ff;">int</span> num ){\
     <span style="color:#0000ff;">bool</span> retVal = <span
style="color:#0000ff;">true</span>;\
     <span style="color:#0000ff;">for</span>( vector\<<span
style="color:#0000ff;">long</span>\>::const\_iterator iter = fibonacciSeq.begin(); iter != fibonacciSeq.end(); iter++ )\
         <span style="color:#0000ff;">if</span>( num%\*iter == 0 ){\
             retVal = <span style="color:#0000ff;">false</span>;\
             <span style="color:#0000ff;">break</span>;\
         }\
\
     <span style="color:#0000ff;">return</span> retVal;\
 }\
\
 <span style="color:#0000ff;">long</span> KthPrimeInFibonacci( <span
style="color:#0000ff;">int</span> k ){\
     <span style="color:#0000ff;">if</span>( k \<= 0 ) <span
style="color:#0000ff;">return</span> 0;\
     <span style="color:#0000ff;">if</span>( k == 1 ) <span
style="color:#0000ff;">return</span> 3;\
\
     <span style="color:#0000ff;">long</span> fnminus1 = 2;\
     <span style="color:#0000ff;">long</span> fnminus2 = 1;\
     <span style="color:#0000ff;">long</span> fn = 3;\
     <span style="color:#0000ff;">int</span> cnt, nth;\
     vector\<<span style="color:#0000ff;">long</span>\> fibonacciSeq;\
     <span
style="color:#0000ff;">for</span>( cnt = 1, nth = 3; cnt \< k; nth++ ){\
         fn = fnminus1 + fnminus2;\
\
         fibonacciSeq.push\_back( fnminus1 );\
         <span style="color:#008000;">//</span><span
style="color:#008000;"> 剪枝,除2外的偶数都不是质数.</span><span
style="color:#008000;">\
 </span>        <span
style="color:#0000ff;">if</span>( (fn&0x01) != 0 && IsPrime( fibonacciSeq, fn) ) cnt++;\
\
         fnminus2 = fnminus1;\
         fnminus1 = fn;\
     }\
\
     <span style="color:#0000ff;">return</span> nth;\
 }\
 <span style="color:#0000ff;">int</span> main(){\
     <span style="color:#0000ff;">int</span> k;\
     <span style="color:#0000ff;">while</span>( cin \>\> k )\
         cout \<\< KthPrimeInFibonacci( k ) \<\< endl;\
 }\
 <span style="color:#008000;">/\*</span><span style="color:#008000;">\
 1\
 3\
\
 2\
 4\
\
 3\
 5\
\
 4\
 7\
\
 5\
 11\
\
 6\
 13\
 </span><span style="color:#008000;">\*/</span>

</div>






